---
title: 'Étape 7 : Ajout et configuration de la destination OLE DB | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 442c841d-d528-4bf0-8724-7156f909ee50
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 89073c9da5a4cd6243bd1fcdcd53d3fa13d02bb9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48138455"
---
# <a name="step-7-adding-and-configuring-the-ole-db-destination"></a>Étape 7 : ajout et configuration de la destination OLE DB
  Votre package peut maintenant extraire des données à partir de la source de fichier plat pour les transformer dans un format compatible avec la destination. La tâche suivante consiste à charger les données transformées dans la destination. Pour charger les données, vous devez ajouter une destination OLE DB au flux de données. La destination OLE DB peut utiliser une table de base de données, un affichage ou une commande SQL pour charger les données dans plusieurs bases de données compatibles OLE DB.  
  
 Au cours de cette procédure, vous allez ajouter et configurer une destination OLE DB pour utiliser le Gestionnaire de connexions OLE DB que vous avez créé précédemment.  
  
### <a name="to-add-and-configure-the-sample-ole-db-destination"></a>Pour ajouter et configurer la destination OLE DB fournie en exemple  
  
1.  Dans la **Boîte à outils SSIS**, développez **Autres destinations**, puis faites glisser **Destination OLE DB** dans la zone de conception de l’onglet **Flux de données** . Placez la destination OLE DB directement sous la transformation **Lookup Date Key** .  
  
2.  Sélectionnez la transformation **Lookup Date Key** et faites glisser la flèche verte vers la nouvelle **Destination OLE DB** pour connecter les deux composants.  
  
3.  Dans la boîte de dialogue **Sélection entrée et sortie** , dans la zone de liste de **Sortie** , cliquez sur **Sortie de recherche avec correspondance**, puis cliquez sur **OK**.  
  
4.  Sur l’aire de conception **Flux de données** , cliquez sur **Destination OLE DB** dans le composant **Destination OLE DB** que vous venez d’ajouter, puis remplacez le nom par **Sample OLE DB Destination**.  
  
5.  Double-cliquez sur **Sample OLE DB Destination**.  
  
6.  Dans la boîte de dialogue **Éditeur de destination OLE DB** , vérifiez que **localhost.AdventureWorksDW2012** est sélectionné dans la zone **Gestionnaire de connexions OLE DB** .  
  
7.  Dans la zone **Nom de la table ou de la vue** , tapez ou sélectionnez **[dbo].[FactCurrencyRate]**.  
  
8.  Cliquez sur le bouton **Nouveau** pour créer une table.  Modifiez le nom de la table dans le script en **NewFactCurrencyRate**.  Cliquez sur **OK**.  
  
9. Après avoir cliqué sur **OK**, la boîte de dialogue se ferme et **Nom de la table ou de la vue** est automatiquement modifié en **NewFactCurrencyRate**.  
  
10. Cliquez sur **Mappages**.  
  
11. Vérifiez que les colonnes d’entrée **AverageRate**, **CurrencyKey**, **EndOfDayRate**et **DateKey** sont correctement mappées aux colonnes de destination. Si des colonnes aux noms identiques sont mappées, le mappage est correct.  
  
12. Cliquez sur **OK**.  
  
13. Cliquez avec le bouton droit sur la **Destination OLE DB exemple** , puis cliquez sur **Propriétés**.  
  
14. Dans la fenêtre Propriétés, vérifiez que le `LocaleID` propriété est définie sur **anglais (États-Unis)** et`DefaultCodePage` propriété est définie sur **1252**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 8 : Rendre le package de la leçon 1 plus facile à comprendre](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Destination OLE DB](data-flow/ole-db-destination.md)  
  
  
