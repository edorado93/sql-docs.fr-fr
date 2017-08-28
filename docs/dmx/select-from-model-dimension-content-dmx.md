---
title: "SELECT FROM &lt;modèle&gt;. DIMENSION_CONTENT (DMX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT
- FROM
- DIMENSION_CONTENT
dev_langs:
- DMX
helpviewer_keywords:
- mining models [Analysis Services], dimension content
- SELECT FROM <model>.DIMENSION_CONTENT statement
ms.assetid: 907fb3fb-2131-4a10-8635-2a39b9a805aa
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f9caf83d8d3d151f1b324f00abf5561549e111ad
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="select-from-ltmodelgtdimensioncontent-dmx"></a>SELECT FROM &lt;modèle&gt;. DIMENSION_CONTENT (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Un modèle d'exploration de données peut être utilisé comme dimension dans un cube OLAP, où chaque nœud du modèle est représenté en tant que membre de la dimension. **SELECT FROM \<modèle >. Dimension_CONTENT** instruction retourne le contenu du modèle qui se rapporte à son utilisation en tant que dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Ce paramètre est facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste séparée par des virgules des identificateurs des colonnes associées dérivés de l'ensemble de lignes de schéma de contenu.  
  
 *model*  
 Identificateur du modèle  
  
 *expression de condition*  
 Ce paramètre est facultatif. Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Ce paramètre est facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Les fournisseurs des algorithmes définissent le contenu à retourner et son mode d'organisation. Par exemple, le fournisseur peut limiter le nombre de nœuds décrits dans le contenu de la dimension.  
  
 Le tableau ci-dessous répertorie les colonnes dont le contenu de dimension peut être interrogé, et la fonction que chaque colonne effectue en tant que dimension d'exploration de données.  
  
|Colonne de l'ensemble de lignes CONTENT|Fonction dans la dimension d'exploration de données|  
|---------------------------|---------------------------------------|  
|ATTRIBUTE_NAME|Propriété de membre|  
|NODE_NAME|Propriété de membre|  
|NODE_UNIQUE_NAME|Attribut de clé.|  
|NODE_TYPE|Propriété de membre|  
|NODE_CAPTION|CaptionColumn de **clé** attribut.|  
|CHILDREN_CARDINALITY|Propriété de membre|  
|PARENT_UNIQUE_NAME|Relatedattribut de le **clé** attribut (ParentAttribute dans la hiérarchie parent-enfant).|  
|NODE_DESCRIPTION|Propriété de membre|  
|NODE_RULE|Propriété de membre|  
|MARGINAL_RULE|Propriété de membre|  
|NODE_PROBABILITY|Propriété de membre|  
|MARGINAL_PROBABILITY|Propriété de membre|  
|NODE_SUPPORT|Propriété de membre|  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a> Description  
 L'exemple sélectionne toutes les colonnes du contenu du modèle `[TM Decision Tree]` qui se rapportent à l'utilisation du modèle en tant que dimension.  
  
### <a name="code"></a>Code  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNEZ &#40; DMX &#41;](../dmx/select-dmx.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
