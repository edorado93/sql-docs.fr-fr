---
title: Élément ReportingWeekToMonthPattern (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportingWeekToMonthPattern Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportingWeekToMonthPattern
helpviewer_keywords:
- ReportingWeekToMonthPattern element
ms.assetid: 8d7c694d-d5c5-4faa-af78-155779e84fe9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 61667552266673b71bae7b8046e47d6c4db5c9f1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083419"
---
# <a name="reportingweektomonthpattern-element-assl"></a>Élément ReportingWeekToMonthPattern (ASSL)
  Définit le modèle de semaine en mois de création de rapports pour le [TimeBinding](../data-type/binding-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<TimeBinding>  
   ...  
   <ReportingWeekToMonthPattern>...</ReportingWeekToMonthPattern>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*445*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*445*|4 semaines dans le premier mois du trimestre, 4 semaines dans le deuxième mois et 5 semaines dans le troisième mois.|  
|*454*|4 semaines dans le premier mois du trimestre, 5 semaines dans le deuxième mois et 4 semaines dans le troisième mois.|  
|*544*|5 semaines dans le premier mois du trimestre, 4 semaines dans le deuxième mois et 4 semaines dans le troisième mois.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `ReportingWeekToMonthPattern` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.ReportingWeekToMonthPattern>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
