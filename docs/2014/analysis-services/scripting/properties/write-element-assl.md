---
title: Élément Write (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Write Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Write element
ms.assetid: d8f7a367-d7bf-4b40-acb4-19c8bc8c6c20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dd39e3354ee68a2e716e4cfbf50e41e371bf5303
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104249"
---
# <a name="write-element-assl"></a>Élément Write (ASSL)
  Détermine si les données ou les métadonnées peuvent être écrites pour une donnée [CubeDimensionPermission](../data-type/permission-data-type-assl.md) ou [autorisation](../data-type/permission-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Write>...</Write>  
   ...  
</CubeDimensionPermission>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Aucun*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CubeDimensionPermission](../objects/cubepermission-element-assl.md), [autorisation](../data-type/permission-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Aucun accès aux données ou métadonnées de l'objet parent n'est autorisé.|  
|*Autorisé*|Un accès en écriture aux données et métadonnées de l'objet parent est autorisé.|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de `Write` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.CubeDimensionPermission> et <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de cube &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Dimension élément &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
