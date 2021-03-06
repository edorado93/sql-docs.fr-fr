---
title: NavigationProperty, élément (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: a36b4d3b-6a6c-489b-8a46-2e6b925b568f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fbb0d38a4bcab7592893aaa63acb1bbb96dac5c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157579"
---
# <a name="navigationproperty-element-csdlbi"></a>Élément NavigationProperty (CSDLBI)
  L'élément NavigationProperty est un type complexe qui étend le type CSDL Member, pour prendre en charge les modèles de données Business Intelligence.  
  
> [!WARNING]  
>  Cet élément est destiné aux rapports et ne peut pas être modifié ou manipulé.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément NavigationProperty.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|CollectionCaption|non|Nom au pluriel pour faire référence à un jeu d'instances de la propriété de navigation.<br /><br /> Si cet attribut est omis, l'attribut Caption du membre de base est utilisé.|  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L’exemple suivant illustre une propriété de navigation, en CSDLBI version 1.1, qui décrit le lien entre la table Product SubCategory et la table Product dans un modèle tabulaire.  
  
```  
  
<NavigationProperty   
    Name="Product_Sub_Category_ProductSubcategoryKey"      
    Relationship="Sandbox.Product_Product_Sub_Category_Product_Sub_Category_ProductSubcategoryKey"  
     FromRole="Product_ProductSubcategoryKey"   
    ToRole="Product_Sub_Category_ProductSubcategoryKey">  
<bi:NavigationProperty   
     ReferenceName="Product Sub-Category_ProductSubcategoryKey" />  
</NavigationProperty>  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant illustre une propriété de navigation, en CSDLBI version 1.1, qui décrit la relation entre deux tables dans le cube Contoso Operations. La relation connecte la table Bike Category et la table Product Subcategory.  
  
```  
  
<NavigationProperty   
     Name="BikeSubcategory_ProductSubcategoryKey"   
     Relationship="Sandbox.Bike_BikeSubcategory_BikeSubcategory_ProductSubcategoryKey"   
     FromRole="Bike_ProductSubcategoryKey"   
     ToRole="BikeSubcategory_ProductSubcategoryKey">  
   <bi:NavigationProperty />  
</NavigationProperty>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du modèle d’objet tabulaire](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
