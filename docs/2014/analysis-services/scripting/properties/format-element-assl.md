---
title: Mettre en forme, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Format Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Format
helpviewer_keywords:
- Format element
ms.assetid: 881ea707-52a7-46f7-ba16-ac2ec44eca22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ed7cf229d4ef65e324a59d2d9292948ae530147
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228009"
---
# <a name="format-element-assl"></a>Élément Format (ASSL)
  Contient le format requis de la [DataItem](../data-type/dataitem-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Valeurs autorisées pour le `Format` élément sont les formats de Microsoft Office Excel et les chaînes *TrimRight*, *TrimLeft*, *TrimAll*, et  *TrimNone*. Pour la troncature, le paramètre par défaut est *TrimRight* .  
  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Toute chaîne de format Excel|Les données sont mises en forme conformément à la chaîne de format nommée ou personnalisée spécifiée. Toutes les chaînes de format prises en charge par Excel peuvent être fournies.|  
|*TrimAll*|Les données sont tronquées à gauche et à droite.|  
|*TrimLeft*|Les données sont tronquées à gauche.|  
|*TrimNone*|Les données ne sont pas tronquées.|  
|*TrimRight*|Les données sont tronquées à droite.|  
  
 L’élément qui correspond au parent de `Format` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
