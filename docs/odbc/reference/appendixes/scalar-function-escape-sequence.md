---
title: Séquence d’échappement de fonction scalaire | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0913458d683d7641145b262552e147033dbfc054
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660787"
---
# <a name="scalar-function-escape-sequence"></a>Séquence d’échappement de fonction scalaire
ODBC utilise les séquences d’échappement pour les fonctions scalaires. La syntaxe de cette séquence d’échappement est comme suit :  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *Échappement ODBC-scalaire-fonction* :: =  
  
 *ODBC-ÉCHAP-initiateur* fn *fonction scalaire ODBC ÉCHAP-marque de fin*  
  
 *fonction scalaire* :: = *nom de la fonction* (*liste d’arguments*)  
  
 (Les définitions pour les éléments non terminaux *nom de la fonction* et *nom de la fonction* (*liste d’arguments*) sont dérivés de la liste des fonctions scalaires dans [ Annexe e : les fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-ÉCHAP-initiateur* :: = {}  
  
 *ODBC ÉCHAP-marque de fin* :: =}  
  
 Pour déterminer si la source de données prend en charge les procédures et le pilote prend en charge la syntaxe d’appel de procédure ODBC, une application peut appeler **SQLGetInfo**. Pour plus d’informations, consultez [annexe e : scalaire fonctions](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
