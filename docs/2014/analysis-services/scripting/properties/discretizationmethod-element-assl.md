---
title: Élément DiscretizationMethod (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DiscretizationMethod Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationMethod
helpviewer_keywords:
- DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 75308b5270eb762236be22fc0838a480474898dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200472"
---
# <a name="discretizationmethod-element-assl"></a>Élément DiscretizationMethod (ASSL)
  Définit la méthode à utiliser pour la discrétisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationMethod>...</DiscretizationMethod>  
   ...  
</DimensionAttribute>  
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
|Éléments parents|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de l'élément `DiscretizationMethod` détermine comment les valeurs de l'élément `DimensionAttribute` ou `ScalarMiningStructureColumn` sont discrétisées ou organisées en un jeu de groupes spécifique. Pour plus d’informations sur les méthodes de discrétisation, consultez [méthodes de discrétisation &#40;d’exploration de données&#41;](../../data-mining/discretization-methods-data-mining.md).  
  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Automatic*|Équivaut à la méthode de discretisation AUTOMATIC pour les colonnes de structure d'exploration de données.|  
|*EqualAreas*|Équivaut à la méthode de discretisation EQUAL_AREAS pour les colonnes de structure d'exploration de données.|  
|*Clusters*|Équivaut à la méthode de discretisation CLUSTERS pour les colonnes de structure d'exploration de données.|  
|*Seuils*|Équivaut à la méthode de discretisation THRESHOLDS pour les colonnes de structure d'exploration de données.|  
|*EqualRanges*|Équivaut à la méthode de discretisation EQUAL_RANGES pour les colonnes de structure d'exploration de données.|  
  
 L'énumération qui correspond aux valeurs autorisées de l'élément `DiscretizationMethod` dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.DiscretizationMethod>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
