---
title: "Priorit&#233;s et associativit&#233; des op&#233;rateurs | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "associativité [Integration Services]"
  - "priorités [Integration Services]"
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# Priorit&#233;s et associativit&#233; des op&#233;rateurs
  Chaque opérateur de l'ensemble des opérateurs pris en charge par l'évaluateur d'expression se caractérise par une priorité dans la hiérarchie des priorités et par un sens d'évaluation. Le sens de l'évaluation d'un opérateur repose sur l'associativité des opérateurs. Les opérateurs dont le degré de priorité est le plus élevé sont évalués avant les opérateurs de priorité moindre. Si une expression complexe comporte plusieurs opérateurs, l'ordre de priorité détermine l'ordre d'exécution des opérations. Cet ordre peut affecter considérablement la valeur résultante. Certains opérateurs ont une priorité identique. Si une expression contient plusieurs opérateurs de priorité identique, ceux-ci sont évalués dans un certain sens, de la gauche vers la droite ou de la droite vers la gauche.  
  
 Le tableau suivant décrit les priorités des opérateurs, de la plus élevée à la moins élevée. Les opérateurs de même niveau ont une priorité identique.  
  
|Symbole d'opérateur|Type d’opération|Associativité|  
|---------------------|-----------------------|-------------------|  
|( )|Expression|De gauche à droite|  
|–, !, ~|Unaire|De droite à gauche|  
|Casts|Unaire|De droite à gauche|  
|*, / ,%|Multiplicatif|De gauche à droite|  
|+, –|Additive|De gauche à droite|  
|\<, >, \<=, >=|Relationnel|De gauche à droite|  
|==, !=|Égalité|De gauche à droite|  
|&|ET au niveau du bit|De gauche à droite|  
|^|OU exclusif au niveau du bit|De gauche à droite|  
|&#124;|Opération OR inclusive au niveau du bit|De gauche à droite|  
|&&|ET logique|De gauche à droite|  
|&#124;&#124;|OU logique|De gauche à droite|  
|? :|Expression conditionnelle|De droite à gauche|  
  
## Voir aussi  
 [Opérateurs &#40;expression SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  