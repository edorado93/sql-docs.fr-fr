---
title: srv_rpcowner (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- srv_rpcowner
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 64ee7f8ad02c141a35cb3bc1cd2f5a599a229f4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696287"
---
# <a name="srvrpcowner-extended-stored-procedure-api"></a>srv_rpcowner (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Retourne le composant propriétaire de la procédure stockée distante actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu la procédure stockée distante). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *len*  
 Pointeur vers une variable de type entier qui reçoit la longueur du nom du propriétaire. Le paramètre *len* peut être NULL ; dans ce cas, la longueur du composant propriétaire n’est pas retournée.  
  
## <a name="returns"></a>Valeur renvoyée  
 Un pointeur DBCHAR vers le composant propriétaire, terminé par le caractère NULL, de la procédure stockée distante actuelle. En l’absence de procédure stockée distante actuelle, NULL est retourné et *len* est défini sur -1.  
  
## <a name="remarks"></a>Notes   
 Cette fonction retourne uniquement le composant propriétaire de la procédure stockée distante. Elle n'inclut pas les spécificateurs facultatifs pour le nom, le nom de la procédure stockée distante et le numéro de la procédure stockée distante.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
