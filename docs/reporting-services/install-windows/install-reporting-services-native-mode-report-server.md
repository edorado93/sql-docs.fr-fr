---
title: "Installer le serveur de rapports Reporting Services en mode natif | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "configuration par défaut [Reporting Services]"
  - "serveurs de rapports [Reporting Services], configurations par défaut"
  - "options d'installation [Reporting Services]"
ms.assetid: 8f25e6dc-b753-400e-9e9a-50f4f35bf6c4
caps.latest.revision: 68
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 65
---
# Installer le serveur de rapports Reporting Services en mode natif
Découvrez comment installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif. Vous bénéficierez d’un accès à un [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] permettant de gérer les rapports et d’autres éléments.

Un serveur de rapports en mode natif [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est le mode de serveur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] par défaut et peut être installé via l’assistant d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou à partir de la ligne de commande. Dans l’assistant d’installation, vous pouvez choisir d’installer les fichiers et de configurer le serveur avec les paramètres par défaut ou de n’installer que les fichiers. Cette rubrique passe en revue *la configuration par défaut pour le mode natif* où le programme d'installation installe et configure une instance de serveur de rapports. Une fois l’installation terminée, le serveur de rapports est opérationnel et prêt à effectuer des tâches de gestion et d’affichage de rapports.  D’autres fonctionnalités, telles que l’intégration de [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] et l’envoi de courriers électroniques avec traitement des abonnements, nécessitent une configuration supplémentaire.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif|  
  
##  <a name="bkmk_whatisdefaultconfiguration"></a> Quelle est la configuration par défaut ?  
 Le programme d'installation installe les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] suivantes lorsque vous sélectionnez la configuration par défaut de l'option de mode natif :  
  
-   Le service Report Server (qui inclut le service web Report Server, l’application de traitement en arrière-plan et le [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] qui permet d’afficher et de gérer les rapports et les autorisations).  
  
-   Le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   Les utilitaires de ligne de commande [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (rsconfig.exe, rskeymgmt.exe et rs.exe).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] sont désormais des téléchargements distincts.  
  
 L'installation configure les éléments suivants pour une installation de serveur de rapports en mode natif :  
  
-   Compte de service pour le service Report Server.  
  
-   URL du service Web Report Server.  
  
-   L’URL de [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)].  
  
-   Base de données du serveur de rapports.  
  
-   Accès des comptes de service aux bases de données Report Server  
  
-   Informations de connexion, également connues en tant que nom de source de données (DSN), pour les bases de données de serveur de rapports.  
  
 L'installation ne configure pas le compte d'exécution sans assistance, la messagerie électronique de serveur de rapports, la sauvegarde des clés de chiffrement ou le déploiement avec montée en puissance parallèle. Vous pouvez utiliser le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour configurer ces propriétés. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).
  
##  <a name="bkmk_whentoinstalldefaultconfig"></a> Quand installer la configuration par défaut pour le mode natif  
 Une configuration par défaut installe [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans un état opérationnel afin que vous puissiez utiliser immédiatement le serveur de rapports une fois l'installation terminée. Spécifiez ce mode lorsque vous souhaitez économiser des étapes en éliminant toutes les tâches de configuration requises que vous devriez autrement exécuter dans l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 L'installation de la configuration par défaut ne garantit pas que le serveur de rapports fonctionne après que l'installation est terminée. L'inscription des URL par défaut peut ne pas s'effectuer quand le service démarre. Testez toujours votre installation pour vérifier que le service démarre et s'exécute comme prévu.  Consultez [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).
  
##  <a name="bkmk_requirements"></a> Spécifications  
 L'option de configuration par défaut utilise les valeurs par défaut pour configurer les paramètres principaux obligatoires pour rendre un serveur de rapports opérationnel. Elle comporte les impératifs suivants :  
  
-   Consultez [Hardware and Software Requirements for Installing SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md) .  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] doivent être installés ensemble dans la même instance. L'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] héberge la base de données du serveur de rapports que le programme d'installation crée et configure.  
  
-   Le compte d'utilisateur utilisé pour exécuter le programme d'installation doit être membre du groupe local Administrateurs et avoir l'autorisation de créer des bases de données et d'y accéder sur l'instance de  [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui héberge les bases de données du serveur de rapports.  
  
-   L’installation doit être en mesure d’utiliser les valeurs par défaut pour réserver les URL qui fournissent l’accès au serveur de rapports et au [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]. Ces valeurs sont le port 80, un caractère générique fort et les noms de répertoire virtuel aux formats **ReportServer_\<***nom_instance***>** et **Reports_\<***nom_instance***>**.  
  
-   L'installation doit être en mesure d'utiliser les valeurs par défaut pour créer les bases de données du serveur de rapports. Ces valeurs sont **ReportServer** et **ReportServerTempDB**. Si vous avez des bases de données d'une précédente installation, le programme d'installation sera bloqué car il ne peut pas configurer le serveur de rapports dans la configuration par défaut pour le mode natif. Vous devez renommer, déplacer ou supprimer les bases de données pour débloquer le programme d'installation.  
  
 Si votre ordinateur ne satisfait pas à toutes les spécifications d'une installation par défaut, vous devez installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode fichiers uniquement, puis utiliser le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour le configurer une fois l'installation terminée.
  
##  <a name="bkmk_defaultURLreservations"></a> Réservations d’URL par défaut  
 Les réservations d'URL se composent d'un préfixe, d'un nom d'hôte, d'un port et d'un répertoire virtuel :  
  
|Élément|Description|  
|----------|-----------------|  
|Préfixe|Le préfixe par défaut est HTTP. Si vous avez préalablement installé un certificat SSL (Secure Sockets Layer), l'installation tente de créer des réservations d'URL qui utilisent le préfixe HTTPS.|  
|Nom d'hôte|Le nom d'hôte par défaut est un caractère générique fort (+). Il spécifie que le serveur de rapports accepte toute requête HTTP sur le port désigné pour tout nom d’hôte qui se résout en l’ordinateur, y compris http://\<nom_ordinateur>/serveur_de_rapports, http://localhost/serveur_de_rapports ou http://\<adresse_IP>/serveur_de_rapports.|  
|Port|Le port par défaut est 80. Notez que si vous utilisez un port autre que le port 80, vous devez l'ajouter explicitement à l'URL lorsque vous ouvrez une application Web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans une fenêtre de navigateur.|  
|Répertoire virtuel|Par défaut, les répertoires virtuels sont créés au format ReportServer_\<*nom_instance*> pour le service Web Report Server et Reports_\<*nom_instance*> pour le [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]. Pour le service Web Report Server, le répertoire virtuel par défaut est **reportserver**. Par défaut, le répertoire virtuel du [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] est **reports**.|  
  
 Voici un exemple de chaîne URL complète :  
  
-   http://+:80/reportserver, fournit l'accès au serveur de rapports.  
  
-   http://+:80/reports, fournit l’accès à [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)].
  
##  <a name="bkmk_installwithwizard"></a> Installer le mode natif avec l’Assistant Installation de SQL Server  
 La liste suivante décrit les étapes et les options spécifiques à  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous pouvez sélectionner dans l'Assistant Installation de SQL Server. La liste ne décrit pas chacune des pages que vous voyez dans l'Assistant Installation. Seules les pages relatives à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et qui font partie d'une installation en mode natif sont décrites.  
  
1.  Exécutez l’Assistant Installation de SQL Server (setup.exe) et passez en revue les pages préliminaires suivantes :  
  
    -   Clé du produit  
  
    -   Termes du contrat de licence  
  
    -   Règles globales  
  
    -   Microsoft Update  
  
    -   Mises à jour du produit  
  
    -   Fichiers de configuration de l’installation  
  
    -   Règles d'installation  
  
2.  Dans la page **Rôle d'installation** , sélectionnez **Installation de fonctionnalités SQL Server**.  
  
     ![SQL Server Feature Installation for setup role](../../reporting-services/install-windows/media/rs-setuprole.png "SQL Server Feature Installation for setup role")  
  
3.  Dans la page **Sélection de fonctionnalités** , sélectionnez ce qui suit :  
  
    -   (1) **Services Moteur de base de données**, sauf si une instance du moteur de base de données est déjà installée.  
  
    -   (2) **Reporting Services - Natif**.  
  
     ![SSRS Native Mode Select in Feature Selection](../../reporting-services/install-windows/media/rs-setupfeatureselection-native-withcircles.png "SSRS Native Mode Select in Feature Selection")  
  
4.  Examinez les **Règles de fonctionnalité** transmises.  
  
5.  Dans la page de configuration de l’instance, n’oubliez pas que si vous choisissez de configurer une **instance nommée**, vous devez utiliser son nom dans les URL lorsque vous accédez au Gestionnaire de rapports et au serveur de rapports. Si l’instance s’appelle « THESQLINSTANCE », les URL seraient similaires à celles-ci :  
  
    -   `http://[ServerName]/ReportServer_THESQLINSTANCE`  
  
    -   `http://[ServerName]/Reports_THESQLINSTANCE`  
  
6.  **Configuration du serveur**: si vous prévoyez d’utiliser la fonctionnalité d’abonnement à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , configurez le type de démarrage **Automatique** pour SQL Server Agent dans la page **Configuration du serveur** .   Par défaut, le démarrage est manuel.  
  
7.  Ajoutez des administrateurs SQL Server dans la page **Configuration du moteur de base de données** .  
  
8.  Dans la page **Configuration de Reporting Services** , sélectionnez **Installer et configurer**.  
  
     ![SSRS Native Mode Configuration](../../reporting-services/install-windows/media/rs-setupconfiguration-native-with-circles.png "SSRS Native Mode Configuration")  
  
    > [!NOTE]  
    >  **Installer et configurer** n’est pas disponible, sauf si la fonctionnalité de base de données est également sélectionnée pour être installée.  
  
9. Règles de configuration de la fonctionnalité : vérifiez les règles transmises. l’assistant d’installation passe automatiquement à la page **Prêt pour l’installation** si toutes les règles sont respectées.  Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les règles vérifient si un catalogue du serveur de rapports et une base de données de catalogue temporaire n’existent pas déjà.  
  
10. ![remarque](../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "remarque")Dans la page **Prêt pour l’installation**, notez le chemin du fichier de configuration, car il vous servira ultérieurement pour obtenir un résumé de la configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] initiale des serveurs, notamment les composants installés, les comptes de service et les administrateurs.  
  
11. Une fois l'Assistant Installation de SQL Server terminé, vérifiez l'installation du mode natif par défaut à l'aide des étapes de base suivantes.  
  
    -   Ouvrez le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], puis vérifiez que vous pouvez vous connecter au serveur de rapports.  
  
    -   Ouvrez votre navigateur **avec des privilèges d’administrateur** et connectez-vous au [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)], par exemple `http://localhost/Reports`.  
  
    -   Ouvrez votre navigateur avec des privilèges d'administrateur et connectez-vous à la page du serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Par exemple,  `http://localhost/ReportServer`  
  
 Pour plus d'informations, consultez la section relative au mode natif dans les deux rubriques suivantes :  
  
 [Vérifier une installation de Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)  
  
 [Dépanner une installation de Reporting Services](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
  
##  <a name="bkmk_additional_configuration"></a> Configuration supplémentaire  
  
-   Pour configurer l’intégration de [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] et pouvoir épingler des éléments de rapport sur un tableau de bord [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)], consultez [Intégration du serveur de rapports Power BI &#40;Gestionnaire de configuration&#41;](../../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
-   Pour configurer la messagerie pour traiter les abonnements, consultez [Paramètres de messagerie : mode natif de Reporting Services &#40;Gestionnaire de configuration&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) et [Remise par courrier électronique dans Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   Pour configurer le [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] et le rendre accessible sur un ordinateur en vue de consulter et de gérer des rapports, consultez [Configurer un pare-feu pour accéder au serveur de rapports](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md) et [Configurer un serveur de rapports pour l’administration à distance](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md).  
  
## Voir aussi  
 [Dépanner une installation de Reporting Services](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
 [Vérifier une installation de Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Installation de fichiers uniquement &#40;Reporting Services&#41;](../../reporting-services/install-windows/files-only-installation-reporting-services.md)   
 [Initialiser un serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/initialize-a-report-server-ssrs-configuration-manager.md)   
 [Configurer des connexions SSL sur un serveur de rapports en mode natif](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)   
 [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [Installation de démarrage rapide de SQL Server 2016](../Topic/Quick-Start%20Installation%20of%20SQL%20Server%202016.md)  
  
  