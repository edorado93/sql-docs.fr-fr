---
title: "LEN (expression SSIS) | Microsoft Docs"
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
  - "LEN (fonction)"
  - "nombre de caractères"
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 36
---
# LEN (expression SSIS)
  Renvoie le nombre de caractères d'une expression de caractères. Si la chaîne comprend des espaces de début et de fin, la fonction les inclut dans le nombre. La fonction LEN renvoie la même valeur pour une chaîne donnée, que celle-ci soit composée de caractères codés sur un octet ou sur deux octets.  
  
## Syntaxe  
  
```  
  
LEN(character_expression)  
```  
  
## Arguments  
 *character_expression*  
 Expression à évaluer.  
  
## Types des résultats  
 DT_I4  
  
## Notes  
 L’argument *character_expression* peut être d’un type de données DT_WSTR, DT_TEXT, DT_NTEXT ou DT_IMAGE. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Si *character_expression* est un littéral de chaîne ou une colonne de données avec le type de données DT_STR, il est implicitement converti dans le type de données DT_WSTR avant que la fonction LEN soit exécutée. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Cast &#40;expression SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Si l'argument transmis à la fonction LEN a un type de données BLOB (Binary Large Object Block), tel que DT_TEXT, DT_NTEXT ou DT_IMAGE, la fonction renvoie un nombre d'octets.  
  
 La fonction LEN renvoie un résultat NULL si l'argument est NULL.  
  
## Exemples d'expressions  
 Cet exemple renvoie la longueur d'un littéral de chaîne. Le résultat obtenu est 12.  
  
```  
LEN("Ball Bearing")  
```  
  
 L'exemple suivant renvoie la différence de longueur des valeurs des colonnes **FirstName** et **LastName** .  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 Renvoie la longueur d'un nom d'ordinateur à partir de la variable système **MachineName**.  
  
```  
LEN(@MachineName)  
```  
  
## Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  