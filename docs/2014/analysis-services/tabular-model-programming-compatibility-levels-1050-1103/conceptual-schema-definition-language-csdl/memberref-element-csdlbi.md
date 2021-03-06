---
title: Élément MemberRef (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bb0912afd99c7a4859ca4750a3ba1b66fdecd5f5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205713"
---
# <a name="memberref-element-csdlbi"></a>Élément MemberRef (CSDLBI)
  L'élément MemberRef spécifie le nom d'une propriété qui est la cible d'une référence.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément MemberRef.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Nom   |Oui|Nom de la propriété contenue dans un élément MemberRef.|  
  
## <a name="memberrefs-element"></a>Élément MemberRefs  
 MemberRefs est un type complexe qui définit une collection de membres dans laquelle chaque membre est contenu dans un élément MemberRef.  
  
 Le tableau suivant répertorie les éléments et les attributs de type MemberRefs.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|MemberRef|Oui|Chaîne contenant la référence de membre.|  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple suivant, en CSDLBI version 1.1, représente une partie du modèle de données exemple AdventureWorks qui définit la table Products. L'élément MemberRef est utilisé pour chaque colonne incluse dans l'ensemble de champs par défaut du modèle.  
  
```  
  
<bi:EntityType>  
   <bi:DefaultDetails>  
     <bi:MemberRef Name="Color" />  
     <bi:MemberRef Name="DealerPrice" />  
     <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant, en CSDLBI version 1.1, représente une partie du cube Contoso Operations qui définit la table Bikes. Dans cet exemple, un élément MemberRef est utilisé pour spécifier le nom de la colonne utilisée en tant qu'ensemble de champs par défaut dans les rapports et un autre élément MemberRef permet de référencer la colonne qui fournit l'ordre de tri.  
  
```  
  
<bi:DefaultDetails>  
   <bi:MemberRef Name="Color" />  
</bi:DefaultDetails>  
  
<bi:SortMembers>  
   <bi:MemberRef Name="Color" />  
</bi:SortMembers>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence sur les annotations pour le décisionnel dans CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
