---
title: MSrepl_identity_range (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5d93e005e4774daebd967518d694d0cb67516280
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704047"
---
# <a name="msreplidentityrange-transact-sql"></a>MSrepl_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSrepl_identity_range** table fournit la prise en charge de gestion des identités plage. Cette table est stockée dans les bases de données de publication, de distribution et d'abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Le nom du serveur de publication.|  
|**publisher_db**|**sysname**|Le nom de la base de données de publication.|  
|**TableName**|**sysname**|Nom de la table.|  
|**identity_support**|**Int**|Indique si la gestion automatique des plages d'identité est activée. La valeur 0 indique que la gestion automatique des plages d'identité n'est pas activée.|  
|**next_seed**|**bigint**|Si la gestion automatique des plages d'identité est activée, indique le point de départ de la plage suivante.|  
|**pub_range**|**bigint**|Taille de la plage d'identité du serveur de publication.|  
|**range**|**bigint**|Taille des valeurs d'identité consécutives qui seraient affectées aux abonnés dans le cas d'un ajustement.|  
|**max_identity**|**bigint**|Limite maximale de la plage d'identité.|  
|**seuil**|**Int**|Seuil de la plage d'identité exprimé en pourcentage.|  
|**current_max**|**bigint**|Maximum actuel qui est susceptible d'être attribué.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
