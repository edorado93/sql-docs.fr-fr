---
title: XML et les Types de données en bloc le comportement de chargement (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d8271deeb51f3225b227b21ad4c6f24c99cff660
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624527"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Types de données et comportement du chargement en masse XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les types de données qui sont spécifiés dans le schéma de mappage (type XSD ou XDR et **SQL : DataType**) sont généralement ignorées, sauf dans les cas suivants :  
  
 Dans XSD :  
  
-   Si le type est **dateTime** ou **temps**, vous devez spécifier le **SQL : DataType** car le chargement en masse XML effectue une conversion de données avant de les envoyer à Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Lorsque vous effectuez un chargement en bloc dans une colonne de **uniqueidentifier** tapez [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et la valeur XSD est un GUID qui inclut des accolades ({et}), vous devez spécifier **SQL : DataType = « uniqueidentifier »** à Supprimez les accolades avant que la valeur est insérée dans la colonne. Si **SQL : DataType** n’est pas spécifié, la valeur est envoyée avec les accolades et l’insertion échoue.  
  
 Pour plus d’informations sur **SQL : DataType**, consultez [forçages de Type de données et de l’Annotation SQL : DataType &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 Dans XDR :  
  
-   Si le **dt : type** est **datetime**, **temps**, **dateTime.tz**, ou **time.tz**, vous devez spécifier à la fois le **dt : type** et **SQL : DataType** car le chargement en masse XML effectue une conversion de données avant d’envoyer les données à des types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Si vos données XML sont de type **uuid**, **SQL : DataType** doit être spécifié ; **dt : type = « uuid »** est également requis, sauf si les données sont des données de type chaîne. Si vous ne spécifiez pas **dt:uuid**, chargement en masse XML accepte les chaînes avec accolades (et les supprime si nécessaire).  
  
-   Si les données XML sont **bin.base64** ou **bin.hex**, vous devez spécifier le type de données XML avec **dt : type**. Le chargement en masse XML charge ensuite les données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sous la forme d'une représentation hexadécimale des données.  
  
  
