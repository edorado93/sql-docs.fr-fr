---
title: Système de fichiers Azure Data Lake Store, tâche | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0c6b4c27b0edde310ba3252dd67bf8f51f40f0e5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48136559"
---
# <a name="azure-data-lake-store-file-system-task"></a>Système de fichiers Azure Data Lake Store, tâche
Le **tâche de système de fichiers Azure Data Lake Store** permet aux utilisateurs d’effectuer diverses opérations de système de fichiers sur [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/en-us/services/data-lake-store/).

Pour ajouter une tâche de système de fichiers Azure Data Lake Store à un package, faites-la glisser depuis la boîte à outils SSIS vers la zone de conception. Double-cliquez sur la tâche, ou avec le bouton droit de la tâche, puis sélectionnez **modifier**pour ouvrir la boîte de dialogue de l’éditeur de tâche.

La propriété **Opération** indique l’opération de système de fichiers à réaliser. Les opérations suivantes sont prises en charge.

* **CopyToADLS :** charger des fichiers dans ADLS.
* **CopyFromADLS :** télécharger des fichiers depuis ADLS.

Pour toute opération, vous devez spécifier un gestionnaire de connexions Azure Data Lake.

Voici les descriptions des propriétés spécifiques à chaque opération.

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory :** Spécifie le répertoire source qui contient les fichiers à charger.
* **FileNamePattern :** spécifie un filtre de nom de fichier pour les fichiers sources. Charger uniquement les fichiers dont le nom correspond au modèle spécifié. Les caractères génériques `*` et `?` sont pris en charge.
* **SearchRecursively :** indique si des fichiers à charger doivent être recherchés de manière récursive dans le répertoire source.
* **AzureDataLakeDirectory :** spécifie le répertoire de destination ADLS dans lequel charger les fichiers.
* **FileExpiry :** spécifie une date d’expiration et l’heure pour les fichiers chargés dans ADLS, ou laissez cette propriété vide pour indiquer que les fichiers n’expirent jamais.

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory :** spécifie le répertoire source ADLS qui contient les fichiers à télécharger.
* **SearchRecursively :** indique si des fichiers à télécharger doivent être recherchés de manière récursive dans le répertoire source.
* **LocalDirectory :** spécifie le répertoire de destination dans lequel stocker les fichiers téléchargés.
