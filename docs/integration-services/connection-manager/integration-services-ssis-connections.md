---
title: "Connexions Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.connectionmanager.f1"
  - "sql13.dts.designer.adddtsconnection.f1"
helpviewer_keywords: 
  - "Packages Integration Services, connexions"
  - "Packages SSIS, connexions"
  - "sources [Integration Services], connexions"
  - "packages [Integration Services], connexions"
  - "destinations [Integration Services], connexions"
  - "tâches [Integration Services], connexions"
  - "connexions [Integration Services], à propos des connexions"
  - "connexions [Integration Services]"
  - "packages SQL Server Integration Services, connexions"
ms.assetid: 72f5afa3-d636-410b-9e81-2ffa27772a8c
caps.latest.revision: 92
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 91
---
# Connexions Integration Services (SSIS)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent des connexions pour effectuer différentes tâches et pour implémenter des fonctionnalités [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] :  
  
-   Connexion à des banques de données sources et de destination telles que du texte, des données XML, des classeurs Excel et des bases de données relationnelles pour extraire et charger des données.  
  
-   Connexion à des bases de données relationnelles qui contiennent des données de référence pour effectuer des recherches exactes ou floues.  
  
-   Connexion à des bases de données relationnelles pour exécuter des instructions SQL telles que des commandes SELECT, DELETE et INSERT, et également des procédures stockées.  
  
-   Connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour effectuer des tâches de maintenance et de transfert telles que la sauvegarde de bases de données et le transfert de connexions.  
  
-   Écriture d'entrées de journal dans des fichiers texte, dans des fichiers XML et dans des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , écriture de configurations de package dans des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour créer des tables de travail temporaires dont certaines transformations ont besoin pour effectuer leur travail.  
  
-   Connexion à des projets et des bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour accéder à des modèles d'exploration de données, traiter des cubes et des dimensions, et exécuter du code DDL.  
  
-   Spécification de fichiers et de dossiers existants, ou création de nouveaux fichiers et dossiers à utiliser avec des énumérateurs et des tâches de boucles Foreach.  
  
-   Connexion à des files d’attente de messages, à WMI (Windows Management Instrumentation), à SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object), au web et à des serveurs de messagerie.  
  
 Pour établir ces connexions, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise des gestionnaires de connexions, comme décrit dans la section suivante.  
  
## Gestionnaires de connexions  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise le gestionnaire de connexions comme représentation logique d'une connexion. Au moment de la conception, vous définissez les propriétés d'un gestionnaire de connexions pour décrire la connexion physique qu' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée lors de l'exécution du package. Par exemple, un gestionnaire de connexions inclut la propriété **ConnectionString** que vous définissez lors de la conception ; au moment de l'exécution, une connexion physique est créée à l'aide de la valeur de la propriété de chaîne de connexion.  
  
 Un package peut utiliser plusieurs instances d'un type de gestionnaire de connexions et vous pouvez définir les propriétés sur chaque instance. Au moment de l'exécution, chaque instance d'un type de gestionnaire de connexions crée une connexion qui possède des attributs différents.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit différents types de gestionnaires de connexions qui permettent aux packages d'établir une connexion à divers serveurs et à diverses sources de données :  
  
-   Il y a des gestionnaires de connexions intégrés que le programme d'installation installe lorsque vous installez [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Il y a des gestionnaires de connexions qui sont téléchargeables à partir du site Web [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
-   Vous pouvez créer votre propre gestionnaire de connexions personnalisé si les gestionnaires de connexions existants ne répondent pas à vos besoins.  
  
### Gestionnaires de connexions intégrés  
 Le tableau suivant répertorie les types de gestionnaires de connexions fournis par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
|Type|Description|Rubrique|  
|----------|-----------------|-----------|  
|ADO|Établit une connexion à des objets ADO (ActiveX Data Objects).|[Gestionnaire de connexions ADO](../../integration-services/connection-manager/ado-connection-manager.md)|  
|ADO.NET|Établit une connexion à une source de données au moyen d'un fournisseur .NET.|[Gestionnaire de connexions ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)|  
|CACHE|Lit les données du flux de données ou d'un fichier cache (.caw) et peut enregistrer des données dans le fichier cache.|[Gestionnaire de connexions du cache](../../integration-services/data-flow/transformations/cache-connection-manager.md)|  
|DQS|Établit une connexion à un serveur Data Quality Services et à une base de données Data Quality Services sur le serveur.|[Gestionnaire de connexions de nettoyage DQS](../../integration-services/data-flow/transformations/dqs-cleansing-connection-manager.md)|  
|EXCEL|Établit une connexion à un fichier de classeur Excel.|[Gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager.md)|  
|FILE|Établit une connexion à un fichier ou un dossier.|[Gestionnaire de connexions de fichiers](../../integration-services/connection-manager/file-connection-manager.md)|  
|FLATFILE|Établit une connexion à des données dans un fichier plat unique.|[Gestionnaire de connexions de fichiers plats](../../integration-services/connection-manager/flat-file-connection-manager.md)|  
|FTP|Établit une connexion à un serveur FTP.|[Gestionnaire de connexions FTP](../../integration-services/connection-manager/ftp-connection-manager.md)|  
|HTTP|Établit une connexion à un serveur Web.|[Gestionnaire de connexions HTTP](../../integration-services/connection-manager/http-connection-manager.md)|  
|MSMQ|Établit une connexion à une file d'attente de messages.|[Gestionnaire de connexions MSMQ](../../integration-services/connection-manager/msmq-connection-manager.md)|  
|MSOLAP100|Établit une connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|[Gestionnaire de connexions Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)|  
|MULTIFILE|Établit une connexion à plusieurs fichiers et dossiers.|[Gestionnaire de connexions de fichiers multiples](../../integration-services/connection-manager/multiple-files-connection-manager.md)|  
|MULTIFLATFILE|Établit une connexion à plusieurs fichiers et dossiers de données.|[Gestionnaire de connexions de fichiers plats multiples](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md)|  
|OLEDB|Établit une connexion à une source de données au moyen d'un fournisseur OLE DB.|[Gestionnaire de connexions OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)|  
|ODBC|Établit une connexion à une source de données au moyen d'ODBC.|[Gestionnaire de connexions ODBC](../../integration-services/connection-manager/odbc-connection-manager.md)|  
|SMOServer|Établit une connexion à un serveur SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects).|[Gestionnaire de connexions SMO](../../integration-services/connection-manager/smo-connection-manager.md)|  
|SMTP|Établit une connexion à un serveur de messagerie SMTP.|[Gestionnaire de connexions SMTP](../../integration-services/connection-manager/smtp-connection-manager.md)|  
|SQLMOBILE|Établit une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.|[Gestionnaire de connexions de SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|  
|WMI|Établit une connexion à un serveur et spécifie la portée de la gestion WMI (Windows Management Instrumentation) sur le serveur.|[Gestionnaire de connexions WMI](../../integration-services/connection-manager/wmi-connection-manager.md)|  
  
### Gestionnaires de connexions pouvant être téléchargés  
 Le tableau suivant répertorie d'autres types de gestionnaires de connexions que vous pouvez télécharger à partir du site Web [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
> [!IMPORTANT]  
>  Les gestionnaires de connexions répertoriés dans le tableau suivant fonctionnent uniquement avec [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] et [!INCLUDE[ssDeveloperEd11](../../includes/ssdevelopered11-md.md)].  
  
|Type|Description|Rubrique|  
|----------|-----------------|-----------|  
|ORACLE|Établit une connexion à un serveur Oracle \<informations de version>.|Le gestionnaire de connexions Oracle est le composant de gestionnaire de connexions du Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour Oracle par Attunity. Le Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour Oracle par Attunity inclut également une source et une destination. Pour plus d'informations, consultez la page de téléchargement [Microsoft Connectors for Oracle and Teradata by Attunity](http://go.microsoft.com/fwlink/?LinkId=251526)(en anglais).|  
|SAPBI|Établit une connexion à un système SAP NetWeaver BI version 7.|Le gestionnaire de connexions SAP BI est le composant de gestionnaire de connexions du Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] for SAP BI. Le Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] for SAP BI inclut également une source et une destination. Pour plus d'informations, consultez la page de téléchargement [Microsoft SQL Server 2008 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=262016).|  
|TERADATA|Établit une connexion à un serveur Teradata \<informations de version>.|Le gestionnaire de connexions Teradata est le composant de gestionnaire de connexions du Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour Teradata par Attunity. Le Connecteur [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour Teradata par Attunity inclut également une source et une destination. Pour plus d'informations, consultez la page de téléchargement [Microsoft Connectors for Oracle and Teradata by Attunity](http://go.microsoft.com/fwlink/?LinkId=251526)(en anglais).|  
  
### Gestionnaires de connexions personnalisés  
 Vous pouvez également écrire des gestionnaires de connexions personnalisés. Pour plus d'informations, consultez [Developing a Custom Connection Manager](../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md).  
  
## Tâches associées  
 Pour plus d’informations sur l’ajout et la suppression d’un gestionnaire de connexions dans un package, consultez [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../Topic/Add,%20Delete,%20or%20Share%20a%20Connection%20Manager%20in%20a%20Package.md).  
  
 Pour plus d’informations sur la définition des propriétés d’un gestionnaire de connexions dans un package, consultez [Définir les propriétés d’un gestionnaire de connexions](../Topic/Set%20the%20Properties%20of%20a%20Connection%20Manager.md).  
  
## Contenu connexe  
  
-   Vidéo, [Utilisez Microsoft Attunity Connector for Oracle pour améliorer les performances des packages](http://technet.microsoft.com/sqlserver/gg598963.aspx), sur technet.microsoft.com  
  
-   Articles Wiki, [Connectivité SSIS](http://social.technet.microsoft.com/wiki/contents/articles/sql-server-integration-services-ssis.aspx#Connectivity), sur social.technet.microsoft.com  
  
-   Entrée de blog, [Se connecter à MySQL SSIS](http://go.microsoft.com/fwlink/?LinkId=217669), sur blogs.msdn.com.  
  
-   Article technique [Extraction et chargement des données SharePoint dans SQL Server Integration Services](http://go.microsoft.com/fwlink/?LinkId=247826), sur msdn.microsoft.com.  
  
-   Article technique, [You get "DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" error message when using Oracle connection manager in SSIS](http://go.microsoft.com/fwlink/?LinkId=233696) (Le message d’erreur « DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER’» s’affiche lors de l’utilisation du gestionnaire de connexions Oracle dans SSIS), sur le site support.microsoft.com.  
  
  