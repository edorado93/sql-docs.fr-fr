---
title: MSmerge_partition_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_partition_groups_TSQL
- MSmerge_partition_groups
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_partition_groups system table
ms.assetid: 5d56d780-ee40-4afc-9c2a-d1723d86e430
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d6b0b9f18377de89f6cf607f9aaab6c294f4a716
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846567"
---
# <a name="msmergepartitiongroups-transact-sql"></a>MSmerge_partition_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_partition_groups** table stocke une ligne pour chaque partition précalculée dans une base de données. Outre les colonnes répertoriées, une colonne est ajoutée à cette table pour chaque fonction utilisée dans un filtre de lignes paramétrable. Par exemple, une colonne nommée **HOST_NAME_FN** est ajouté à la table si un filtre utilise le [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) (fonction). Une ligne est stockée pour chaque jeu unique de valeurs de fonction synchronisées avec ce serveur de publication. Plusieurs abonnés qui synchronisent avec exactement la même valeur pour toutes ces fonctions partageront la même ligne dans cette table et auront dès lors tous le même ID de partition. Cette table est stockée dans la base de données de publication.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**Int**|Colonne d'identité fournissant un numéro d'identification unique pour la partition précalculée.|  
|**publication_number**|**smallint**|Le numéro de publication, qui est stocké dans **sysmergepublications**.|  
|**maxgen_whenadded**|**bigint**|Génération la plus élevée connue sur le serveur de publication au moment de l'insertion de la ligne dans cette table.|  
|**using_partition_groups**|**bit**|Indique si la partition appartient à une publication qui utilise des partitions précalculées. Peut être l'une des valeurs suivantes :<br /><br /> **0** = publication n’utilise pas les partitions précalculées.<br /><br /> **1** = la publication utilise des partitions précalculées<br /><br /> Pour plus d’informations, consultez [Optimiser les performances des filtres paramétrés avec des partitions précalculées](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).|  
|**HOST_NAME_FN**|**nvarchar(128)**|Valeur fournie lors de l'utilisation du filtre de lignes paramétrable en vue de générer des partitions. Pour plus d’informations, consultez [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
