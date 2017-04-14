---
title: "Configuration de la surface d&#39;exposition | Microsoft Docs"
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
  - "réduction de la surface d'exposition attaquable"
  - "mise à niveau de SQL Server, sécurité"
  - "configuration de la surface d'exposition [SQL Server]"
  - "configuration de la surface d’exposition [SQL Server], à propos de la configuration de la surface d’exposition"
  - "surface d'exposition attaquable [SQL Server]"
  - "installation de SQL Server, sécurité"
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
caps.latest.revision: 79
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 79
---
# Configuration de la surface d&#39;exposition
  Dans la configuration par défaut des nouvelles installations de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], de nombreuses fonctionnalités ne sont pas activées. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe et démarre de manière sélective uniquement les principaux services et fonctionnalités, de manière à réduire le nombre de fonctionnalités qui peuvent être soumises à une attaque d'un utilisateur malveillant. Un administrateur système peut modifier ces valeurs par défaut au moment de l'installation, et également activer ou désactiver sélectivement les fonctionnalités d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]en cours d'exécution. En outre, certains composants peuvent ne pas être disponibles lors de la connexion à partir d'autres ordinateurs jusqu'à ce que les protocoles soient configurés.  
  
> [!NOTE]  
>  Contrairement aux nouvelles installations, aucun service ou fonctionnalité existant n'est désactivé durant une mise à niveau, mais des options de configuration de la surface d'exposition supplémentaires peuvent être appliquées une fois la mise à niveau terminée.  
  
## Protocoles, connexion et options de démarrage  
 Utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour démarrer et arrêter des services, configurer les options de démarrage et activer des protocoles et autres options de connexion.  
  
#### Pour démarrer le Gestionnaire de configuration SQL Server  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
    -   Utilisez la zone **Services SQL Server** pour démarrer des composants et configurer les options de démarrage automatique.  
  
    -   Utilisez la zone **Configuration du réseau SQL Server** pour activer des protocoles de connexion et des options de connexion telles que les ports TCP/IP fixes ou le forçage du chiffrement.  
  
 Pour plus d’informations, consultez [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md). La connectivité distante peut également dépendre de la configuration correcte d'un pare-feu. Pour plus d’informations, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## Activation et désactivation de fonctionnalités  
 L'activation et la désactivation de fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être configurée à l'aide de facettes dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Pour configurer la surface d'exposition à l'aide de facettes  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connectez-vous à un composant de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le serveur, puis cliquez sur **Facettes**.  
  
3.  Dans la boîte de dialogue **Afficher les facettes**, développez la liste **Facette** et sélectionnez la facette **Configuration de la surface d’exposition** appropriée (**Configuration de la surface d’exposition**, **Configuration de la surface d’exposition pour Analysis Services** ou **Configuration de la surface d’exposition pour Reporting Services**).  
  
4.  Dans la zone **Propriétés de la facette** , sélectionnez les valeurs souhaitées pour chaque propriété.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Pour vérifier périodiquement la configuration d'une facette, utilisez la Gestion basée sur des stratégies. Pour plus d’informations sur la gestion basée sur des stratégies, consultez [Administrer des serveurs à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md).  
  
 Vous pouvez également définir des options du [!INCLUDE[ssDE](../../includes/ssde-md.md)] à l’aide de la procédure stockée **sp_configure**. Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 Pour modifier la propriété **EnableIntegrated Security** de [!INCLUDE[ssRS](../../includes/ssrs-md.md)], utilisez les paramètres de propriété dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour modifier les propriétés **Événements programmés et remise du rapport activés** et **Service Web et accès HTTP activés** , modifiez le fichier de configuration **RSReportServer.config** .  
  
## Options d'invite de commandes  
 Utilisez l’applet de commande **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell pour appeler des stratégies de configuration de la surface d’exposition. Pour plus d’informations, consultez [Utiliser les applets de commande du Moteur de base de données](../../relational-databases/scripting/use-the-database-engine-cmdlets.md).  
  
## Points de terminaison SOAP et Service Broker  
 Pour désactiver des points de terminaison, utilisez la Gestion basée sur des stratégies. Pour créer et modifier les propriétés de points de terminaison, utilisez [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md) et [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
## Contenu connexe  
 [Centre de sécurité pour le moteur de base de données SQL Server et la base de données SQL Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  