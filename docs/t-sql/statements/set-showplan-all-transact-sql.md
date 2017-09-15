---
title: SET SHOWPLAN_ALL (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET SHOWPLAN_ALL
- SET_SHOWPLAN_ALL_TSQL
- SHOWPLAN_ALL
- SHOWPLAN_ALL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- SET SHOWPLAN_ALL statement
- SHOWPLAN_ALL option
- canceling statement execution
- stopping statement execution
- estimated execution information [SQL Server]
ms.assetid: a500b682-bae4-470f-9e00-47de905b851b
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: beb2d1647869da3ebb3f7463c896d8f6f986c387
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-showplanall-transact-sql"></a>SET SHOWPLAN_ALL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Empêche Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'exécuter des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. Au lieu de cela, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne des informations détaillées sur l'exécution des instructions et une estimation des ressources requises pour leur exécution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET SHOWPLAN_ALL { ON | OFF }  
```  
  
## <a name="remarks"></a>Notes  
 L'option SET SHOWPLAN_ALL est définie lors de l'exécution, et non pas durant l'analyse.  
  
 Si SET SHOWPLAN_ALL a la valeur ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne des informations sur l'exécution de chaque instruction sans toutefois l'exécuter ; les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ne sont pas exécutées. Une fois cette option activée, des informations sur toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ultérieures sont retournées, jusqu'à ce que l'option soit de nouveau désactivée. Par exemple, si une instruction CREATE TABLE est exécutée alors que l'option SET SHOWPLAN_ALL est activée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un message d'erreur pour toute instruction SELECT ultérieure se rapportant à cette table, informant les utilisateurs qu'elle n'existe pas. Par conséquent, les prochaines références à cette table échoueront. Lorsque SET SHOWPLAN_ALL a la valeur OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécute les instructions sans générer de rapport.  
  
 L'option SET SHOWPLAN_ALL est conçue pour être utilisée avec des applications capables de gérer ses résultats. Utilisez SET SHOWPLAN_TEXT pour retourner pour les applications d’invite de commandes Microsoft Win32, telles que la **osql** utilitaire.  
  
 Les options SET SHOWPLAN_TEXT et SET SHOWPLAN_ALL ne peuvent pas être spécifiées dans une procédure stockée ; elles doivent être les seules instructions dans le traitement.  
  
 SET SHOWPLAN_ALL retourne les informations sous forme d'un ensemble de lignes formant une arborescence représentant les étapes réalisées par le processeur de requêtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pendant qu'il exécute chaque instruction. Chaque instruction reflétée dans la sortie contient une ligne unique comportant le texte de l'instruction, suivie de plusieurs lignes contenant les détails des étapes d'exécution. Le tableau suivant illustre les colonnes figurant dans les résultats.  
  
|Nom de colonne| Description|  
|-----------------|-----------------|  
|**StmtText**|Pour les lignes qui ne sont pas du type PLAN_ROW, cette colonne contient le texte de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour les lignes de type PLAN_ROW, cette colonne contient une description de l'opération. Cette colonne contient l'opérateur physique et peut, en option, contenir l'opérateur logique. Elle peut également être suivie d'une description qui est déterminée par l'opérateur physique. Pour plus d’informations, consultez [Showplan logiques et physiques de référence des opérateurs](../../relational-databases/showplan-logical-and-physical-operators-reference.md).|  
|**StmtId**|Numéro de l'instruction dans le traitement courant.|  
|**NodeId**|ID du nœud dans la requête courante.|  
|**Parent**|ID du nœud de l'étape parente.|  
|**PhysicalOp**|Algorithme d'implémentation physique du nœud. Pour les lignes de type PLAN_ROWS uniquement.|  
|**LogicalOp**|Opérateur algébrique relationnel représenté par ce nœud. Pour les lignes de type PLAN_ROWS uniquement.|  
|**Argument**|Fournit des informations supplémentaires sur l'opération en cours. Le contenu de cette colonne est fonction de l'opérateur physique.|  
|**DefinedValues**|Contient la liste des valeurs introduites par cet opérateur, séparées par des virgules. Il peut s'agir d'expressions calculées présentes dans la requête courante (par exemple, dans la liste SELECT ou la clause WHERE), ou de valeurs internes introduites par le processeur de requêtes pour le traitement de cette requête. Ces valeurs définies peuvent ensuite être référencées à un autre endroit de la requête. Pour les lignes de type PLAN_ROWS uniquement.|  
|**EstimateRows**|Estimation du nombre de lignes de résultats produites par cet opérateur. Pour les lignes de type PLAN_ROWS uniquement.|  
|**EstimateIO**|Estimation du coût* des E/S pour cet opérateur. Pour les lignes de type PLAN_ROWS uniquement.|  
|**EstimateCPU**|Estimation du coût* UC pour cet opérateur. Pour les lignes de type PLAN_ROWS uniquement.|  
|**AvgRowSize**|Estimation de la taille moyenne (en octets) de la ligne transmise par le biais de cet opérateur.|  
|**TotalSubtreeCost**|Estimation du coût* (cumulatif) de cette opération et des opérations enfants.|  
|**OutputList**|Contient la liste des colonnes projetées par l'opération en cours, séparées par des virgules.|  
|**Avertissements**|Contient la liste des messages d'erreur (séparés par des virgules) relatifs à l'opération en cours. Les messages d'avertissement peuvent inclure la chaîne « NO STATS: () » avec une liste de colonnes. Ce message signifie que l'optimiseur de requêtes a tenté de prendre une décision en se basant sur les statistiques de cette colonne, mais aucune statistique n'était disponible. Par conséquent, l'optimiseur de requête a dû faire une estimation et a pu sélectionner un plan de requête inapproprié. Pour plus d’informations sur la création ou mise à jour des statistiques de colonnes (qui permettent à l’optimiseur de requête choisit un plan de requête plus efficace), consultez [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md). Cette colonne peut parfois inclure la chaîne « MISSING JOIN PREDICATE » qui indique qu'une jointure (portant sur des tables) est réalisée sans prédicat de jointure. Lorsqu'un prédicat de jointure est supprimé accidentellement, l'exécution d'une requête peut prendre beaucoup plus de temps que prévu, et retourner un jeu de résultats énorme. Si cet avertissement s'affiche, vérifiez que tout prédicat de jointure manquant a été intentionnellement supprimé.|  
|**Type**|Type de nœud. Pour le nœud parent de chaque requête, il s'agit du type d'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] (par exemple, SELECT, INSERT, EXECUTE, etc). Pour les sous-nœuds représentant des plans d'exécution, il s'agit du type PLAN_ROW.|  
|**Parallel**|**0** = opérateur n’est pas en cours d’exécution en parallèle.<br /><br /> **1** = (opérateur) est en cours d’exécution en parallèle.|  
|**EstimateExecutions**|Estimation du nombre de fois que cet opérateur sera exécuté durant l'exécution de la requête courante.|  
  
 *Les unités de coût sont basées sur une mesure interne d'heure, et non sur l'horloge murale. Elles permettent de déterminer le coût relatif d'un plan par rapport à d'autres plans.  
  
## <a name="permissions"></a>Permissions  
 Pour utiliser SET SHOWPLAN_ALL, vous devez disposer des autorisations suffisantes pour exécuter les instructions sur lesquelles SET SHOWPLAN_ALL est exécuté, ainsi que de l'autorisation SHOWPLAN pour toutes les bases de données contenant les objets auxquels elles font référence.  
  
 Pour SELECT, INSERT, UPDATE, DELETE, EXEC *procédure_stockée*et EXEC *user_defined_function* instructions, pour produire un plan de requête que l’utilisateur doit :  
  
-   disposer des autorisations appropriées pour exécuter les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ;  
  
-   disposer de l'autorisation SHOWPLAN sur toutes les bases de données contenant les objets auxquels les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] font référence, tels que les tables, les vues, etc.  
  
 Pour toutes les autres instructions, telles que DDL, USE *nom_base_de_données*, SET, DECLARE, dynamic SQL et ainsi de suite, seules les autorisations appropriées pour exécuter le [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions sont nécessaires.  
  
## <a name="examples"></a>Exemples  
 Les deux instructions suivantes utilisent l'option SET SHOWPLAN_ALL, activée puis désactivée, pour montrer comment [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] analyse et optimise l'utilisation des index dans les requêtes.  
  
 La première requête utilise l'opérateur de comparaison Égal à (=) dans la clause WHERE sur une colonne indexée. Ainsi, la valeur Clustered Index Seek dans le **LogicalOp** colonne et le nom de l’index dans le **Argument** colonne.  
  
 La seconde requête utilise l'opérateur LIKE dans la clause WHERE. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit utiliser une analyse d'index cluster et rechercher les données répondant à la condition spécifiée par la clause WHERE. Ainsi, la valeur Clustered Index Scan dans la **LogicalOp** colonne portant le nom de l’index dans le **Argument** colonne et la valeur de filtre dans le **LogicalOp** colonne avec la condition de la clause WHERE dans le **Argument** colonne.  
  
 Les valeurs dans le **EstimateRows** et **TotalSubtreeCost** les colonnes sont plus petites pour la première requête indexée, indiquant qu’il est traitée beaucoup plus rapide et utilise moins de ressources que la requête non indexée.  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_ALL ON;  
GO  
-- First query.  
SELECT BusinessEntityID   
FROM HumanResources.Employee  
WHERE NationalIDNumber = '509647174';  
GO  
-- Second query.  
SELECT BusinessEntityID, EmergencyContactID   
FROM HumanResources.Employee  
WHERE EmergencyContactID LIKE '1%';  
GO  
SET SHOWPLAN_ALL OFF;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_TEXT &#40; Transact-SQL &#41;](../../t-sql/statements/set-showplan-text-transact-sql.md)   
 [SET SHOWPLAN_XML &#40; Transact-SQL &#41;](../../t-sql/statements/set-showplan-xml-transact-sql.md)  
  
  
