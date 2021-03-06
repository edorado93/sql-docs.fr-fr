---
title: Leçon 6 résultats potentiels Predict à l’aide des modèles R (SQL Server Machine Learning) | Microsoft Docs
description: Didacticiel expliquant comment incorporer R dans SQL Server des procédures stockées et fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/08/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 03118cec4ee068f5615af7d3319ca8f3172de0c1
ms.sourcegitcommit: 7d702a1d01ef72ad5e133846eff6b86ca2edaff1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48798569"
---
# <a name="lesson-6-predict-potential-outcomes-using-an-r-model-in-a-stored-procedure"></a>Leçon 6 : Prédire les résultats potentiels à l’aide d’un modèle R dans une procédure stockée
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fait partie d’un didacticiel pour les développeurs SQL sur l’utilisation de R dans SQL Server.

Dans cette étape, vous allez utiliser le modèle par rapport à nouvelles observations pour prédire les résultats potentiels. Le modèle est encapsulé dans une procédure stockée qui peut être appelée directement par d’autres applications. La procédure pas à pas montre plusieurs façons d’effectuer l’évaluation :

- **Mode de notation par lots**: utiliser une requête SELECT en tant qu’entrée à la procédure stockée. La procédure stockée retourne une table d’observations correspondant aux cas d’entrée.

- **Mode de calcul de score individuel**: passer un ensemble de valeurs de paramètres en tant qu’entrée.  La procédure stockée retourne une seule ligne ou valeur.

Tout d’abord, examinons le fonctionnement du calcul de score en général.

## <a name="basic-scoring"></a>Notation de base

La procédure stockée **PredictTip** illustre la syntaxe de base pour l’encapsulation d’un appel de prédiction dans une procédure stockée.

```SQL
CREATE PROCEDURE [dbo].[PredictTip] @inquery nvarchar(max) 
AS 
BEGIN 
  
DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);  
EXEC sp_execute_external_script @language = N'R',
  @script = N' 
    mod <- unserialize(as.raw(model)); 
    print(summary(mod)) 
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE); 
    str(OutputDataSet) 
    print(OutputDataSet) 
    ', 
  @input_data_1 = @inquery, 
  @params = N'@model varbinary(max)',
  @model = @lmodel2 
  WITH RESULT SETS ((Score float));
END
GO
```

+ L’instruction SELECT Obtient le modèle sérialisé à partir de la base de données et stocke le modèle dans la variable R `mod` pour un traitement ultérieur à l’aide de R.

+ Les nouveaux cas pour calculer les scores sont obtenues à partir de la [!INCLUDE[tsql](../../includes/tsql-md.md)] requête spécifiée dans `@inquery`, le premier paramètre de la procédure stockée. Lors de la lecture des données de requête, les lignes sont enregistrées dans la trame de données par défaut, `InputDataSet`. Cette trame de données est transmise à la [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) fonctionner dans [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), ce qui génère les scores.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Une trame de données ne pouvant contenir qu’une seule ligne, vous pouvez utiliser le même code pour le calcul de score unique ou de lot.
  
+ La valeur retournée par la `rxPredict` fonction est un **float** qui représente la probabilité que le pilote Obtient une info-bulle d’un montant quelconque.

## <a name="batch-scoring"></a>Notation par lot

Examinons maintenant le fonctionnement du calcul de score du lot.

1.  Commençons par obtenir un plus petit jeu de données d’entrée à utiliser. Cette requête crée une liste « top 10 » des trajets avec le nombre de passagers et d’autres caractéristiques nécessaires pour établir une prédiction.
  
    ```SQL
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **Exemples de résultats**
    
    ```
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

    Cette requête peut être utilisée en tant qu’entrée à la procédure stockée, **PredictTipMode**, fourni dans le cadre du téléchargement.

2. Prenez une minute pour examiner le code de la procédure stockée **PredictTipMode** dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

    ```SQL
    /****** Object:  StoredProcedure [dbo].[PredictTipMode]  ******/
    CREATE PROCEDURE [dbo].[PredictTipMode] @inquery nvarchar(max)
    AS
    BEGIN
    DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);
    EXEC sp_execute_external_script 
      @language = N'R',
      @script = N'
        mod <- unserialize(as.raw(model));
        print(summary(mod))
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);
        str(OutputDataSet)
        print(OutputDataSet)
      ',
      @input_data_1 = @inquery,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

3.  Fournir le texte de requête dans une variable et passez-le en tant que paramètre à la procédure stockée :

    ```SQL
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'

    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[PredictTip] @inquery = @query_string;
    ```
  
4. La procédure stockée retourne une série de valeurs qui représentent la prédiction pour chacun des courses 10 premiers. Toutefois, les trajets supérieurs sont également un seul passager avec une distance relativement courte voyage, pour laquelle le pilote est peu de chances d’obtenir une info-bulle.
  

> [!TIP]
> 
> Au lieu de retourner uniquement les « Oui-info-bulle » et « non-info-bulle » résultats, vous pouvez également retourner le score de probabilité pour la prédiction et ensuite appliquer une clause WHERE à la _Score_ les valeurs de colonne pour classer le score comme « susceptibles de Conseil » ou » peu de chances de Conseil », en utilisant une valeur de seuil comme 0,5 ou 0,7. Cette étape n’est pas incluse dans la procédure stockée, mais elle est facile à implémenter.

## <a name="single-row-scoring"></a>Ligne unique de score

Parfois, vous souhaitez transmettre des valeurs spécifiques à partir d’une application, et obtenir un résultat unique basé sur ces valeurs. Par exemple, vous pouvez configurer une feuille de calcul Excel, une application web ou un rapport Reporting Services pour appeler la procédure stockée et fournir des entrées tapées ou sélectionnées par les utilisateurs.

Dans cette section, vous allez apprendre à créer des prédictions uniques à l’aide d’une procédure stockée.

1. Prenez une minute pour examiner le code de la procédure stockée **PredictTipSingleMode**, qui est inclus dans le cadre du téléchargement.
  
    ```SQL
    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0, @trip_distance float = 0, @trip_time_in_secs int = 0, @pickup_latitude float = 0, @pickup_longitude float = 0, @dropoff_latitude float = 0, @dropoff_longitude float = 0
    AS
    BEGIN
    DECLARE @inquery nvarchar(max) = N'SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs,  @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)';
    DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);
    EXEC sp_execute_external_script  
      @language = N'R',
      @script = N'  
        mod <- unserialize(as.raw(model));  
        print(summary(mod));  
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
        str(OutputDataSet);
        print(OutputDataSet); 
        ',  
      @input_data_1 = @inquery,  
      @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float', @model = @lmodel2, @passenger_count =@passenger_count, @trip_distance=@trip_distance, @trip_time_in_secs=@trip_time_in_secs, @pickup_latitude=@pickup_latitude, @pickup_longitude=@pickup_longitude, @dropoff_latitude=@dropoff_latitude, @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END
    ```
  
    - Cette procédure stockée accepte plusieurs valeurs uniques comme entrée, telles que le nombre de passagers, la distance du trajet, et ainsi de suite.
  
        Si vous appelez la procédure stockée à partir d’une application externe, assurez-vous que les données correspondant aux critères du modèle R. Vous pourriez par exemple vérifier que les données d’entrée peuvent être transtypées ou converties en un type de données R, ou valider le type de données et la longueur des données. 
  
    -   La procédure stockée crée un score basé sur le modèle R stocké.
  
2. Essayez-la en fournissant les valeurs manuellement.
  
    Ouvrez une nouvelle **requête** fenêtre, puis appelez la procédure stockée, en fournissant des valeurs pour chacun des paramètres. Les paramètres représentent des colonnes de fonctionnalités utilisées par le modèle et sont nécessaires.

    ```
    EXEC [dbo].[PredictTipSingleMode] @passenger_count = 0,
    @trip_distance = 2.5,
    @trip_time_in_secs = 631,
    @pickup_latitude = 40.763958,
    @pickup_longitude = -73.973373,
    @dropoff_latitude =  40.782139,
    @dropoff_longitude = 73.977303
    ```

    Ou, utilisez ce formulaire plus court pris en charge pour [paramètres à une procédure stockée](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters):
  
    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. Les résultats indiquent que la probabilité d’obtention d’une info-bulle est faible (zéro) sur ces allers-retours top 10, dans la mesure où toutes les sont un seul passager sur une distance relativement courte.

## <a name="conclusions"></a>Conclusions

Cela conclut le didacticiel. Maintenant que vous avez appris à incorporer le code R dans les procédures stockées, vous pouvez étendre ces pratiques pour générer des modèles de votre choix. L’intégration à [!INCLUDE[tsql](../../includes/tsql-md.md)] simplifie grandement le déploiement de modèles R pour la prédiction et l’incorporation de la reformation de modèle dans le cadre d’un workflow de données d’entreprise.

## <a name="previous-lesson"></a>Leçon précédente

[Leçon 5 : Former et enregistrer un modèle R à l’aide de T-SQL](../r/sqldev-train-and-save-a-model-using-t-sql.md)
