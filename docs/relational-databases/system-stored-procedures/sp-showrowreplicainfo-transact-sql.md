---
title: sp_showrowreplicainfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_showrowreplicainfo_TSQL
- sp_showrowreplicainfo
helpviewer_keywords:
- sp_showrowreplicainfo
ms.assetid: 6a9dbc1a-e1e1-40c4-97cb-8164a2288f76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5fdf29f59931c919b69b7c0662b2586d8df5ccc7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47791147"
---
# <a name="spshowrowreplicainfo-transact-sql"></a>sp_showrowreplicainfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche des informations concernant une ligne d'une table utilisée en tant qu'article dans une réplication de fusion. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_showrowreplicainfo [ [ @ownername = ] 'ownername' ]  
    [ , [ @tablename =] 'tablename' ]   
        , [ @rowguid =] rowguid   
    [ , [ @show = ] 'show' ]   
```  
  
## <a name="arguments"></a>Arguments  
 [ **@ownername**=] **'***ownername***'**  
 Nom du propriétaire de la table. *ownername* est **sysname**, avec NULL comme valeur par défaut. Ce paramètre est utile pour différencier les tables si une base de données contient plusieurs tables du même nom, chacune de ces tables ayant un propriétaire différent.  
  
 [  **@tablename =**] **'***tablename***'**  
 Nom de la table qui contient la ligne dont les informations sont renvoyées. *TableName* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@rowguid =**] *rowguid*  
 Identificateur unique de la ligne. *ROWGUID* est **uniqueidentifier**, sans valeur par défaut.  
  
 [ **@show**=] **'***afficher***'**  
 Détermine le volume d'informations à renvoyer dans l'ensemble de résultats. *afficher* est **nvarchar (20)** avec une valeur par défaut à la fois. Si **ligne**, uniquement les informations de version de ligne sont retournées. Si **colonnes**, uniquement les informations de version de colonne sont retournées. Si **à la fois**, à la fois lignes et les informations de colonne sont retournées.  
  
## <a name="result-sets-for-row-information"></a>Ensemble de résultats pour les informations de ligne  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Nom du serveur hébergeant la base de données qui a effectué l'entrée de la version de ligne.|  
|**db_name**|**sysname**|Nom de la base de données qui a effectué cette entrée.|  
|**db_nickname**|**binary(6)**|Surnom de la base de données qui a effectué cette entrée.|  
|**version**|**Int**|Version de l'entrée.|  
|**current_state**|**nvarchar(9)**|Retourne des informations sur l'état actuel de la ligne.<br /><br /> **y** -données de la ligne représente l’état actuel de la ligne.<br /><br /> **n** -données de ligne ne représente pas l’état actuel de la ligne.<br /><br /> **\<n/a >** - non applicable.<br /><br /> **\<inconnu >** -Impossible de déterminer l’état actuel.|  
|**rowversion_table**|**NCHAR(17)**|Indique si les versions de ligne sont stockées dans le [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) table ou la [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) table.|  
|**Commentaire**|**nvarchar(255)**|Informations supplémentaires concernant l'entrée de version de cette ligne. En général, ce champ est vide.|  
  
## <a name="result-sets-for-column-information"></a>Ensemble de résultats pour les informations de colonne  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Nom du serveur hébergeant la base de données qui a effectué l'entrée de la version de colonne.|  
|**db_name**|**sysname**|Nom de la base de données qui a effectué cette entrée.|  
|**db_nickname**|**binary(6)**|Surnom de la base de données qui a effectué cette entrée.|  
|**version**|**Int**|Version de l'entrée.|  
|**nom de colonne**|**sysname**|Nom de la colonne d'article que l'entrée de la version de colonne représente.|  
|**Commentaire**|**nvarchar(255)**|Informations supplémentaires concernant l'entrée de version de cette colonne. En général, ce champ est vide.|  
  
## <a name="result-set-for-both"></a>Ensemble de résultats pour la ligne et la colonne  
 Si la valeur **à la fois** est choisi pour *afficher*, jeux de résultats de la ligne et la colonne est retournée.  
  
## <a name="remarks"></a>Notes  
 **sp_showrowreplicainfo** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Permissions  
 **sp_showrowreplicainfo** peut uniquement être exécutée par les membres de la **db_owner** rôle de base de données fixe sur la base de données de publication ou par les membres de la liste d’accès de publication (PAL) sur la base de données de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Détecter et résoudre les conflits de réplication de fusion](../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
