---
title: ICommand (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ICommand [SQL Server Native Client]
ms.assetid: 5e24b3a0-0658-44fc-b653-f4c52f9eb328
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 370e838e61da8fa7f18c3c295f0a42ec4c88b1c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683417"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Cette rubrique présente le comportement OLE DB qui est spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 L'insertion de données dont la taille est supérieure à celle d'une colonne provoque généralement une erreur. Toutefois, il existe des cas où S_OK sera retourné, mais *dwStatus* aura la valeur DBSTATUS_S_TRUNCATED. Cette situation se produit généralement lors de l'insertion de données avec des paramètres, lorsque la colonne n'est pas assez large pour contenir les données et que **ICommandWithParameters::SetParameterInfo** n'a pas été appelé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
