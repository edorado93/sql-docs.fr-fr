---
title: Élément StorageMode (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- StorageMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- StorageMode
helpviewer_keywords:
- StorageMode element
ms.assetid: 197e8153-1ab6-43ba-a7e9-ae9be19ac511
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 11c7c07f0373d3d271c39146509c73b11c9b7f9b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104939"
---
# <a name="storagemode-element-assl"></a>Élément StorageMode (ASSL)
  Détermine le mode de stockage de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <StorageMode>...</StorageMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*MOLAP*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Élément de cube &#40;ASSL&#41;](../objects/cube-element-assl.md), [Dimension élément &#40;ASSL&#41;](../objects/dimension-element-assl.md), [élément MeasureGroup &#40;ASSL&#41;](../objects/group-element-assl.md), [Partition Élément &#40;ASSL&#41;](../objects/partition-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*MOLAP*|Le parent utilise le mode OLAP multidimensionnel (MOLAP).|  
|*ROLAP*|Le parent utilise le mode OLAP relationnel (ROLAP).|  
|*HOLAP*|Le parent utilise le mode OLAP hybride (HOLAP). **Remarque :** cette valeur n’est pas valide pour [Dimension](../objects/dimension-element-assl.md) éléments parents.|  
|*InMemory*|Le parent utilise le stockage IMBI.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `StorageMode` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.StorageMode>.  
  
 Les éléments qui correspondent aux parents de `StorageMode` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup> et <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
