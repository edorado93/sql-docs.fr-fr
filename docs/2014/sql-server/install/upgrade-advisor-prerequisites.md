---
title: Configuration requise du Conseiller de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- requirements [Upgrade Advisor]
- software [Upgrade Advisor]
- system requirements [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, prerequisites
- prerequisites [Upgrade Advisor]
- Upgrade Advisor [SQL Server], prerequisites
ms.assetid: d21a39e5-5f81-4096-a7dd-f244e4779992
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 130059c64357d36ddf6c5eea7e27b15b0e42778c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48148509"
---
# <a name="upgrade-advisor-prerequisites"></a>Configuration requise par le Conseiller de mise à niveau
  Cette rubrique décrit la configuration logicielle requise par le Conseiller de mise à niveau.  
  
## <a name="prerequisites"></a>Prérequis  
 La configuration requise pour l'installation et l'exécution du Conseiller de mise à niveau est la suivante :  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] depuis SP2, Windows 7 ou [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.  
  
-   Windows Installer 4.5. Vous pouvez installer le programme d’installation de Windows à partir de la [site Web du programme d’installation Windows](http://go.microsoft.com/fwlink/?LinkId=49112).  
  
-   The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], depuis .NET Framework 4. Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] est disponible sur le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support du produit et à partir de la [site Web de téléchargement du SDK, redistribuable et le service pack](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
    -   Pour installer .NET Framework 4 à partir du support de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], localisez la racine du lecteur de disque. Ensuite, double-cliquez sur le dossier \redist, sur le dossier DotNetFrameworks et exécutez dotNetFx40_Full_x86_x64.exe (pour les systèmes d'exploitation 32 bits et 64 bits).  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom est requis pour l’installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Conseiller de mise à niveau et n’est pas installé par l’installation du Conseiller de mise à niveau. Le programme d’installation vous oblige à télécharger et installer le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom à partir de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour installer le Conseiller de mise à niveau](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
