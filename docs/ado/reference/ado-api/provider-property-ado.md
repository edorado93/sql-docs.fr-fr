---
title: Fournisseur, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::get_Provider
- Connection15::PutProvider
- Connection15::put_Provider
- Connection15::GetProvider
- Connection15::Provider
helpviewer_keywords:
- Provider property [ADO]
ms.assetid: 0ff70e72-0061-4ffc-90fb-e3ea23129bb2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22ee1b88ee6065a49c53ae7024c93e869099ca3a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755287"
---
# <a name="provider-property-ado"></a>Provider, propriété (ADO)
Indique le nom du fournisseur pour un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur qui indique le nom du fournisseur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **fournisseur** propriété pour définir ou retourner le nom du fournisseur pour une connexion. Cette propriété peut également être définie par le contenu de la [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propriété ou le *ConnectionString* argument de la [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) méthode ; Toutefois, en spécifiant un fournisseur dans plusieurs endroits lors de l’appel le **Open** méthode peut avoir des résultats imprévisibles. Si aucun fournisseur n’est spécifié, la propriété par défaut est MSDASQL ([fournisseur Microsoft OLE DB pour ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)).  
  
 Le **fournisseur** propriété est en lecture/écriture lorsque la connexion est fermée et en lecture seule lorsqu’il est ouvert. Le paramètre ne prend pas effet tant que vous ouvrez le **connexion** objet ou l’accès le [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection de la **connexion** objet. Si le paramètre n’est pas valide, une erreur se produit.  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Provider et DefaultDatabase propriétés exemple (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider et DefaultDatabase propriétés exemple (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Fournisseur Microsoft OLE DB pour ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [Annexe A : Fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
