---
title: 'Étape 4 : Test du package du didacticiel de la leçon 5 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3c9054cdbba90a3d0323a46e29aa4a860fbca7c7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060889"
---
# <a name="step-4-testing-the-lesson-5-tutorial-package"></a>Étape 4 : Test de la leçon 5 du Package du didacticiel
  Au moment de l'exécution, votre package récupère la valeur de la propriété `Directory` à partir d'une variable mise à jour à l'exécution au lieu d'utiliser le nom du répertoire d'origine spécifié lors de la création du package. La valeur de cette variable est remplie par le fichier SSISTutorial.dtsConfig.  
  
 Pour vérifier si le package met à jour la propriété Directory avec la nouvelle valeur lors de l'exécution, exécutez tout simplement le package. Étant donné que seuls trois fichiers de données exemple ont été copiés dans le nouveau répertoire, le flux de données ne sera exécuté que trois fois au lieu de parcourir les 14 fichiers du dossier d'origine.  
  
## <a name="checking-the-package-layout"></a>Vérification de la disposition du package  
 Avant de tester le package, vous devez vérifier que le flux de contrôle et le flux de données dans le package de la leçon 5 contiennent les objets affichés dans les diagrammes suivants. Le flux de contrôle doit être identique au flux de contrôle de la leçon 4. Le flux de données doit être identique au flux de données de la leçon 4.  
  
 **Flux de contrôle**  
  
 ![Flux de contrôle dans le package](../../2014/tutorials/media/task4lesson2control.gif "Flux de contrôle dans le package")  
  
 **Flux de données**  
  
 ![Flux de données dans le package](../../2014/tutorials/media/task9lesson1data.gif "Flux de données dans le package")  
  
### <a name="to-test-the-lesson-5-tutorial-package"></a>Pour tester le package du didacticiel Lesson 5  
  
1.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
2.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 6 : Utilisation des paramètres dans le modèle de déploiement de projet](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
