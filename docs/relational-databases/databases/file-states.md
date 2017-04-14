---
title: "&#201;tats des fichiers | Microsoft Docs"
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
  - "restauration de l'état de fichier [SQL Server]"
  - "vérification des états de fichiers"
  - "états actuels des fichiers"
  - "vérification des états de groupes de fichiers"
  - "états des fichiers [SQL Server]"
  - "état de fichier en ligne"
  - "état de fichier hors connexion [SQL Server]"
  - "affichage des états de groupes de fichiers"
  - "affichage des états de fichiers"
  - "état de fichier suspect"
  - "récupération de l'état de fichier [SQL Server]"
  - "état actuel du groupe de fichiers"
  - "état de fichier récupération en attente [SQL Server]"
  - "affichage des états de fichiers"
  - "états [SQL Server], fichiers"
  - "affichage des états de groupes de fichiers"
  - "état de fichier défunt"
ms.assetid: b426474d-8954-4df0-b78b-887becfbe8d6
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# &#201;tats des fichiers
  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'état d'un fichier de base de données est géré indépendamment de l'état de la base de données. Un fichier a toujours un seul état spécifique, tel que ONLINE ou OFFLINE. Pour afficher l’état actuel d’un fichier, utilisez l’affichage catalogue [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md) ou [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md). Si la base de données est hors connexion, l’état des fichiers peut être visualisé à partir de l’affichage catalogue [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md).  
  
 L'état des fichiers dans un groupe de fichiers détermine la disponibilité du groupe de fichiers tout entier. Pour qu'un groupe de fichiers soit disponible, tous ses fichiers doivent être en ligne. Pour afficher l’état actuel d’un groupe de fichiers, utilisez l’affichage catalogue [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md). Si un groupe de fichiers est hors connexion et que vous tentez d'y accéder par l'intermédiaire d'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)], l'opération échoue et une erreur est générée. Lorsque l'optimiseur de requête planifie des instructions SELECT, il évite les index non-cluster et les vues indexées résidant dans les groupes de fichiers hors connexion, de sorte que ces instructions puissent être exécutées correctement. Cependant, si le groupe de fichiers hors connexion contient le segment ou l'index cluster d'une table cible, les instructions SELECT échouent. De plus, toute instruction INSERT, UPDATE ou DELETE modifiant une table assortie d'un index dans un groupe de fichiers hors connexion ne peut être exécutée.  
  
## Définitions de l'état d'un fichier  
 Le tableau suivant décrit les états d'un fichier.  
  
|État|Définition|  
|-----------|----------------|  
|ONLINE|Le fichier est accessible pour toutes les opérations. Les fichiers du groupe de fichiers primaire sont toujours en ligne lorsque la base de données elle-même l'est. Si un fichier du groupe de fichiers primaire n'est pas en ligne, la base de données n'est pas en ligne et les états des fichiers secondaires ne sont pas définis.|  
|OFFLINE|Le fichier n'est pas accessible et il se peut qu'il ne soit pas présent sur le disque. Les fichiers prennent l'état hors connexion du fait d'une action explicite de l'utilisateur et restent hors connexion tant qu'une autre action n'est pas exécutée.<br /><br /> **\*\* Attention \*\*** Un fichier ne doit être mis hors connexion que lorsqu’il est endommagé, mais qu’il peut être restauré. Un fichier mis hors connexion ne peut être remis en ligne qu'en étant restauré à partir d'une sauvegarde. Pour plus d’informations sur la restauration d’un fichier unique, consultez [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md).|  
|RESTORING|Le fichier est en cours de restauration. Les fichiers passent à l'état « restauration » en raison d'une commande de restauration affectant l'ensemble du fichier, et non pas juste une page, et conservent cet état tant que la restauration n'est pas accomplie et le fichier récupéré.|  
|RECOVERY PENDING|La récupération du fichier a été différée. Un fichier prend cet état automatiquement à la suite d'un processus de restauration fragmentaire au cours duquel le fichier n'est ni restauré ni récupéré. Une action supplémentaire est requise de la part de l'utilisateur pour résoudre l'erreur et permettre au processus de récupération de s'achever. Pour plus d’informations, consultez [Restaurations fragmentaires &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md).|  
|SUSPECT|La récupération du fichier a échoué au cours d'un processus de restauration en ligne. Si le fichier fait partie du groupe de fichiers primaire, la base de données est également marquée comme étant suspecte. Sans cela, seul le fichier est suspect et la base de données reste en ligne.<br /><br /> Le fichier garde l'état suspect tant qu'il n'est pas rendu de nouveau disponible à l'aide de l'une des méthodes suivantes :<br /><br /> Restauration et récupération<br /><br /> DBCC CHECKDB avec REPAIR_ALLOW_DATA_LOSS|  
|DEFUNCT|Le fichier a été supprimé alors qu'il n'était pas en ligne. Tous les fichiers d'un groupe de fichiers prennent l'état « ancien » quand un groupe de fichiers hors connexion est supprimé.|  
  
## Contenu connexe  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
 [États d'une base de données](../../relational-databases/databases/database-states.md)  
  
 [États de la mise en miroir &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
 [Groupes de fichiers et fichiers de base de données](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  