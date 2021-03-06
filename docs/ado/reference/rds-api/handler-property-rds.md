---
title: Gestionnaire, propriété (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Handler property [ADO]
ms.assetid: fdc34362-6d47-4727-b171-8d033159408e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 038cb740cd2d8e2457f83f829c85f4d6598b9f97
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47824077"
---
# <a name="handler-property-rds"></a>Handler, propriété (RDS)
Indique le nom d’un programme de personnalisation côté serveur (gestionnaire) qui étend les fonctionnalités de la [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)et tous les paramètres utilisés par le *gestionnaire*.  
  
 **S’applique à :** [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 *Chaîne*  
 Un **chaîne** valeur qui contient le nom du gestionnaire et tous les paramètres, tous séparés par des virgules (par exemple, `"handlerName,parm1,parm2,...,parm` *N*`"`).  
  
## <a name="remarks"></a>Notes  
 Cette propriété prend en charge [personnalisation](../../../ado/guide/remote-data-service/datafactory-customization.md), une fonctionnalité qui requiert la définition du [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété **adUseClient**.  
  
 Le nom du gestionnaire et ses paramètres, le cas échéant, sont séparés par des virgules («, »). Un comportement imprévisible est générée si un point-virgule (« ; ») apparaît quelque part dans *chaîne*. Vous pouvez écrire votre propre gestionnaire, sous réserve qu’il prend en charge la **IDataFactoryHandler** interface.  
  
 Le nom du gestionnaire par défaut est **MSDFMAP. Gestionnaire**, et son paramètre par défaut est un fichier de personnalisation nommé **MSDFMAP. INI**. Cette propriété permet d’appeler d’autres fichiers de personnalisation créés par votre administrateur de serveur.  
  
 L’alternative au paramètre la **gestionnaire** propriété consiste à spécifier un gestionnaire et des paramètres dans le [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propriété ; autrement dit, « **Gestionnaire = *** handlerName, parameter1, parameter2,... ;* ".  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Handler, exemple de propriété (VB)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


