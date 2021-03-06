---
title: Sys.dm_os_memory_cache_clock_hands (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_clock_hands_TSQL
- dm_os_memory_cache_clock_hands
- dm_os_memory_cache_clock_hands_TSQL
- sys.dm_os_memory_cache_clock_hands
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_clock_hands dynamic management view
ms.assetid: 0660eddc-691c-425f-9d43-71151d644de7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b39f40a36a9b9a639b8b6c90f6a6a37f7a32a4e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815109"
---
# <a name="sysdmosmemorycacheclockhands-transact-sql"></a>sys.dm_os_memory_cache_clock_hands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le statut de chaque aiguille d'une horloge de cache spécifique.  
  
> [!NOTE]  
>  À appeler à partir [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_memory_cache_clock_hands**.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Adresse du cache associé à l'horloge. N'accepte pas la valeur NULL.|  
|**nom**|**nvarchar (256)**|Nom du cache. N'accepte pas la valeur NULL.|  
|**type**|**nvarchar(60)**|Type de cache. Il peut exister plusieurs caches du même type. N'accepte pas la valeur NULL.|  
|**clock_hand**|**nvarchar(60)**|Type d'aiguille. Il s’agit d’une des opérations suivantes :<br /><br /> External<br /><br /> Interne<br /><br /> N'accepte pas la valeur NULL.|  
|**clock_status**|**nvarchar(60)**|Statut de l'horloge. Il s’agit d’une des opérations suivantes :<br /><br /> Suspendu<br /><br /> Exécution en cours<br /><br /> N'accepte pas la valeur NULL.|  
|**rounds_count**|**bigint**|Nombre de balayages effectués sur le cache pour supprimer des entrées. N'accepte pas la valeur NULL.|  
|**removed_all_rounds_count**|**bigint**|Nombre d'entrées supprimées par tous les balayages. N'accepte pas la valeur NULL.|  
|**updated_last_round_count**|**bigint**|Nombre d'entrées mises à jour lors du dernier balayage. N'accepte pas la valeur NULL.|  
|**removed_last_round_count**|**bigint**|Nombre d'entrées supprimées lors du dernier balayage. N'accepte pas la valeur NULL.|  
|**last_tick_time**|**bigint**|Heure, en millisecondes, du dernier mouvement de l'aiguille de l'horloge. N'accepte pas la valeur NULL.|  
|**round_start_time**|**bigint**|Heure, en millisecondes, du balayage précédent. N'accepte pas la valeur NULL.|  
|**last_round_start_time**|**bigint**|Durée totale, en millisecondes, du précédent cycle d'horloge. N'accepte pas la valeur NULL.|  
|**pdw_node_id**|**Int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="permissions"></a>Permissions  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stocke des informations en mémoire dans une structure appelée un cache mémoire. Les informations stockées dans le cache peuvent être des données, des entrées d'index, des plans de procédures compilées et divers autres types d'informations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour éviter d'avoir à recréer ces informations, celles-ci sont conservées aussi longtemps que possible dans le cache mémoire et sont généralement supprimées du cache lorsqu'elles sont trop anciennes pour être utiles ou lorsqu'il est nécessaire de libérer l'espace mémoire pour stocker de nouvelles informations. Le processus de suppression des anciennes informations s'appelle un balayage mémoire. Le balayage mémoire est une activité fréquente, mais pas continue. Un algorithme d'horloge contrôle le balayage du cache mémoire. Chaque horloge peut contrôler plusieurs balayages mémoire, qui sont appelés des aiguilles. L'aiguille de l'horloge du cache mémoire correspond à l'emplacement actuel de l'une des aiguilles d'un balayage mémoire.  

## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
 [sys.dm_os_memory_cache_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)
  

