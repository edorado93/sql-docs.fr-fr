---
title: Ensemble de lignes DISCOVER_OBJECT_MEMORY_USAGE | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DISCOVER_OBJECT_MEMORY_USAGE rowset
ms.assetid: 211cfa04-7bd6-43fe-8bd5-bfbff78bdafb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cfea97bbc901c86c5c90a72b74d9ddba396e745c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126549"
---
# <a name="discoverobjectmemoryusage-rowset"></a>Ensemble de lignes DISCOVER_OBJECT_MEMORY_USAGE
  Fournit des informations sur les ressources mémoire utilisées par les objets.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_OBJECT_MEMORY_USAGE` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`||Chemin d'accès au parent de l'objet actuel.|  
|`OBJECT_ID`|`DBTYPE_WSTR`||ID de l'objet tel que défini lors de la création.|  
|`OBJECT_MEMORY_SHRINKABLE`|`DBTYPE_I8`||Quantité totale de mémoire (en octets) utilisée par tous les objets réductibles appartenant directement à l'objet actuel. La valeur actuelle n'inclut pas la mémoire des objets détenus par les objets nommés appartenant à l'objet actuel.|  
|`OBJECT_MEMORY_NONSHRINKABLE`|`DBTYPE_I8`||Quantité de mémoire (en octets) de tous les objets non réductibles appartenant directement à l'objet actuel. La valeur actuelle n'inclut pas la mémoire des objets détenus par les objets nommés appartenant à l'objet actuel.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Numéro de version de métadonnées de l'objet. Ce nombre change chaque fois que l'objet est modifié.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Numéro de lignage des données contenues dans l'objet. Ce nombre est incrémenté chaque fois que l'objet est traité.|  
|`OBJECT_TYPE_ID`|`DBTYPE_I4`||Réservé à une utilisation interne.|  
|`OBJECT_TIME_CREATED`|`DBTYPE_DBTIMESTAMP`||Heure UTC du serveur au moment où l'objet a été créé.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_OBJECT_MEMORY_USAGE` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`|Facultatif.|  
|`OBJECT_ID`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  
