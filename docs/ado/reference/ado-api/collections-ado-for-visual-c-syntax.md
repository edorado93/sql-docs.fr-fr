---
title: Collections (syntaxe ADO pour Visual C++) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- ADO for Visual C++ syntax [ADO]
- syntax indexes [ADO], ADO for Visual C++ syntax
- collections [ADO], ADO for Visual C++ syntax
ms.assetid: 6a0109a0-f2d9-4f7c-8e1e-42763f9acaea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d94570a337f564588b2709fd292eab5ed5396dc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679877"
---
# <a name="collections-ado-for-visual-c-syntax"></a>Collections (syntaxe ADO pour Visual C++)
## <a name="parameters"></a>Paramètres  
  
### <a name="methods"></a>Méthodes  
  
```  
Append(IDispatch *Object);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Append, méthode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Delete, méthode (collection Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Properties  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, _ADOParameter **ppvObject);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item, propriété (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="fields"></a>Champs  
  
### <a name="methods"></a>Méthodes  
  
```  
Append(BSTR bstrName, DataTypeEnum Type, long DefinedSize, FieldAttributeEnum Attrib);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Append, méthode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Delete, méthode (collection Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Properties  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOField **ppvObject);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item, propriété (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="errors"></a>Erreurs  
  
### <a name="methods"></a>Méthodes  
  
```  
Clear(void);  
Refresh(void);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Clear, méthode (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)  
  
-   [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Properties  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOError **ppvObject);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item, propriété (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="properties"></a>Properties  
  
### <a name="methods"></a>Méthodes  
  
```  
Refresh(void);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Properties  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOProperty **ppvObject);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item, propriété (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Collection d’erreurs (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Collection de champs (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Collection de paramètres (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
