---
title: "Extraction sur des structures d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0b00a3b-f9db-4289-a8cb-ddf600cd64ac
caps.latest.revision: 6
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 6
---
# Extraction sur des structures d&#39;exploration de donn&#233;es
  *L'extraction* désigne la capacité d'interroger un modèle d'exploration de données ou une structure d'exploration de données pour obtenir des informations détaillées qui ne sont pas exposées dans le modèle.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] fournit deux options différentes pour l'extraction des données de cas. Vous pouvez extraire les données utilisées pour générer le modèle d'exploration de données ou les données sources de la structure d'exploration de données.  
  
## Extraction dans des cas de modèle et dans la structure  
 L'extraction dans des **cas de modèle** est utile pour rechercher des informations supplémentaires sur les règles, les modèles ou les clusters dans un modèle.  
  
 Par opposition, **l'extraction dans les données de la structure** est conçue pour fournir un accès aux informations qui n'ont pas été mises à disposition dans le modèle. Par exemple, si vous disposez des autorisations appropriées, vous pouvez identifier les lignes de données qui ont été utilisées pour l'apprentissage du modèle et celles qui ont utilisées pour le test.  
  
 Vous pouvez également consulter les attributs des données qui n'ont pas été utilisées dans l'analyse, si elles ont été incluses dans la définition de la structure. Par exemple, souvent les structures d'exploration de données prennent en charge différents types de modèles, et certaines colonnes de structure peuvent avoir été exclues d'un modèle, car le type de données est incompatible ou les données ne sont pas utiles pour l'analyse. Par exemple, vous ne devez pas utiliser les informations de contact client dans un modèle de clustering, même si les données ont été incluses dans la structure, mais en activant l'extraction vous accédez à ces informations sans exécuter de requêtes distinctes sur la source de données.  
  
## Activation de l'extraction pour structurer les données  
 Pour utiliser l'extraction sur la structure d'exploration de données, les conditions suivantes doivent être remplies :  
  
-   L'extraction sur le modèle doit également être activée. Par défaut, l'extraction des deux types est désactivée. Pour activer l'extraction dans l'Assistant Exploration de données, sélectionnez l'option d'activation de l'extraction vers les cas de modèles sur la dernière page de l'Assistant. Vous pouvez également ajouter la capacité d’extraction sur un modèle ultérieurement en modifiant la propriété **AllowDrillthrough**.  
  
-   Si vous créez la structure d'exploration de données avec DMX, utilisez la clause WITH DRILLTHROUGH. Pour plus d’informations, consultez [CREATE MINING STRUCTURE &#40;DMX&#41;](../../dmx/create-mining-structure-dmx.md).  
  
-   Le principe de l'extraction consiste à extraire des informations sur les cas d'apprentissage mis en cache lorsque vous avez traité la structure d'exploration de données. Ainsi, si vous effacez les données en cache après avoir traité la structure en modifiant la propriété <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> en **ClearAfterProcessing**, l’extraction ne fonctionne pas. Pour activer l’extraction aux colonnes de structure, vous devez modifier la propriété <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> en **KeepTrainingCases**, puis retraiter la structure.  
  
-   Vérifiez que pour la structure et le modèle d’exploration de données la propriété [AllowDrillThrough](../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) a la valeur **True**. De plus, vous devez être membre d'un rôle ayant les autorisations d'extraction sur la structure et le modèle.  
  
## Problèmes de sécurité pour l'extraction  
 Les autorisations d'extraction sont définies séparément sur la structure et le modèle. L'autorisation de modèle permet d'effectuer une extraction à partir du modèle, même si vous n'avez pas d'autorisations sur la structure. Les autorisations d’extraction sur la structure permettent en outre d’inclure des colonnes de structure dans les requêtes d’extraction à partir du modèle, à l’aide de la fonction [StructureColumn &#40;DMX&#41;](../../dmx/structurecolumn-dmx.md).  
  
 Pour plus d’informations sur la création de rôles et l’attribution d’autorisations dans Analysis Services, consultez [Concepteur de rôle &#40;Analysis Services - Données multidimensionnelles&#41;](../Topic/Role%20Designer%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
> [!NOTE]  
>  Si vous activez l'extraction à la fois sur la structure d'exploration de données et le modèle d'exploration de données, tout utilisateur membre d'un rôle ayant les autorisations d'extraction sur le modèle d'exploration de données peut également consulter les colonnes de la structure d'exploration de données, même si ces colonnes ne sont pas incluses dans le modèle d'exploration de données. Par conséquent, afin de protéger les informations sensibles, vous devez configurer la vue de la source de données de façon à masquer les informations personnelles et à n'autoriser l'accès en extraction sur la structure d'exploration de données qu'en cas de nécessité.  
  
## Tâches associées  
 Consultez les rubriques suivantes pour plus d'informations sur l'utilisation de l'extraction avec des modèles d'exploration de données.  
  
|||  
|-|-|  
|Utiliser l'extraction dans la structure des visionneuses de modèle d'exploration de données|[Utiliser l'extraction des visionneuses de modèle](../../analysis-services/data-mining/use-drillthrough-from-the-model-viewers.md)|  
|Consulter les exemples de requêtes d'extraction pour les types de modèles spécifiques.|[Requêtes d'exploration de données](../../analysis-services/data-mining/data-mining-queries.md)|  
|Obtenir des informations sur l'assignation d'autorisations qui s'appliquent à des structures d'exploration de données et à des modèles d'exploration de données spécifiques.|[Octroyer des autorisations sur des modèles et des structures d’exploration de données &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## Voir aussi  
 [Extraction sur des modèles d'exploration de données](../../analysis-services/data-mining/drillthrough-on-mining-models.md)  
  
  