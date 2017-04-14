---
title: "Configurer l&#39;option de configuration du serveur remote access | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "serveurs distants [SQL Server], exécution des procédures stockées"
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Configurer l&#39;option de configuration du serveur remote access
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette rubrique concerne la fonctionnalité Accès à distance. Il s’agit d’une fonctionnalité de communication peu intelligible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Elle est déconseillée et il vaudrait mieux que vous ne l’utilisiez pas. Si vous êtes sur cette page en raison de problèmes de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez plutôt l’une des rubriques suivantes :  
  
-   [Didacticiel : mise en route du moteur de base de données](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
  
-   [Connexion à SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
-   [Se connecter à SQL Server lorsque les administrateurs système n'y ont plus accès](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
-   [Se connecter à un serveur inscrit &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/connect-to-a-registered-server-sql-server-management-studio.md)  
  
-   [Se connecter à n'importe quel composant de SQL Server à partir de SQL Server Management Studio](../../ssms/f1-help/connect-to-any-sql-server-component-from-sql-server-management-studio.md)  
  
-   [Se connecter au moteur de base de données avec sqlcmd](../../relational-databases/scripting/connect-to-the-database-engine-with-sqlcmd.md)  
  
-   [Comment faire pour résoudre les problème de connexion au moteur de base de données SQL Server](http://social.technet.microsoft.com/wiki/contents/articles/2102.how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx)  
  
 Les programmeurs peuvent s’intéresser aux rubriques suivantes :  
  
-   [How To: Connect to SQL Server Using SQL Authentication in ASP.NET 2.0 (Comment : établir une connexion à SQL Server à l’aide de l’authentification SQL dans ASP.NET 2.0)](https://msdn.microsoft.com/library/ff648340.aspx)  
  
-   [Connexion à une instance de SQL Server](https://msdn.microsoft.com/library/ms162132.aspx)  
  
-   [Comment : créer des connexions à des bases de données SQL Server](https://msdn.microsoft.com/library/s4yys16a.aspx)  
  
 **Le corps de cette rubrique commence ici.**  
  
 Cette rubrique explique comment configurer l'option de configuration de serveur **Accès à distance** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option **Accès à distance** contrôle l'exécution des procédures stockées depuis les serveurs locaux ou distants sur lesquels des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont en cours d'exécution. La valeur par défaut de cette option est 1. Cette valeur autorise l'exécution des procédures stockées locales depuis des serveurs distants, ou des procédures stockées distantes depuis le serveur local. Pour empêcher l'exécution des procédures stockées locales depuis un serveur distant ou des procédures stockées distantes depuis le serveur local, attribuez la valeur 0 à cette option.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilisez de préférence [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option Accès à distance, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option Accès à distance](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   L’option **Accès à distance** ne s’applique qu’aux serveurs ajoutés au moyen de [sp_addserver](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)et n’est incluse que pour des raisons de compatibilité descendante.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour configurer l'option Accès à distance  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Connexions** .  
  
3.  Sous **Connexions au serveur distant**, activez ou désactivez la case à cocher **Autoriser les accès distants à ce serveur** .  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour configurer l'option Accès à distance  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour définir l’option `remote access` sur `0`.  
  
```tsql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Pour plus d’informations, consultez [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option Accès à distance  
 SQL Server doit être redémarré pour que ce paramètre prenne effet.  
  
## Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  