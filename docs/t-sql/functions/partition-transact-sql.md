---
title: $PARTITION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- $partition_TSQL
- $partition
dev_langs:
- TSQL
helpviewer_keywords:
- $PARTITION function
- partitions [SQL Server], numbers
ms.assetid: abc865d0-57a8-49da-8821-29457c808d2a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 74287e364736b4a1d09711b20817a9a0b0c694c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47839537"
---
# <a name="partition-transact-sql"></a>$PARTITION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le numéro de la partition dans laquelle un ensemble de valeurs de colonnes de partitionnement doit être mappé afin de pouvoir être utilisé par une fonction de partition précise dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[ database_name. ] $PARTITION.partition_function_name(expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la base de données contenant la fonction de partition.  
  
 *partition_function_name*  
 Nom de la fonction de partition existante à laquelle un ensemble de valeurs de colonnes de partitionnement est appliqué.  
  
 *expression*  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) dont le type de données doit correspondre au type de données de sa colonne de partitionnement correspondante ou être convertible de façon implicite en celui-ci. *expression* peut également représenter le nom d’une colonne de partitionnement participant actuellement à *partition_function_name*.  
  
## <a name="return-types"></a>Types de retour  
 **Int**  
  
## <a name="remarks"></a>Notes   
 $PARTITION renvoie une valeur de type **int** comprise entre 1 et le nombre de partitions de la fonction de partition.  
  
 $PARTITION retourne le numéro de partition pour toute valeur valide, sans vérifier l'existence de celle-ci dans une table ou un index partitionné utilisant la fonction de partition.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-getting-the-partition-number-for-a-set-of-partitioning-column-values"></a>A. Obtention du numéro de partition pour un ensemble de valeurs de colonnes de partitionnement  
 L'exemple suivant crée une fonction de partition appelée `RangePF1`, chargée de partitionner une table ou un index en quatre partitions. $PARTITION permet de déterminer si la valeur `10`, correspondant à la colonne de partitionnement de `RangePF1`, doit être placée dans la partition 1 de la table.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE PARTITION FUNCTION RangePF1 ( int )  
AS RANGE FOR VALUES (10, 100, 1000) ;  
GO  
SELECT $PARTITION.RangePF1 (10) ;  
GO  
```  
  
### <a name="b-getting-the-number-of-rows-in-each-nonempty-partition-of-a-partitioned-table-or-index"></a>B. Récupération du nombre de lignes de chaque partition non vide dans une table ou un index partitionné  
 L'exemple suivant retourne le nombre de lignes de chaque partition issue de la table `TransactionHistory` contenant les données. La table `TransactionHistory` utilise la fonction de partition `TransactionRangePF1` et est partitionnée sur la colonne `TransactionDate`.  
  
 Pour lancer cet exemple, vous devez au préalable exécuter le script PartitionAW.sql sur l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Pour plus d’informations, consultez [PartitioningScript](http://go.microsoft.com/fwlink/?LinkId=201015).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT $PARTITION.TransactionRangePF1(TransactionDate) AS Partition,   
COUNT(*) AS [COUNT] FROM Production.TransactionHistory   
GROUP BY $PARTITION.TransactionRangePF1(TransactionDate)  
ORDER BY Partition ;  
GO  
```  
  
### <a name="c-returning-all-rows-from-one-partition-of-a-partitioned-table-or-index"></a>C. Retour de toutes les lignes d'une partition donnée faisant partie d'une table ou d'un index partitionné  
 L'exemple suivant retourne toutes les lignes de la partition `5` de la table `TransactionHistory`.  
  
> [!NOTE]  
>  Pour lancer cet exemple, vous devez au préalable exécuter le script PartitionAW.sql sur l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Pour plus d’informations, consultez [PartitioningScript](http://go.microsoft.com/fwlink/?LinkId=201015).  
  
```  
SELECT * FROM Production.TransactionHistory  
WHERE $PARTITION.TransactionRangePF1(TransactionDate) = 5 ;  
```  
  
## <a name="see-also"></a> Voir aussi  
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)  
  
  
