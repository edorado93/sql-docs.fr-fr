---
title: Sqlcleanupconnectionpoolid, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1dc2552c848b691346c57a0191f9c9200bad4523
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666167"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>SQLCleanupConnectionPoolID, fonction
**Conformité**  
 Version introduite : ODBC normes 3,81 conformité : ODBC  
  
 **Résumé**  
 **SQLCleanupConnectionPoolID** informe un pilote qui a un ID de pool a été dépassé. Un pool d’ID peut le délai d’attente chaque fois que toutes les connexions dans un pool associé à cet ID de pool ont été a expiré. Consultez [le regroupement dans le Microsoft Data Access Components](http://msdn.microsoft.com/library/ms810829.aspx) pour plus d’informations sur le délai de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Arguments  
 *EnvironmentHandle*  
 [Entrée] Le handle d’environnement du pool.  
  
 *PoolID*  
 [Entrée] Le pool associé à l’ID du pool qui a été dépassé.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Le Gestionnaire de pilotes ne traitera pas retournées à partir des informations de diagnostic **SQLCleanupConnectionPoolID**.  
  
 Une application ne peut pas recevoir le message d’erreur retourné par le pilote.  
  
## <a name="remarks"></a>Notes  
 **SQLCleanupConnectionPoolID** peut être appelée à tout moment, mais le Gestionnaire de pilotes garantit qu’aucun autre thread n’appelle simultanément **SQLGetPoolID** et aucun autre thread n’appelle simultanément  **SQLRateConnection** et **SQLPoolConnect** avec un jeton d’informations de connexion affecté à cet ID de pool. Par conséquent, le pilote doit Assurez-vous que cette fonction est thread-safe.  
  
 Un pilote peut nettoyer les ressources associées à l’ID de pool.  
  
 Applications ne doivent pas appeler cette fonction directement. Un pilote ODBC qui prend en charge le regroupement de connexions prenant en charge les pilotes doive implémenter cette fonction.  
  
 Inclure sqlspi.h pour le développement de pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Le regroupement de connexions prenant en charge de pilote](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
