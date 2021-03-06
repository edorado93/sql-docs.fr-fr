---
title: Imprimer un rapport (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: b96936c9-c387-41a9-8c19-6eb325769ffd
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 081f7b0c748b06a87e8497582ffc8dabbda3e57f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095199"
---
# <a name="print-a-report-report-builder-and-ssrs"></a>Imprimer un rapport (Générateur de rapports et SSRS)
  Après avoir enregistré un rapport sur un serveur de rapports, vous pouvez l'afficher et l'imprimer à partir d'un navigateur, du Gestionnaire de rapports ou de toute application permettant d'afficher un rapport exporté. Avant d'enregistrer un rapport, vous pouvez l'imprimer après avoir affiché son aperçu.  
  
 Lorsque vous imprimez un rapport, vous pouvez spécifier le format du papier à utiliser. Le format du papier détermine le nombre de pages dans un rapport et les données de rapport qui remplissent chaque page. Le format de papier affecte uniquement les rapports rendus avec des convertisseurs de saut de page manuel : PDF, Image et Impression. La définition du format de papier n'a aucun effet sur d'autres convertisseurs. Pour plus d’informations, consultez [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
 Dans la barre d'outils de la visionneuse de rapports dans le Gestionnaire de rapports ou en mode Aperçu dans le Générateur de rapports, vous pouvez exporter un rapport vers un convertisseur de saut de page manuel ou cliquer sur le bouton Imprimer pour imprimer une copie du rapport. Vous pouvez devoir définir le format de papier ou d'autres propriétés de mise en page. Utilisez la boîte de dialogue **Propriétés du rapport** pour modifier les propriétés de mise en page, y compris le format de papier.  
  
 Vous pouvez spécifier les marges de page pour l'impression à deux emplacements : en mode Création et en mode Exécution.  
  
-   **Mode Création.** Lorsque vous définissez des marges de page en mode Création, ces paramètres sont enregistrés dans la définition de rapport lorsque vous enregistrez le rapport.  
  
-   **Mode Exécution.** Lorsque vous définissez des marges de page en mode Exécution, ces informations ne sont pas enregistrées dans la définition de rapport. La prochaine fois que vous imprimerez le rapport, vous obtiendrez les paramètres de la définition du rapport à moins que vous n'indiquiez de nouveau vos marges pour l'impression.  
  
    > [!NOTE]  
    >  Les marges pour l'impression ne sont pas affichées en mode Création et Exécution. Il n'y a aucune relation entre l'aire de conception et la zone d'impression de votre rapport. Pour afficher les marges pour l’impression, en mode Exécution, cliquez sur Page sous l’onglet **Exécuter** dans le ruban.  
  
 Pour plus d’informations sur la pagination des rapports, consultez [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-print-a-report-in-report-builder"></a>Pour imprimer un rapport dans le Générateur de rapports  
  
1.  Ouvrez un rapport.  
  
2.  Sous l’onglet Accueil, cliquez sur **Exécuter**.  
  
3.  (Facultatif) Cliquez sur **Page** pour visualiser l’apparence du rapport imprimé.  
  
4.  (Facultatif) Cliquez sur **Mise en page** pour définir le papier, l’orientation et les marges.  
  
    > [!NOTE]  
    >  Les valeurs par défaut proviennent des propriétés du rapport, qui sont définies en mode Conception. Les valeurs que vous définissez dans cette boîte de dialogue **Mise en page** s’appliquent uniquement à la session active. Si vous fermez puis rouvrez le rapport, il présentera à nouveau les valeurs par défaut.  
  
5.  Cliquez sur **Imprimer**.  
  
6.  Dans la boîte de dialogue **Imprimer** , sélectionnez une imprimante et spécifiez d’autres options d’impression.  
  
### <a name="to-print-a-report-from-a-web-browser-application"></a>Pour imprimer un rapport à partir d'un navigateur Web  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'au rapport à imprimer. Ouvrez le rapport.  
  
3.  Dans la barre d’outils, en haut du rapport, cliquez sur **Imprimer**.  
  
    > [!NOTE]  
    >  Lorsque vous imprimez un rapport HTML pour la première fois, le serveur de rapports vous invite à installer un contrôle ActiveX d'impression. Vous devez installer et configurer ce contrôle pour pouvoir imprimer.  
  
4.  Dans la boîte de dialogue **Imprimer** , sélectionnez une imprimante, puis cliquez sur **Imprimer**.  
  
### <a name="to-print-a-report-from-other-applications"></a>Pour imprimer un rapport à partir d'autres applications  
  
1.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'au rapport à imprimer. Ouvrez le rapport.  
  
2.  Dans la barre d’outils en haut du rapport, sélectionnez un format de rendu, puis cliquez sur **Exporter**. Le rapport s'ouvre dans une application visionneuse correspondant au format de rendu.  
  
     De fait, si vous sélectionnez le format PDF, le rapport s'ouvre dans Adobe Acrobat Reader.  
  
3.  Dans le menu **Fichier** de ce programme, cliquez sur **Imprimer**.  
  
### <a name="to-change-paper-size"></a>Pour modifier le format de papier  
  
1.  Cliquez avec le bouton droit à l’extérieur du corps du rapport, puis cliquez sur **Propriétés du rapport**.  
  
2.  Dans **Mise en page**, sélectionnez une valeur dans la liste **Format de papier** . Chaque option remplit les propriétés **Largeur** et **Hauteur** . Vous pouvez également spécifier un format personnalisé en tapant des valeurs numériques dans les zones **Largeur** et **Hauteur** . [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  Les valeurs qui définissent la taille sont assorties d'une unité par défaut qui est basée sur les paramètres régionaux de l'utilisateur. Pour choisir une unité différente, tapez un indicateur d'unité physique comme cm, mm, pt ou pc après la valeur numérique.  
  
### <a name="to-set-page-margins-in-design-mode"></a>Pour définir des marges de page en mode Création  
  
-   Cliquez avec le bouton droit sur la zone bleue autour de l’aire de conception, cliquez sur **Propriétés du rapport**, puis cliquez sur la page **Mise en page** .  
  
### <a name="to-set-page-margins-in-run-mode"></a>Pour définir des marges de page en mode Exécution  
  
-   Cliquez sur **Mise en page** sous l’onglet **Exécuter** .  
  
## <a name="see-also"></a>Voir aussi  
 [Imprimer des rapports &#40;Générateur de rapports et SSRS&#41;](print-reports-report-builder-and-ssrs.md)   
 [Exportation de rapports &#40;Générateur de rapports et SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés du rapport, Mise en page &#40;Générateur de rapports&#41;](../report-properties-dialog-box-page-setup-report-builder.md)   
 [Mode Création de rapport &#40;Générateur de rapports&#41;](report-design-view-report-builder.md)  
  
  
