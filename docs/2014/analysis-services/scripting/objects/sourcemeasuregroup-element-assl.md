---
title: Élément SourceMeasureGroup (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SourceMeasureGroup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SourceMeasureGroup
helpviewer_keywords:
- SourceMeasureGroup element
ms.assetid: aaa7cc0b-162a-4c31-ab03-a90f81eeca00
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 98cf2ab2b8f97c976f0be4f9a008eb162116b124
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099319"
---
# <a name="sourcemeasuregroup-element-assl"></a>Élément SourceMeasureGroup (ASSL)
  Identifie le groupe de mesures servant de source de données à une colonne de structure d'exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructureColumn xsi:type="TableMiningStructureColumn">  
   ...  
   <SourceMeasureGroup xsi:type="MeasureGroupBinding">...</SourceMeasureGroup>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[MeasureGroupBinding](../data-type/binding-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) de type [TableMiningStructureColumn](../data-type/tableminingstructurecolumn-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [Type de données de liaison &#40;ASSL &#41;](../data-type/binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Les éléments qui correspondent aux parents de `SourceMeasureGroup` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.MiningStructureColumn> et <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
