---
title: Espace TempDB suffisant | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- TempDB space in RDS [ADO]
ms.assetid: 09130db1-6248-4234-a1e5-a9c8e1622c06
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc4fd9d29c7623b3c814f0e45904e55463defe0c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666577"
---
# <a name="ensuring-sufficient-tempdb-space"></a>Configuration d’un espace TempDB suffisant
Si des erreurs surviennent lors de la gestion des [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objets nécessitant un espace de traitement dans Microsoft SQL Server 6.5, vous devrez peut-être augmenter la taille de TempDB. (Certaines requêtes nécessitent un espace de traitement temporaire ; par exemple, une requête avec une clause ORDER BY exige le tri de la **Recordset**, ce qui nécessite peu d’espace temporaire.)  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
> [!IMPORTANT]
>  Lisez cette procédure avant d’effectuer les actions, car il n’est pas aussi simple de réduire un appareil une fois qu’il est développé.  
  
> [!NOTE]
>  Par défaut inMicrosoft SQL Server 7.0 et versions ultérieur, TempDB est définie à croître automatiquement en fonction des besoins. Par conséquent, cette procédure peut uniquement être nécessaire sur les serveurs exécutant des versions antérieures à la version 7.0.  
  
### <a name="to-increase-the-tempdb-space-on-sql-server-65"></a>Pour augmenter l’espace de TempDB sur SQL Server 6.5  
  
1.  Démarrez Microsoft SQL Server Enterprise Manager, ouvrez l’arborescence pour le serveur, puis ouvrez l’arborescence de la base de données des appareils.  
  
2.  Sélectionnez un appareil (physique) pour développer, telles que Master et double-cliquez sur l’appareil pour ouvrir le **modifier l’unité de base de données** boîte de dialogue.  
  
     Cette boîte de dialogue affiche la quantité d’espace à l’aide de bases de données actuelles.  
  
3.  Dans le **taille** boîte, augmenter l’appareil à la quantité souhaitée (par exemple, 50 mégaoctets (Mo) d’espace disque).  
  
4.  Cliquez sur **modifier maintenant** pour augmenter la quantité d’espace dans lequel la base de données (logique) tempdb.  
  
5.  Ouvrir l’arborescence de bases de données sur le serveur, puis double-cliquez sur **TempDB** pour ouvrir le **modifier la base de données** boîte de dialogue. Le **base de données** onglet répertorie la quantité d’espace actuellement alloué à TempDB (**taille des données**). Par défaut, il s’agit de 2 Mo.  
  
6.  Sous le **taille** de groupe, cliquez sur **Expand**. Les graphiques montrent l’espace disponible et allouée sur chacun des périphériques physiques. Les barres de couleur marron représentent l’espace disponible.  
  
7.  Sélectionnez un **journal appareil**, telles que Master, pour afficher la taille disponible dans le **taille (Mo)** boîte.  
  
8.  Cliquez sur **développer maintenant** à allouer cet espace à la base de données TempDB.  
  
     Le **modifier la base de données** boîte de dialogue affiche la nouvelle taille allouée pour TempDB.  
  
 Pour plus d’informations sur cette rubrique, recherchez le fichier d’aide de Microsoft SQL Server Enterprise Manager pour « Boîte de dialogue de développer la base de données ».  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


