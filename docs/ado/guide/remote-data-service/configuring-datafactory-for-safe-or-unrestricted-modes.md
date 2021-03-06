---
title: Configuration de DataFactory en mode sécurisé ou non restreint | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory configuration in RDS [ADO]
ms.assetid: 8ff24805-dc7a-42ae-b600-5bad0e3f51b8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 664a44b9594b77cec07fa4ce7b80afcc0b651323
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675397"
---
# <a name="configuring-datafactory-for-safe-or-unrestricted-modes"></a>Configuration de DataFactory en mode sans échec ou unrestricted
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Par défaut, ADO est installé avec un « sûre » [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) configuration. Mode sans échec pour les composants serveur RDS signifie que les conditions suivantes sont réunies :  
  
1.  Gestionnaire est nécessaire avec RDSServer.DataFactory (imposé par un paramètre de clé de Registre).  
  
2.  Le gestionnaire par défaut, msdfmap.handler, est inscrit, présent dans la liste de gestionnaires sécurisés et marqués comme étant le gestionnaire par défaut.  
  
3.  Fichier Msdfmap.ini est installé dans le répertoire Windows. Vous devez configurer ce fichier selon vos besoins, avant d’utiliser des services Bureau à distance en mode trois niveaux.  
  
 Si vous le souhaitez, vous pouvez configurer sans restriction **DataFactory** installation. **DataFactory** peut être utilisé directement sans le gestionnaire personnalisé. Les utilisateurs peuvent toujours utiliser un gestionnaire personnalisé en modifiant les chaînes de connexion, mais il n’est pas obligatoire. Pour plus d’informations sur les conséquences de l’utilisation de la **RDSServer.DataFactory** d’objets, consultez [sécurisation des Applications RDS](../../../ado/guide/remote-data-service/securing-rds-applications.md).  
  
 Le handsafe.reg de fichier de Registre a été fourni pour configurer les entrées de Registre de gestionnaire pour une configuration sécurisée. Pour exécuter en mode sans échec, exécutez handsafe.reg.  
  
 Après avoir exécuté handsafe.reg, vous devez arrêter et redémarrer le Service de publication World Wide Web sur le serveur Web en tapant les commandes suivantes dans une fenêtre d’invite de commande : « NET STOP W3SVC » et « NET démarrer W3SVC ».  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



