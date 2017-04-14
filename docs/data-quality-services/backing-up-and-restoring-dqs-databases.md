---
title: "Sauvegarde et restauration de bases de donn&#233;es DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
caps.latest.revision: 12
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 12
---
# Sauvegarde et restauration de bases de donn&#233;es DQS
  Cette rubrique explique comment sauvegarder et restaurer les bases de données DQS.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Vous devez connaître ou mémoriser le mot de passe de la clé principale de base de données que vous avez fourni pendant l'installation du serveur DQS.  
  
-   Vérifiez qu'aucune activité ou aucun processus n'est en cours d'exécution dans DQS. Pour ce faire, utilisez l'écran **Analyse des activités** . Pour plus d'informations sur l'utilisation de cet écran, consultez [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md).  
  
-   Assurez-vous qu'aucun utilisateur n'est connecté au serveur DQS.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
  
-   Votre compte d'utilisateur Windows doit être membre du rôle serveur fixe sysadmin dans l'instance de SQL Server pour effectuer les opérations de sauvegarde et de restauration.  
  
-   Vous devez disposer du rôle dqs_administrator sur la base de données DQS_MAIN pour mettre fin à toutes les activités en cours d'exécution ou arrêter tous les processus en cours d'exécution dans DQS.  
  
##  <a name="BackupRestore"></a> Sauvegarder et restaurer des bases de données DQS  
  
1.  Démarrez Microsoft SQL Server Management Studio et connectez-vous à l'instance de SQL Server appropriée.  
  
2.  Dans l'Explorateur d'objets, développez le nœud **Bases de données** .  
  
3.  Sauvegardez la base de données DQS_STAGING_DATA. Pour obtenir des instructions détaillées pour la sauvegarde d’une base de données SQL Server, consultez [créer une sauvegarde complète de la base de données & #40 ; SQL Server & #41 ;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
4.  Sauvegardez la base de données DQS_PROJECTS.  
  
5.  Sauvegardez la base de données DQS_MAIN.  
  
6.  Déconnectez-vous de l'instance actuelle de SQL Server, et connectez-vous à l'instance de SQL Server où vous voulez restaurer ces bases de données.  
  
7.  Restaurez la base de données DQS_MAIN. Pour obtenir des instructions pas à pas restaurer une base de données SQL Server, consultez [restaurer un SSMS à l’aide de sauvegarde de base de données](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).  
  
8.  Restaurez la base de données DQS_PROJECTS.  
  
9. Restaurez la base de données DQS_STAGING_DATA.  
  
10. Dans l’Explorateur d’objets, cliquez sur le serveur, puis cliquez sur **nouvelle requête**.  
  
11. Dans la fenêtre Éditeur de requête, copiez les instructions SQL suivantes, puis remplacez *\< mot de passe>* avec le mot de passe que vous avez fourni pendant l’installation de DQS pour la clé principale de base de données :  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
  
    ```  
  
12. Appuyez sur F5 pour exécuter les instructions. Consultez le volet de **résultats** pour vérifier que les instructions ont été correctement exécutées.  
  
## Voir aussi  
 [Gérer des bases de données DQS](../data-quality-services/manage-dqs-databases.md)  
  
  