---
title: Élément CalculationProperty (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CalculationProperty Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalculationProperty
helpviewer_keywords:
- CalculationProperty element
ms.assetid: 5f0b4cfc-7d25-4c01-a517-cc2e89859be3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cfd8d16293314db4a9ca382d6a4042dd0a493f06
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161699"
---
# <a name="calculationproperty-element-assl"></a>Élément CalculationProperty (ASSL)
  Contient une collection de propriétés d’interface utilisateur pour un calcul utilisé dans un [MdxScript](mdxscript-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CalculationProperties>  
   <CalculationProperty>  
      <CalculationReference>...</CalculationReference>  
      <CalculationType>...</CalculationType>  
      <Translations>...</Translations>  
      <Description>...</Description>  
      <Visible>...</Visible>  
      <SolveOrder>...</SolveOrder>  
      <FormatString>...</FormatString>  
      <ForeColor>...</ForeColor>  
      <BackColor>...</BackColor>  
            <FontName>...</FontName>  
            <FontSize>...</FontSize>  
            <FontFlags>...</FontFlags>  
            <NonEmptyBehavior>...</NonEmptyBehavior>  
      <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
      <DisplayFolder>...</DisplayFolder>  
   </CalculationProperty>  
</CalculationProperties>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CalculationProperties](../collections/calculationproperties-element-assl.md)|  
|Éléments enfants|[AssociatedMeasureGroupID](../properties/id-element-assl.md), [BackColor](../properties/backcolor-element-assl.md), [CalculationReference](../properties/calculationreference-element-assl.md), [CalculationType](../properties/calculationtype-element-assl.md), [Description](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [FontFlags](../properties/fontflags-element-assl.md), [FontName](../properties/name-element-assl.md), [FontSize](../properties/fontsize-element-assl.md), [ForeColor](../properties/forecolor-element-assl.md), [FormatString](../properties/formatstring-element-assl.md), [NonEmptyBehavior](../properties/nonemptybehavior-element-assl.md), [SolveOrder](../properties/solveorder-element-assl.md), [traductions](../collections/translations-element-assl.md), [Visible](../properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
