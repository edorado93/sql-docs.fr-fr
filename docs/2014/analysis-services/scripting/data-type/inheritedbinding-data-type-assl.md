---
title: Type de données InheritedBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- InheritedBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- InheritedBinding
helpviewer_keywords:
- InheritedBinding data type
ms.assetid: a61f58c5-62d6-44e8-a02f-db2b17d1f256
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3859b2efa2f4847d9b45f124b1f8177b4e16dc68
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168039"
---
# <a name="inheritedbinding-data-type-assl"></a>Type de données InheritedBinding (ASSL)
  Définit un type de données dérivé indiquant qu’un [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md) élément hérite ses liaisons de l’attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<InheritedBinding>...</InheritedBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Liaison](binding-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|None|  
|Éléments dérivés|Consultez [de liaison](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [Type de données de liaison &#40;ASSL&#41; ](binding-data-type-assl.md) élément.  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.InheritedBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données de liaison &#40;ASSL&#41;](binding-data-type-assl.md)   
 [Sources de données et liaisons &#40;SSAS multidimensionnel&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
