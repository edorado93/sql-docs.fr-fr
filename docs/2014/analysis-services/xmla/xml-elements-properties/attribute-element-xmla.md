---
title: Attribut d’élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Attribute Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Attribute
- microsoft.xml.analysis.attribute
- urn:schemas-microsoft-com:xml-analysis#Attribute
helpviewer_keywords:
- Attribute element
ms.assetid: 0df9cf44-dc5f-4234-8a5a-daac8aabc0d6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7baad7e154cda5ce52e67f08af46e7344f6af1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128209"
---
# <a name="attribute-element-xmla"></a>Élément Attribute (XMLA)
  Définit ou filtre un membre dans un attribut sur lequel un parent [insérer](../xml-elements-commands/insert-element-xmla.md), [mise à jour](../xml-elements-commands/update-element-xmla.md), ou [Drop](../xml-elements-commands/drop-element-xmla.md) commande effectue.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Attributes>  
   ...  
   <Attribute>  
      <AttributeName>...</AttributeName>  
      <Keys>...</Keys>  
      <!-- The following elements are included only for attributes contained in the Attributes element of a parent Insert or Update command -->  
      <Name>...</Name>  
      <Translations>...</Translations>  
      <CustomRollup>...</CustomRollup>  
      <CustomRollupProperties>...</CustomRollupProperties>  
      <UnaryOperator>...</UnaryOperator>  
      <SkippedLevels>...</SkippedLevels>  
   </Attribute>  
   ...  
</Attributes>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attributs](attributes-element-xmla.md)|  
  
 **Éléments enfants**  
  
|||  
|-|-|  
|**Ancêtre ou Parent**|**Élément enfant**|  
|[DROP](../xml-elements-commands/drop-element-xmla.md), [où](name-element-xmla.md), [clés](keys-element-xmla.md)|  
|[Insérer](../xml-elements-commands/insert-element-xmla.md), [mise à jour](../xml-elements-commands/update-element-xmla.md)|[AttributeName](name-element-xmla.md), [CustomRollup](customrollup-element-xmla.md), [CustomRollupProperties](properties-element-xmla.md), [clés](keys-element-xmla.md), [nom](name-element-xmla.md), [ SkippedLevels](skippedlevels-element-xmla.md), [traductions](translations-element-xmla.md), [UnaryOperator](unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le `Attribute` élément définit le membre d’attribut qui est inséré, mis à jour ou supprimé, respectivement, par le `Insert`, `Update`, ou `Drop` commande. Comme ces commandes peuvent fonctionner uniquement sur les membres d’un attribut à la fois, le [attributs](attributes-element-xmla.md) collection de la `Insert`, `Update`, et `Drop` commandes peuvent contenir un seul `Attribute` élément. Toutefois, la collection `Attributes` de l'élément `Where` pour les commandes `Drop` et `Update` peut contenir plusieurs éléments `Attribute`, afin que vous puissiez filtrer les attributs à supprimer ou mettre à jour dans une dimension accessible en écriture.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)   
 [Dimensions activées en écriture](../../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
