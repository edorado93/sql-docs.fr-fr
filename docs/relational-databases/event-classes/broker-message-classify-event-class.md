---
title: "Classe d&#39;&#233;v&#233;nements Broker:Message Classify | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Broker:Message Classify, classe d'événements"
ms.assetid: e51f3351-1239-4c41-b87c-1dd86968e027
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# Classe d&#39;&#233;v&#233;nements Broker:Message Classify
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement **Broker:Message Classify** quand Service Broker détermine le routage d’un message.  
  
## Colonnes de données de la classe d'événements Broker:Message Classify  
  
|Colonne de données|Type de données|Description|Numéro de colonne|Filtrable|  
|-----------------|---------------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|**ClientProcessID**|**int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|**int**|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**EventClass**|**int**|Type de classe d'événements capturée. Renvoie toujours **141** pour **Broker:Message Classify**.|27|Non|  
|**EventSequence**|**int**|Numéro de séquence de cet événement.|51|Non|  
|**EventSubClass**|**nvarchar**|Type de sous-classe d’événements, qui fournit des informations complémentaires concernant chaque classe d’événements. Cette colonne peut contenir les valeurs suivantes.<br /><br /> **Local** : la route choisie possède l’adresse LOCAL.<br /><br /> **Distant** :                 la route choisie possède une adresse autre que LOCAL.<br /><br /> **Retardé** :                 le message fait l’objet d’un retard, soit parce que le transfert est désactivé, soit parce qu’aucune route correspondante n’est présente.|21|Oui|  
|**FileName**|**nvarchar**|Nom du service vers lequel le message est dirigé.|36|Non|  
|**GUID**|**uniqueidentifier**|ID de conversation du dialogue. Cet identifiant est transmis en tant que partie intégrante du message et est partagé par les deux intervenants de la conversation.|54|Non|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Non|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**OwnerName**|**nvarchar**|Identificateur de Service Broker vers lequel le message est dirigé.|37|Non|  
|**RoleName**|**nvarchar**|Indique si le message a été reçu du réseau ou provient de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|38|Non|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SPID**|**int**|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|**Start Time**|**datetime**|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**TargetUserName**|**nvarchar**|Adresse réseau du Service Broker du saut suivant.|39|Non|  
|**TransactionID**|**bigint**|ID affecté à la transaction par le système.|4|Non|  
  
## Voir aussi  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  