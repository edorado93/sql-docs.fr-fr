---
title: Deadlock Graph, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Deadlock Graph event class
ms.assetid: 20f92233-c912-4382-8993-8e2e23d03fbe
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 16b53261745e40f0d49a034421ee6fc6c35dfe13
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47831327"
---
# <a name="deadlock-graph-event-class"></a>Deadlock Graph, classe d’événements
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La classe d’événements **Deadlock Graph** fournit une description XML d’un interblocage. Cette classe a lieu en même temps que la classe d’événements **Lock:Deadlock** .  
  
## <a name="deadlock-graph-event-class-data-columns"></a>Colonnes de la classe d'événements Deadlock Graph  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**Int**|Type d’événement = 148.|27|non|  
|**EventSequence**|**Int**|Séquence d'un événement donné au sein de la demande.|51|non|  
|**IsSystem**|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur. Cette valeur est toujours égale à 1 pour cet événement.|60|Oui|  
|**LoginName**|**nvarchar**|Nom de la connexion de l’utilisateur (soit la connexion de sécurité [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d’identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur). Cette valeur est toujours l'utilisateur du système pour cet événement.|11|Oui|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur. Cette valeur est toujours le SID de l'utilisateur du système pour cet événement.|41|Oui|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**Int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure de détection du blocage.|14|Oui|  
|**TextData**|**ntext**|Description XML du blocage.|1|Oui|  
|**TransactionID**|**bigint**|Non utilisé.|4|Oui|  
  
## <a name="see-also"></a> Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Classe d'événements Lock:Deadlock](../../relational-databases/event-classes/lock-deadlock-event-class.md)  
  
  
