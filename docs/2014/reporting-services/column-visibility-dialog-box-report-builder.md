---
title: Boîte de dialogue visibilité de colonne (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10127"
ms.assetid: 0c030cab-6087-45a5-99f0-c7bd693f20a1
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f6ab67682afc00057085fe3d0f793c51a28258d7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057763"
---
# <a name="column-visibility-dialog-box-report-builder"></a>Boîte de dialogue Visibilité de la colonne (Générateur de rapports)
  Utilisez la boîte de dialogue **Visibilité de la colonne** pour afficher ou masquer la colonne sélectionnée lorsque le rapport est exécuté pour la première fois, ou pour utiliser un autre élément de rapport pour activer/désactiver la visibilité de la colonne.  
  
## <a name="options"></a>Options  
 **Lors de la première exécution de l’état**  
 Sélectionnez une option pour indiquer le mode d'affichage initial de l'élément de rapport dans le rapport.  
  
 **Afficher**  
 Choisissez cette option pour afficher la colonne.  
  
 **Masquer**  
 Choisissez cette option pour masquer la colonne.  
  
 **Afficher ou masquer en fonction d’une expression**  
 Choisissez cette option pour modifier la visibilité initiale à l'aide d'une expression.  
  
 Tapez une expression qui prend la valeur d’un `Boolean` valeur `True` pour masquer l’élément et `False` pour afficher l’élément. Cliquez sur le bouton Expression (*fx*) pour modifier l’expression.  
  
 **Affichage peut être activé ou désactivé par cet élément de rapport**  
 Choisissez cette option pour afficher une image bascule qui permet à l'utilisateur d'afficher ou de masquer cette colonne dans une visionneuse de rapports HTML.  
  
 Tapez ou sélectionnez le nom d'une zone de texte du rapport dans laquelle afficher une image bascule, par exemple Textbox1. La zone de texte que vous choisissez doit figurer dans l'étendue actuelle ou contenante de cet élément de rapport. Par exemple, pour afficher ou masquer les lignes associées à un groupe enfant, sélectionnez une zone de texte dans une ligne associée au groupe parent. Pour afficher ou masquer un graphique, sélectionnez une zone de texte qui est dans la même étendue contenante que le graphique, par exemple le corps du rapport ou un rectangle.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Ajouter une action Développer ou Réduire à un élément &#40;Générateur de rapports et SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [Images &#40;Générateur de rapports et SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Boîte de dialogue Propriétés de l’image, Général &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
