---
title: Filtre (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d740148052712a69a39e0de314496733b3b26a8b
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740528"
---
# <a name="filter-mdx"></a>Filter (MDX)


  Retourne le jeu résultant du filtrage d'un jeu spécifié selon une condition de recherche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Filter(Set_Expression, Logical_Expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Logical_Expression*  
 Expression logique MDX (Multidimensional Expressions) valide qui prend la valeur True ou False.  
  
## <a name="remarks"></a>Notes  
 Le **filtre** fonction évalue l’expression logique spécifiée par rapport à chaque tuple dans le jeu spécifié. La fonction retourne un jeu composé de chaque tuple dans le jeu spécifié où l’expression logique prend la valeur **true**. Si aucun tuple donnent comme résultat **true**, un ensemble vide est retourné.  
  
 Le **filtre** fonctionne de manière similaire à celle de la [IIf](../mdx/iif-mdx.md) (fonction). Le **IIf** fonction retourne uniquement une des deux options en fonction de l’évaluation d’une expression logique MDX, tandis que la **filtre** fonction retourne un jeu de tuples qui satisfait la condition de recherche spécifié. En effet, le **filtre** fonction exécute `IIf(Logical_Expression, Set_Expression.Current, NULL)` sur chaque tuple du jeu et retourne le jeu obtenu.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre l'utilisation de la fonction Filter sur l'axe des lignes d'une requête afin de retourner uniquement les dates où le Montant des ventes sur Internet est supérieur à $10 000 :  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 La fonction Filter peut également s'utiliser à l'intérieur des définitions de membre calculées. L’exemple suivant retourne la somme de la `Measures.[Order Quantity]` membre, agrégé sur les neuf premiers mois de 2003 contenus dans le `Date` dimension, à partir de la **Adventure Works** cube. Le **PeriodsToDate** fonction définit les tuples dans le jeu sur lequel le **d’agrégation** fonction s’exécute. Le **filtre** fonction limite les tuples retournés à ceux ayant des valeurs inférieures de la mesure Reseller Sales Amount pour la période précédente.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
