---
title: Utilisation de la clause OUTPUT avec OLE DB dans le pilote OLE DB pour SQL Server | Microsoft Docs
description: Utilisation de la clause OUTPUT avec OLE DB dans le pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: bec0f04cfc575fb48996bbe028f66f8880cd58d8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825797"
---
# <a name="using-the-output-clause-with-ole-db-in-ole-db-driver-for-sql-server"></a>Utilisation de la clause OUTPUT avec OLE DB dans le pilote OLE DB pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Si vous utilisez une clause OUTPUT dans une commande INSERT, UPDATE, DELETE ou MERGE, le nombre de lignes affectées n’est pas disponible. L’application doit compter le nombre de lignes de l’ensemble de lignes retourné par la clause OUTPUT.  
  
## <a name="see-also"></a> Voir aussi  
 [Création d’une application OLE DB Driver pour SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md) 
  
  
