---
title: SQRT (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b223b4f96f70e2d7526bcf1c9f076733da167619
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103623"
---
# <a name="sqrt-ssis-expression"></a>SQRT (expression SSIS)
  Renvoie la racine carrée d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_numérique*  
 Expression numérique d'un type de données numérique. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types de résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes  
 La fonction SQRT renvoie un résultat NULL si l'argument est NULL.  
  
 Elle échoue si l'argument est une valeur négative.  
  
 L'argument est converti vers le type de données DT_R8 avant le calcul de la racine carrée.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant renvoie la racine carrée d'un littéral numérique. Le résultat obtenu est 12.  
  
```  
SQRT(144)  
```  
  
 L'exemple suivant renvoie la racine carrée d'une expression, en l'occurrence le résultat de la soustraction des valeurs des colonnes **Value1** et **Value2** .  
  
```  
SQRT(Value1 - Value2)  
```  
  
 L'exemple suivant renvoie la longueur du troisième côté d'un triangle rectangle en appliquant la fonction SQUARE à deux variables puis en calculant la racine carrée de leur somme. Si la variable **Side1** a pour valeur 3 et que la variable **Side2** a pour valeur 4, la fonction SQRT renvoie 5.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  Dans les expressions, les noms de variables comportent toujours le préfixe \@.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;SSIS Expression&#41;](functions-ssis-expression.md)  
  
  
