---
title: Classe SQLServerDataSourceObjectFactory | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 135dad379d0642059af19060b9df27baec0e3e24
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47615188"
---
# <a name="sqlserverdatasourceobjectfactory-class"></a>Classe SQLServerDataSourceObjectFactory
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une fabrique d'objet permettant de matérialiser des sources de données à partir de JNDI (Java Naming and Directory Interface).  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.lang.Object  
  
 **Implémente :** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Notes   
 Cette méthode est héritée par toutes les classes de source de données. Dans le cadre de sa prise en charge de l’interface Referenceable, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] expose cette classe qui implémente un ObjectFactory. Les serveurs d’applications Java appelleront getReference sur une classe de source de données, entraînant ainsi la création d’un objet Reference qui utilise de façon interne le nom de classe en tant que fabrique de classe.  
  
 Lorsque le serveur d’applications Java doit déréférencer l’objet de référence, il crée une instance de l’objet de SQLServerDataSourceObjectFactory et appelle le [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md) méthode, en passant à l’objet de référence récupérer l’instance de source de données.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSourceObjectFactory, membres](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
