---
title: Élément CreatedTimestamp (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CreatedTimestamp Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CreatedTimestamp
helpviewer_keywords:
- CreatedTimestamp element
ms.assetid: 35f5dd33-ea82-4be3-a117-69136aa9d1a4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e13b032b34ee63a7c7a939d7ad17b8ceb1786739
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191019"
---
# <a name="createdtimestamp-element-assl"></a>Élément CreatedTimestamp (ASSL)
  Contient l'horodateur de création en lecture seule de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Assembly> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <CreatedTimestamp>...</CreatedTimestamp>  
   ...  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|DateTime|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Assembly](../objects/assembly-element-assl.md), [Cube](../objects/cube-element-assl.md), [base de données](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [Dimension](../objects/dimension-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [Partition](../objects/partition-element-assl.md), [Autorisation](../data-type/permission-data-type-assl.md), [Perspective](../objects/perspective-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `CreatedTimestamp` élément contient en lecture seule `DateTime` valeur qui représente la date et l’heure à laquelle l’objet a été créé sur une instance donnée de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. La valeur de cet élément ne peut pas être vide.  
  
 Les éléments qui correspondent aux parents de `CreatedTimestamp` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.Assembly>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.DataSourceView>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MdxScript>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure>, <xref:Microsoft.AnalysisServices.Partition>, <xref:Microsoft.AnalysisServices.Permission>, et <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
