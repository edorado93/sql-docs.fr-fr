---
title: Installation de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 67843ed150df786dd84967e284e239c2cb019a91
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106719"
---
# <a name="installation-for-sql-server-2014"></a>Installation de SQL Server 2014
 ## <a name="-download-sql-server-2014-express-httpwwwhanselmancomblogdownloadsqlserverexpressaspx"></a>[ Télécharger SQL Server 2014 Express ](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  **Nous vous remercions d’avoir à [Scott Hanselman](http://www.hanselman.com/) pour la collecte de tous les liens de package de programme d’installation au même endroit !**
  
  L'Assistant Installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit une arborescence de fonctionnalités unique pour installer tous les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   Outils d'administration  
  
-   Composants de connectivité  
  
 Vous pouvez installer chaque composant individuellement ou sélectionner une combinaison de composants ci-dessus. Pour choisir au mieux les éditions et les composants disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [éditions et composants de SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) et [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est disponible en éditions 32 bits et 64 bits.
 
 **Essayez :**  
  
-   Vous avez un compte Azure ?  Puis accédez **[ici](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** pour lancer une Machine virtuelle avec SQL Server 2014 Service Pack 1 (SP1) déjà installé. Pour plus d’informations sur SQL Server 2014 (SP1), consultez [les informations de version de SQL Server 2014 Service Pack 1 ](https://support.microsoft.com/en-us/kb/3058865).  
  
## <a name="in-this-section"></a>Dans cette section  
 Que vous utilisiez l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l'invite de commandes pour installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le processus d'installation implique les étapes suivantes :  
  
 [Planification d'une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)  
 Décrit comment préparer l'ordinateur pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Configuration matérielle et logicielle requise.  
  
-   Vérifier les spécifications de l'Outil d'analyse de configuration système et les problèmes bloquants.  
  
-   Considérations sur la sécurité.  
  
 [Installer SQL Server 2014](install-sql-server.md)  
 Décrit les options d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Mise à niveau vers SQL Server 2014](upgrade-sql-server.md)  
 Décrit les options pour effectuer une mise à niveau vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Désinstaller SQL Server 2014](../../sql-server/install/uninstall-sql-server.md)  
 Décrit les procédures pour désinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
 [Installation d'un cluster de basculement SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 Cette section de la documentation d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] décrit comment installer et configurer un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 [Installer les fonctionnalités BI de SQL Server 2014](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les fonctions qui font partie de la plateforme BI de Microsoft sont notamment [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], ainsi que plusieurs applications clientes servant à créer ou utiliser des données analytiques. Cette section de la documentation de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] explique comment installer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="related-sections"></a>Sections connexes  
 [Rubriques de procédures relatives à l’installation](../../sql-server/install/installation-how-to-topics.md)  
 Fournit des liens vers des rubriques de procédure pour installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à partir de l'Assistant Installation, à partir de l'invite de commandes, à l'aide des fichiers de configuration, puis à l'aide de SysPrep.  
  
 [Installer des fonctionnalités SQL Server BI avec SharePoint &#40;PowerPivot et Reporting Services&#41;](../../sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
 Cette section explique comment installer les fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un environnement SharePoint. Elle identifie les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibles en fonction d'une version et d'une édition spécifiques de SharePoint. Elle inclut également des procédures d'installation de PowerPivot pour SharePoint et Reporting Services en mode SharePoint.  
  
 [L’installation de SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com/)  
 Explique comment installer et configurer les exemples et les exemples de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés liées à l'installation de SQL Server](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
  
