---
title: Élément CalculationReference (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CalculationReference Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalculationReference
helpviewer_keywords:
- CalculationReference element
ms.assetid: 4dd18b1f-55c3-4673-afbe-736d1bce8331
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b97ce0ccb7c9a8ba6bc5f1e5778c334380747bc6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049120"
---
# <a name="calculationreference-element-assl"></a>Élément CalculationReference (ASSL)
  Contient le nom du jeu nommé ou de cellule calculée référencée par le [CalculationProperty](../objects/calculationproperty-element-assl.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CalculationProperty>  
   ...  
   <CalculationReference>...</CalculationReference>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément obligatoire qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Si la valeur de l'élément `CalculationReference` ne correspond pas au nom d'un jeu nommé existant ou d'une définition de cellule calculée, l'élément `CalculationReference` est ignoré.  
  
 L’élément qui correspond au parent de `CalculationReference` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Élément MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Élément MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
