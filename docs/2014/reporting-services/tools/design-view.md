---
title: Design, vue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.layoutview.f1
helpviewer_keywords:
- Layout View dialog box
ms.assetid: 6fa378aa-442f-4d2f-beab-02a0fb5cd3ce
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 32578d4810140314964d3e7e2ceaa8d836aa99bd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137389"
---
# <a name="design-view"></a>Vue Design
  Utilisez la vue Design pour organiser les éléments présents dans le rapport. Cette vue est parfois appelée aire de conception ou mode de conception.  
  
## <a name="report-design-surface"></a>Aire de conception du rapport  
 L'aire de conception se compose de trois sections : le corps, l'en-tête et le pied de page du rapport. Utilisez la boîte à outils pour sélectionner les éléments à placer dans ces trois sections. Utilisez le volet des données de rapportpour consulter des images, paramètres, sources de données et dataset, y compris les requêtes de dataset et listes de champs. Après avoir ajouté des éléments de rapport à l’aire de conception, faites glisser des champs de dataset du volet **Données du rapport** vers des régions de données telles qu’une table, une matrice ou une liste. Chaque élément présent dans l'aire de conception du rapport contient des propriétés qui peuvent être gérées via une boîte de dialogue de propriétés ou le volet Propriétés.  
  
## <a name="toolbox"></a>Boîte à outils  
 La Boîte à outils répertorie les régions de données et autres éléments de rapport disponibles pour votre rapport. Pour ajouter de éléments de rapport à partir de la Boîte à outils, double-cliquez sur l’élément qui vous intéresse ou faites-le glisser jusqu’à l’aire de conception. Vous pouvez ensuite modifier la forme et la taille en utilisant les handles d’objet.  
  
## <a name="report-data-pane"></a>Volet des données de rapport  
 Pour afficher le volet Données de rapport, dans le menu **Affichage** , cliquez sur **Données du rapport**. Utilisez ce volet pour définir des paramètres, des images, des sources de données et des datasets et pour référencer des champs intégrés tels que ReportName. Pour ajouter un nouvel élément, cliquez sur le menu **Nouveau** et sélectionnez un élément. Pour ajouter des champs calculés à un dataset existant, cliquez sur **Dataset**puis, dans la boîte de dialogue **Propriétés du dataset** , sélectionnez **Champs**. Sélectionnez un élément et cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Propriétés** . Vous pouvez également cliquer avec le bouton droit sur les éléments du volet des données de rapportpour ajouter des éléments ou mettre à jour leurs propriétés.  
  
 Pour ajouter des données et des images à un rapport, faites glisser les éléments depuis le volet des données de rapportvers les régions de données et les zones de texte de l'aire de conception.  
  
 Pour plus d'informations, consultez [Report Data Pane](../report-data/report-data-pane.md).  
  
## <a name="grouping-pane"></a>Volet de regroupement  
 Les groupes sont utilisés pour hiérarchiser vos données de rapport de façon visuelle et pour calculer des totaux. Utilisez le volet Regroupement pour afficher les groupes définis pour une table, une matrice ou une région de données de type liste. Par défaut, le volet Regroupement affiche l’ensemble des groupes de la région de données sélectionnée sous forme de liste aplatie. Le volet Regroupement est désactivé pour les régions de données Graphique et Jauge.  
  
 Pour afficher les groupes et leurs relations mutuelles, basculez le volet Regroupement en mode Avancé. Ce mode affiche la hiérarchie des membres des groupes, c’est-à-dire qu’il présente de façon visuelle les cellules de la région de données qui correspondent à chaque de groupe.  
  
 Pour plus d'informations, consultez [Grouping Pane](grouping-pane.md).  
  
## <a name="page-header-and-page-footer"></a>En-tête et pied de page  
 Un en-tête de page et un pied de page sont situés respectivement le long des bords supérieur et inférieur de chaque page. Les en-têtes et pieds de page peuvent contenir du texte statique, des images, des courbes, des rectangles, des bordures, une couleur d'arrière-plan et des images d'arrière-plan. Pour ajouter des éléments de rapport à un en-tête de page ou à pied de page, cliquez avec le bouton droit sur l’aire de conception et sélectionnez En-tête ou Pied de page. Les sections d’en-tête et de pied de page apparaissent sur l'aire de conception.  
  
## <a name="properties-pane"></a>Volet Propriétés  
 Utilisez le volet Propriétés pour afficher les propriétés de l'élément de rapport sélectionné sur l'aire de conception ou du groupe sélectionné dans le volet Regroupement. Vous pouvez aussi cliquer avec le bouton droit sur un groupe ou un élément de rapport sélectionné, puis cliquer sur **Propriétés** pour ouvrir la boîte de dialogue **Propriétés** correspondant au groupe ou à l’élément de rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md)   
 [Conseils de conception de rapport &#40;Générateur de rapports et SSRS&#41;](../report-design/report-design-tips-report-builder-and-ssrs.md)  
  
  
