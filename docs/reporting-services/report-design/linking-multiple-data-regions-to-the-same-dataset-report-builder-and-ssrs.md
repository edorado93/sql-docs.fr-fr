---
title: "Liaison de plusieurs r&#233;gions de donn&#233;es &#224; un m&#234;me dataset (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 90c94a91-8fb2-42cb-b998-563691f30d2d
caps.latest.revision: 10
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 10
---
# Liaison de plusieurs r&#233;gions de donn&#233;es &#224; un m&#234;me dataset (G&#233;n&#233;rateur de rapports et SSRS)
  Vous pouvez ajouter plusieurs régions de données à un rapport paginé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour proposer des vues différentes des données d’un même dataset de rapport. Par exemple, vous pouvez afficher des données dans une table et les représenter dans un graphique. Pour ce faire, vous devez utiliser des étendues et des expressions identiques pour les expressions de filtre, les expressions de tri et les expressions de groupe appropriées.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Pour savoir s'il convient d'utiliser un graphique avec une table ou une matrice pour représenter des données identiques, il peut s'avérer utile d'établir un parallèle entre une table et les graphiques à base de formes d'une part et une matrice et les graphiques en aires, les graphiques à barres et les histogrammes d'autre part. Une table avec un seul groupe de lignes peut facilement être représentée sous forme de graphique à secteurs. À mesure que vous ajoutez des groupes de lignes, vous pouvez choisir différents types de graphiques pour représenter au mieux les groupes imbriqués. L'ajout de groupes de lignes imbriqués à un graphique à secteurs augmente le nombre de secteurs dans le graphique. Vous devez déterminer si le nombre d'instances de groupe correspondant au groupe parent et au groupe enfant réunis est trop important pour être représenté dans un seul graphique à secteurs. Lorsque plusieurs valeurs de groupe sont représentées sous forme de petits secteurs dans un graphique à secteurs, vous pouvez définir une propriété de telle sorte que toutes les valeurs en dessous d'un certain seuil soient représentées sous forme de graphique à secteurs à part entière. Pour plus d’informations, consultez [Regrouper des petits secteurs sur un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md).  
  
 Une table comportant plusieurs groupes de lignes peut être représentée sous forme d'histogramme avec plusieurs groupes de catégorie. Pour plus d’informations, consultez [Afficher les mêmes données dans une matrice et sur un graphique &#40;Générateur de rapports&#41;](../../reporting-services/report-design/display-the-same-data-on-a-matrix-and-a-chart-report-builder.md). Pour obtenir un exemple de table et de graphique présentant différentes vues d'un même dataset de rapport, consultez le rapport Product Line Sales dans Exemples de rapports AdventureWorks. Comme la table et le graphique sont liés au même dataset dans ce rapport, lorsque vous cliquez sur le bouton de tri interactif d'Employee Name dans la table Top Employees, le nouvel ordre de tri est automatiquement répercuté dans le graphique Top Employees. Pour plus d'informations sur le téléchargement de cet exemple de rapport et d'autres rapports, consultez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Exemples de rapports du Générateur de rapports et du Concepteur de rapports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
 La représentation d'une matrice qui comporte plusieurs groupes de lignes et de colonnes peut être améliorée à l'aide d'un graphique en aires, d'un graphique à barres ou d'un histogramme avec des groupes de catégories et de séries. Utilisez les mêmes expressions de groupe pour les groupes de colonnes de la matrice et les groupes de catégories du graphique et les mêmes expressions de groupe pour les groupes de lignes de la matrice et les groupes de séries du graphique. Gardez à l'esprit que le nombre d'instances de groupe influe sur la lisibilité du graphique. Vous pouvez définir des groupes en fonction de valeurs de plages pour réduire le nombre d'instances de groupe dans un rapport. Pour plus d’informations, consultez [Exemples d’expressions de groupe &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md).  
  
## Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Régions de données imbriquées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/nested-data-regions-report-builder-and-ssrs.md)  
  
  