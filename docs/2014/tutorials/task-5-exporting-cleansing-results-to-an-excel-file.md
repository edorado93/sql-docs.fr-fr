---
title: 'Tâche 5 : Exportation des résultats du nettoyage vers un fichier Excel | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d2d52304ff9a8dae16e74d9d5aa7324adb2aac4f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48138169"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>Tâche 5 : Exportation des résultats du nettoyage vers un fichier Excel
  Dans cette tâche, vous allez exporter les résultats de l'activité de nettoyage dans un fichier Excel. Consultez [étape d’exportation](http://msdn.microsoft.com/library/hh213061.aspx#Export) rubrique pour plus d’informations.  
  
1.  Dans le volet droit, sélectionnez **Excel** pour le **Type de Destination**.  
  
2.  Cliquez sur **Parcourir**, spécifiez le nom de fichier de sortie en tant que **Cleansed Supplier List.xls**, puis cliquez sur **Open**.  
  
3.  Sélectionnez **uniquement les données** pour le **sortie** format pour exporter uniquement les données nettoyées. La deuxième option, **données et des informations sur le nettoyage**, vous permet d’exporter les détails de l’activité nettoyage avec les données nettoyées. Le **normaliser le Format** option vous permet d’appliquer les formats de sortie que vous définissez sur un domaine pour les valeurs de ce domaine. Vous n'avez pas défini de format de sortie pour un domaine dans le didacticiel.  
  
     ![Page des résultats de nettoyage de l’exportation](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Page des résultats de nettoyage de l’exportation")  
  
4.  Cliquez sur **exporter** pour exporter les données. Ne cliquez pas sur **Terminer** encore.  
  
5.  Cliquez sur **fermer** sur le **exportation** boîte de dialogue.  
  
6.  Cliquez sur **Terminer** pour terminer l’activité. Si vous avez oublié d’exporter les résultats avant de cliquer sur **Terminer**, cliquez sur **ouvrir projet de qualité des données** dans la page principale de **Client DQS**, sélectionnez **fournisseur nettoyer Liste** dans la liste des projets, puis cliquez sur **suivant** en bas de l’écran pour accéder à la **exporter** étape du processus de nettoyage à nouveau. Vous pouvez également basculer vers **gérer et afficher les résultats** onglet en cliquant sur **retour** bouton.  
  
7.  Ouvrez le **Cleansed Supplier List.xls** et procédez comme suit :  
  
    1.  Vérifiez qu'aucune adresse de messagerie ne se termine par adventure-work.com (sans caractère « s ») en recherchant « adventure-work.com » dans la feuille de calcul.  
  
    2.  Voir qu’il y a aucune **USA** valeur dans le **pays** colonne.  
  
    3.  Recherchez **Los Angeles** et voir que le **état** a la valeur **autorité de certification**.  
  
    4.  Confirmer qu’il n’y a aucun terme **Co.**, **corp.**, et **Inc.**.  
  
    5.  Supprimer le **Validation d’adresses** colonne à partir de la feuille de calcul et enregistrez le fichier excel. Cette colonne supplémentaire correspond au domaine composite Validation d'adresses.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 6 : Importation de valeurs depuis le projet de nettoyage de la liste des fournisseurs](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
