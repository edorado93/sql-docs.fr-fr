---
title: "Append (méthode) (colonnes ADOX) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c6c9323dbc1e3c69445dc09ad06373856fb67bc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="append-method-adox-columns"></a>Append (méthode) (colonnes ADOX)
Ajoute un nouveau [colonne](../../../ado/reference/adox-api/column-object-adox.md) de l’objet à la [colonnes](../../../ado/reference/adox-api/columns-collection-adox.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Colonne*  
 Le **colonne** objet à ajouter ou le nom de la colonne à créer et à ajouter.  
  
 *Type*  
 Ce paramètre est facultatif. A **Long** valeur qui spécifie le type de données de la colonne. Le *Type* paramètre correspond à la [Type](../../../ado/reference/adox-api/type-property-column-adox.md) propriété d’un **colonne** objet.  
  
 *DefinedSize*  
 Ce paramètre est facultatif. A **Long** valeur qui spécifie la taille de la colonne. Le *DefinedSize* paramètre correspond à la [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md) propriété d’un **colonne** objet.  
  
> [!NOTE]
>  Une erreur se produit lors de l’ajout un **colonne** à la **colonnes** collection d’un [Index](../../../ado/reference/adox-api/index-object-adox.md) si le **colonne** n’existe pas dans un [Table](../../../ado/reference/adox-api/table-object-adox.md) déjà ajouté à la [Tables](../../../ado/reference/adox-api/tables-collection-adox.md) collection.  
  
## <a name="applies-to"></a>S'applique à  
 [Collection de colonnes (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Colonnes et Tables ajouter des méthodes, exemple de propriété Name (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule exemple (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Exemple de propriété ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append (méthode) (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (méthode) (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (méthode) (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (méthode) (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (méthode) (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (méthode) (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append (méthode) (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)