---
title: "R&#233;cup&#233;rer &#224; partir d&#39;une d&#233;faillance d&#39;instance de cluster de basculement | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "clusters [SQL Server], récupération après une panne"
  - "clustering de basculement [SQL Server], récupération après une panne"
  - "défaillances matérielles [SQL Server]"
  - "récupération d'échecs de cluster de basculement [SQL Server]"
ms.assetid: 3d151d0c-e841-4325-8606-c094de37d7d1
caps.latest.revision: 31
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 31
---
# R&#233;cup&#233;rer &#224; partir d&#39;une d&#233;faillance d&#39;instance de cluster de basculement
  Cette rubrique explique comment récupérer des échecs de cluster à l'aide du composant logiciel enfichable Gestionnaire du cluster de basculement après un basculement dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Le composant logiciel enfichable Gestionnaire du cluster de basculement est l'application de gestion du service de cluster de basculement Windows Server (WSFC).  
  
-   [Récupérer en cas d'erreur irréparable](#Scenario1)  
  
-   [Récupérer en cas d'erreur logicielle](#Scenario2)  
  
##  <a name="Scenario1"></a> Récupérer en cas d'erreur irréparable  
 Utilisez les étapes suivantes pour récupérer une erreur irréparable. L'erreur peut être provoquée, par exemple, par la défaillance d'un contrôleur de disque ou du système d'exploitation. Dans ce cas, l'erreur est due à une défaillance matérielle dans le nœud 1 d'un cluster à deux nœuds.  
  
1.  Après la défaillance du nœud 1, la FCI de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bascule sur le nœud 2.  
  
2.  Supprimez le nœud 1 de la FCI. Pour cela, à partir du nœud 2, ouvrez le composant logiciel enfichable Gestionnaire du cluster de basculement, cliquez avec le bouton droit sur Node1, cliquez sur **Déplacer des actions**, puis sur **Supprimer le nœud**.  
  
3.  Assurez-vous que le nœud 1 a été supprimé de la définition de cluster.  
  
4.  Installez le nouveau matériel pour remplacer le matériel défaillant dans le nœud 1.  
  
5.  Ajoutez le nœud 1 au cluster existant à l'aide du composant logiciel enfichable Gestionnaire du cluster de basculement. Pour plus d’informations, consultez [Avant l’installation du clustering de basculement](../../../sql-server/failover-clusters/install/before-installing-failover-clustering.md).  
  
6.  Vérifiez que les comptes administrateurs sont bien les mêmes sur tous les nœuds de cluster.  
  
7.  Exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] afin d'ajouter le nœud 1 à la FCI. Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
##  <a name="Scenario2"></a> Récupérer d'une erreur réparable  
 Utilisez les étapes suivantes pour récupérer suite à une erreur réparable. Dans ce cas, la défaillance est causée par le nœud 1, défectueux ou hors connexion, mais il n'est pas rompu de manière irrémédiable. Cette erreur peut être due à une défaillance du système d'exploitation, à une défaillance matérielle ou à une défaillance dans l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] elle-même.  
  
1.  Après la défaillance du nœud 1, la FCI bascule sur le nœud 2.  
  
2.  Résolvez le problème du nœud 1.  
  
3.  Vérifiez que le service WSFC fonctionne et que tous les nœuds sont en ligne.  
  
4.  Effectuez le basculement de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers le nœud récupéré.  
  
  