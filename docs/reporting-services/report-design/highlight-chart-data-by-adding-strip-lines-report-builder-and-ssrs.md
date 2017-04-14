---
title: "Mettre en surbrillance des donn&#233;es de graphique en ajoutant des bandes (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: addd6137-4b6e-4e88-a7e8-9600fcd1ccce
caps.latest.revision: 6
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 6
---
# Mettre en surbrillance des donn&#233;es de graphique en ajoutant des bandes (G&#233;n&#233;rateur de rapports et SSRS)
  Les franges sont des plages horizontales ou verticales qui assombrissent l'arrière-plan du graphique à intervalles réguliers ou personnalisés. Vous pouvez utiliser des bandes pour obtenir les résultats suivants :  
  
-   Améliorer la lisibilité des valeurs individuelles sur le graphique. Spécifiez des bandes à des intervalles réguliers pour séparer les points de données lors de la lecture du graphique.  
  
-   Mettre en surbrillance les dates qui arrivent à des intervalles réguliers. Par exemple, dans un état des ventes, vous pouvez utiliser des bandes pour identifier les points des données indiquant les week-ends.  
  
-   Mettre en surbrillance une plage clé spécifique. À l'aide de l'exemple précédent, vous pouvez utiliser une bande pour mettre en surbrillance la plage la plus élevée des ventes qui se trouve entre 80 et 100 $.  
  
 Les bandes ne sont pas applicables aux types de graphiques à base de forme ou polaires.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour afficher des franges entrelacées à des intervalles réguliers sur un graphique  
  
1.  Pour afficher des franges horizontales, cliquez avec le bouton droit sur l’axe vertical du graphique, puis cliquez sur **Propriétés de l’axe vertical**.  
  
     Pour afficher des franges verticales, cliquez avec le bouton droit sur l’axe horizontal du graphique, puis cliquez sur **Propriétés de l’axe horizontal**.  
  
2.  Sélectionnez l'option **Utiliser l'entrelacement** . Des franges grises apparaîtront sur votre graphique.  
  
3.  (Facultatif) Spécifiez une couleur pour les franges à l’aide de la liste déroulante **Couleur** adjacente.  
  
### Pour afficher des franges entrelacées à des intervalles personnalisés sur un graphique  
  
1.  Pour afficher des franges horizontales, cliquez avec le bouton droit sur l’axe vertical du graphique, puis cliquez sur **Propriétés de l’axe vertical**.  
  
     Pour afficher des franges verticales, cliquez avec le bouton droit sur l’axe horizontal du graphique, puis cliquez sur **Propriétés de l’axe horizontal**.  
  
     Les propriétés de l'axe s'affichent dans la fenêtre Propriétés.  
  
2.  Dans la section **Apparence** du volet Propriétés, pour la propriété StripLines, cliquez sur le bouton Modifier la collection (…) pour ouvrir **l’Éditeur de collections ChartStripLine**.  
  
3.  Cliquez sur **Ajouter** pour ajouter une nouvelle bande à la collection.  
  
4.  Cliquez sur StripWidth pour spécifier la largeur de la bande, mesurée en pouces sur le rapport. Si vous mettez en surbrillance des dates ou des heures, cliquez sur StripWidthType, puis sélectionnez un intervalle de temps.  
  
5.  Tapez une valeur ou une expression pour Intervalle afin de spécifier la fréquence à laquelle la bande se répétera.  Par exemple, si vous spécifiez un intervalle de 10, et que votre largeur de bande est de 5, les bandes s'afficheront aux valeurs 0 à 5, 15 à 20, 30 à 35, etc.  
  
> [!NOTE]  
>  Par défaut, Intervalle a la valeur Auto, ce qui signifie que le graphique ne calculera pas d’intervalle pour les bandes personnalisées. Le graphique ne calcule des intervalles pour les bandes que si une valeur d'intervalle est définie.  
  
## Voir aussi  
 [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Ajouter une moyenne mobile à un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)  
  
  