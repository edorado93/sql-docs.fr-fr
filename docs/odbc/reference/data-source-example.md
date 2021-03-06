---
title: Exemple de Source de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69cc3a0d32c12c71b3909bda23dea93417475f2a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847627"
---
# <a name="data-source-example"></a>Exemple de source de données
Sur les ordinateurs exécutant Microsoft® Windows NT® Server/Windows 2000 Server, Microsoft Windows NT Workstation/Windows 2000 Professionnel ou Microsoft Windows® 95/98, données de l’ordinateur, les informations de la source sont stockées dans le Registre. En fonction de quel Registre clés que les informations sont stockées sous, la source de données est appelée un *source de données utilisateur* ou un *source de données système*. Sources de données utilisateur sont stockés sous la clé HKEY_CURRENT_USER et sont disponibles uniquement pour l’utilisateur actuel. Sources de données système sont stockés sous la clé HKEY_LOCAL_MACHINE et peuvent être utilisées par plusieurs utilisateurs sur un même ordinateur. Elles peuvent également servir par les services du système, qui peuvent alors accéder à la source de données même si aucun utilisateur n’est connecté à l’ordinateur. Pour plus d’informations sur l’utilisateur et les sources de données système, consultez [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md).  
  
 Supposons qu’un utilisateur a trois sources de données utilisateur : le Personnel et l’inventaire, qui utilisent un SGBD Oracle ; et de la paie, qui utilise un SGBD Microsoft SQL Server. Les valeurs de Registre pour les sources de données peuvent être :  
  
```  
HKEY_CURRENT_USER  
SOFTWARE  
          ODBC  
               Odbc.ini  
                    ODBC Data Sources  
                    Personnel : REG_SZ : Oracle  
                    Inventory : REG_SZ : Oracle  
                    Payroll : REG_SZ : SQL Server  
```  
  
 et les valeurs de Registre pour la source de données de paie peuvent être :  
  
```  
HKEY_CURRENT_USER  
     SOFTWARE  
          ODBC  
               Odbc.ini  
                    Payroll  
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll  
                         Description : REG_SZ : Payroll database  
                         Server : REG_SZ : PYRLL1  
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```
