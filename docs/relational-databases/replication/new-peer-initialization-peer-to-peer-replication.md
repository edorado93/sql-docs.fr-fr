---
title: "Initialisation d&#39;un nouvel homologue (r&#233;plication d&#39;&#233;gal &#224; &#233;gal) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.p2pwizard.init.f1"
ms.assetid: 050c00e1-78bd-4d9c-affe-40e22feb4d94
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Initialisation d&#39;un nouvel homologue (r&#233;plication d&#39;&#233;gal &#224; &#233;gal)
  Utilisez la page **Initialisation d'un nouvel homologue** pour spécifier comment les bases de données d'homologues ont été initialisées. (Les homologues doivent être initialisés avant la fin de cet Assistant.) Les homologues sont initialisés manuellement ou en utilisant la fonctionnalité **initialize with backup** fournie par la réplication transactionnelle. (La réplication transactionnelle d'égal à égal ne prend pas en charge l'initialisation d'homologues à l'aide d'un instantané.) Si différents homologues doivent être initialisés à l'aide de différentes méthodes, vous devez ajouter séparément les homologues en exécutant l'Assistant plusieurs fois.  
  
## Options  
 **Spécifiez comment la ou les nouvelles bases de données d'homologues ont été initialisées**  
 Chaque homologue doit comporter le schéma et les données pour tous les objets publiés. Sélectionnez l'une des options suivantes :  
  
-   Sélectionnez la première option si vous avez créé manuellement le schéma pour les objets publiés ou si vous avez restauré une sauvegarde et qu'aucune modification de données n'a été apportée dans la première base de données de publication depuis la sauvegarde. Si vous avez créé le schéma manuellement, vous devez vous assurer que chaque homologue comporte toutes les données requises. Cette option correspond à la valeur **prise en charge de la réplication uniquement** pour la propriété d’abonnement **sync_type**.  
  
-   Sélectionnez la seconde option si vous avez restauré une sauvegarde et qu'aucune modification n'a été apportée aux données dans la première base de données de publication depuis la sauvegarde. La réplication doit à présent illustrer les modifications qui ont été apportées dans la première base de données de publication et qui n'étaient pas comprises dans la sauvegarde. Cette option correspond à la valeur **initialisation avec sauvegarde** pour la propriété d’abonnement **sync_type**.  
  
     Lorsqu’une publication est activée pour la réplication d’égal à égal, la **allow_initialize_from_backup** la valeur de propriété de la publication. La réplication commence immédiatement à suivre les modifications dans la première base de données de publication. Par conséquent, ces modifications peuvent être remises à une base de données restaurée au niveau d'un ou de plusieurs homologues si l'option **initialize with backup** est sélectionnée. Cliquez sur le **Parcourir** pour localiser la sauvegarde utilisée et la réplication lit le numéro de séquence de journal (LSN) à partir de la sauvegarde. Toutes les modifications dans la première base de données de publication, avec un numéro de séquence d'enregistrement supérieur, sont transférées vers chaque homologue.  
  
     Il est possible que cette option ne soit pas disponible si vous créez ou enrichissez une topologie qui inclut [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Le tableau suivant indique si l'option est disponible lorsque vous ajoutez un nœud à une topologie existante.  
  
    |Nouveau nœud|Premier nœud|Nœuds supplémentaires|Option|  
    |--------------|----------------|----------------------|------------|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Désactivé|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Aucune|Désactivé|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Désactivé|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Aucune|Activé|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Aucune|Activé|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Activé|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Aucune|Activé|  
  
## Voir aussi  
 [Administrer une topologie d’égal à égal & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Réplication transactionnelle d'égal à égal](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  