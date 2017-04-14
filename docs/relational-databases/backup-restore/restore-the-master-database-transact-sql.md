---
title: "Restaurer la base de donn&#233;es MASTER (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "base de données MASTER [SQL Server], restauration"
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
caps.latest.revision: 42
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 42
---
# Restaurer la base de donn&#233;es MASTER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment restaurer la base de données **master** à partir d'une sauvegarde complète d'une base de données.  
  
### Pour restaurer la base de données master  
  
1.  Démarrez l'instance de serveur en mode mono-utilisateur.  
  
     Pour savoir comment spécifier le paramètre de démarrage mono-utilisateur (**-m**), consultez [Configurer les options de démarrage du serveur &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/configure-server-startup-options-sql-server-configuration-manager.md).  
  
2.  Pour restaurer une sauvegarde complète de la base de données **master**, utilisez l’instruction [RESTORE DATABASE](../Topic/RESTORE%20\(Transact-SQL\).md)[!INCLUDE[tsql](../../includes/tsql-md.md)] suivante :  
  
     `RESTORE DATABASE master FROM`  *<unité_de_sauvegarde>*  `WITH REPLACE`  
  
     L'option REPLACE indique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de restaurer la base de données spécifiée même lorsqu'il existe déjà une base de données du même nom. Le cas échéant, la base de données existante est supprimée. En mode mono-utilisateur, nous vous recommandons d’entrer l’instruction RESTORE DATABASE dans l’[utilitaire sqlcmd](../../tools/sqlcmd-utility.md). Pour plus d’informations, consultez [Utiliser l’utilitaire sqlcmd](../../relational-databases/scripting/use-the-sqlcmd-utility.md).  
  
    > [!IMPORTANT]  
    >  Une fois la base de données **MASTER** restaurée, l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’arrête et met fin au processus **sqlcmd** . Avant de redémarrer l'instance du serveur, supprimez le paramètre de démarrage en mode mono-utilisateur. Pour plus d’informations, consultez [Configurer les options de démarrage du serveur &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/configure-server-startup-options-sql-server-configuration-manager.md).  
  
3.  Redémarrez l'instance du serveur et poursuivez les autres étapes de récupération telles que la restauration d'autres bases de données, l'attachement de bases de données et la correction des incompatibilités au niveau utilisateur.  
  
## Exemple  
 Dans l'exemple suivant, la base de données `master` est restaurée sur l'instance du serveur par défaut. L'exemple suppose que l'instance du serveur s'exécute déjà en mode mono-utilisateur. L’exemple démarre `sqlcmd` et exécute une instruction `RESTORE DATABASE` qui restaure une sauvegarde complète de la base de données de `master` à partir d’une unité de disque : `Z:\SQLServerBackups\master.bak`.  
  
> [!NOTE]  
>  Dans le cas d’une instance nommée, la commande **sqlcmd** doit spécifier l’option **-S***\<NomOrdinateur>*\\*\<NomInstance>*.  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## Voir aussi  
 [Restaurations complètes de bases de données &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [Restaurations complètes de bases de données &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Dépanner des utilisateurs orphelins &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [Attacher et détacher une base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [Reconstruire des bases de données système](../../relational-databases/databases/rebuild-system-databases.md)   
 [Options de démarrage du service moteur de base de données](../../database-engine/configure-windows/database-engine-service-startup-options.md)   
 [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md)   
 [Sauvegarder et restaurer des bases de données système &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Démarrer SQL Server en mode mono-utilisateur](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  