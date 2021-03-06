---
title: Configurer l’option de configuration de serveur default language | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- default language option
ms.assetid: c08c26d8-5a62-487e-a4ee-4c529e4f9287
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2ca958583cbdf6fec00d5d507051f10be503abf4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079739"
---
# <a name="configure-the-default-language-server-configuration-option"></a>Configurer l'option de configuration de serveur default language
  Cette rubrique explique comment configurer l'option de configuration de serveur **default language** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option **Langue par défaut** spécifie la langue par défaut pour toutes les connexions nouvellement créées. Pour définir la langue par défaut, spécifiez la valeur **langid** de la langue souhaitée. La valeur **langid** peut être obtenue en interrogeant la vue de compatibilité **sys.syslanguages** .  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option default language, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option Langue par défaut](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   La langue par défaut pour une session ouverte peut être remplacée en utilisant CREATE LOGIN ou ALTER LOGIN. Elle correspond à celle définie dès l'ouverture de la session, à moins qu’elle ne soit remplacée à chaque session à l’aide des API ODBC (Open Database Connectivity) ou OLE DB. Remarque : Vous ne pouvez définir l’option **default language** que sur un identificateur de langue existant dans [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) (0-32). Lorsque vous utilisez des bases de données autonomes, il est possible de définir une langue par défaut pour une base de données à l'aide de CREATE DATABASE ou de ALTER DATABASE, et pour les utilisateurs de bases de données autonomes, à l'aide de CREATE USER ou de ALTER USER. La langue par défaut dans une base de données autonome peut être définie à l'aide de la valeur **langid**, du nom de la langue, ou d'un alias de langue répertorié dans **sys.syslanguages**.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-default-language-option"></a>Pour configurer l'option default language  
  
1.  Dans l'Explorateur d'objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Paramètres divers du serveur** .  
  
3.  Dans la zone **Langue par défaut pour l'utilisateur** , sélectionnez la langue dans laquelle [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit afficher les messages système.  
  
     La langue par défaut est l'anglais.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-default-language-option"></a>Pour configurer l'option default language  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) pour attribuer à l’option `default language` la valeur Français (`2`).  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'default language', 2 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option default language  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)   
 [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)   
 [ALTER USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
