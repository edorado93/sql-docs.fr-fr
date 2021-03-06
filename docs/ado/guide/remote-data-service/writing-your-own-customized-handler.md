---
title: Écrire votre propre gestionnaire personnalisé | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
- customized handler in RDS [ADO]
ms.assetid: d447712a-e123-47b5-a3a4-5d366cfe8d72
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ced8796278ffab61b5f4e45b687e8059bb34255f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680197"
---
# <a name="writing-your-own-customized-handler"></a>Écriture d’un gestionnaire personnalisé
Vous souhaiterez écrire votre propre gestionnaire si vous êtes un administrateur de serveur IIS qui souhaite que la valeur par défaut prennent en charge des services Bureau à distance, mais plus de contrôle sur les demandes des utilisateurs et droits d’accès.  
  
 Le gestionnaire MSDFMAP. Gestionnaire implémente le **IDataFactoryHandler** interface.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="idatafactoryhandler-interface"></a>String  
 Cette interface comporte deux méthodes, **GetRecordset** et **reconnexion**. Les deux méthodes requièrent que le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété être définie sur **adUseClient**.  
  
 Les deux méthodes acceptent des arguments qui apparaissent après la première virgule dans le «**gestionnaire =**« mot clé. Par exemple, `"Handler=progid,arg1,arg2;"` transmettra une chaîne d’argument `"arg1,arg2"`, et `"Handler=progid"` un argument null.  
  
## <a name="getrecordset-method"></a>Méthode GetRecordset  
 Cette méthode interroge la source de données et crée un nouveau [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) de l’objet à l’aide des arguments fournis. Le **Recordset** doit être ouvert avec **adLockBatchOptimistic** et ne doit pas être ouvert de façon asynchrone.  
  
### <a name="arguments"></a>Arguments  
 ***conn*** la chaîne de connexion.  
  
 ***args*** les arguments pour le gestionnaire.  
  
 ***requête*** le texte de commande pour effectuer une requête.  
  
 ***ppRS*** le pointeur où le **Recordset** doit être retourné.  
  
## <a name="reconnect-method"></a>Méthode ReConnect  
 Cette méthode met à jour la source de données. Il crée un nouveau [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet et attache la donnée **Recordset**.  
  
### <a name="arguments"></a>Arguments  
 ***conn*** la chaîne de connexion.  
  
 ***args*** les arguments pour le gestionnaire.  
  
 ***demandes de tirage*** A **Recordset** objet.  
  
## <a name="msdfhdlidl"></a>msdfhdl.idl  
 Il s’agit de la définition d’interface **IDataFactoryHandler** qui s’affiche dans le **msdfhdl.idl** fichier.  
  
```  
[  
  uuid(D80DE8B3-0001-11d1-91E6-00C04FBBBFB3),  
  version(1.0)  
]  
library MSDFHDL  
{  
    importlib("stdole32.tlb");  
    importlib("stdole2.tlb");  
  
    // TLib : Microsoft ActiveX Data Objects 2.0 Library  
    // {00000200-0000-0010-8000-00AA006D2EA4}  
    #ifdef IMPLIB  
    importlib("implib\\x86\\release\\ado\\msado15.dll");  
    #else  
    importlib("msado20.dll");  
    #endif  
  
    [  
      odl,  
      uuid(D80DE8B5-0001-11d1-91E6-00C04FBBBFB3),  
      version(1.0)  
    ]  
    interface IDataFactoryHandler : IUnknown  
    {  
HRESULT _stdcall GetRecordset(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] BSTR query,  
      [out, retval] _Recordset **ppRS);  
  
// DataFactory will use the ActiveConnection property  
// on the Recordset after calling Reconnect.  
   HRESULT _stdcall Reconnect(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] _Recordset *pRS);  
    };  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de personnalisation, Section Connect](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Fichier de personnalisation, Section de journaux](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Fichier de personnalisation, Section SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Fichier de personnalisation, Section UserList](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Paramètres Client requis](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Présentation du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)


