---
title: Octroi de privilèges d’invité sur un serveur Web | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f0ebb888b223cab81d01817ec4c10f96813d3f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678477"
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Octroi de privilèges d’invité à un serveur web
Le compte de serveur Web anonyme (IUSR_*ComputerName*) doit être ajouté au groupe local invités sur l’ordinateur serveur Web à l’utilisation de RDS.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Pour accorder des privilèges d’invité sur un serveur Web  
  
1.  Sur votre ordinateur Microsoft Windows 2000 Server, cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **outils d’administration**, puis cliquez sur **ordinateur Gestion**.  
  
2.  Dans l’arborescence de la console, dans **utilisateurs et groupes locaux**, cliquez sur **groupes**.  
  
3.  Sélectionnez le **invités** groupe local. À partir de la **Action** menu, choisissez **propriétés**.  
  
4.  Dans le **invités propriétés** boîte de dialogue, cliquez sur **ajouter**.  
  
5.  Si le compte anonyme du serveur Web n’apparaît pas dans la liste dans le **sélectionner des utilisateurs ou groupes** boîte de dialogue, tapez son nom (IUSR_*ComputerName*) dans la zone vierge en bas, puis cliquez sur **ajouter** .  
  
6.  Cliquez sur **OK**.


