---
title: Position du catalogue | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog position
- catalog position [ODBC]
ms.assetid: 5bc5f64b-c75a-43d2-8745-102ec7a49000
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22a9a9d50891a6101076af6378fb33543274b21b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606227"
---
# <a name="catalog-position"></a>Position du catalogue
La position d’un nom de catalogue dans un identificateur et la façon dont il est séparé du reste de l’identificateur varie à partir de la source de données à la source de données. Par exemple, dans une source de données Xbase, le nom du catalogue est un répertoire et, dans Microsoft® Windows®, est séparé du nom de table (qui est un nom de fichier) par une barre oblique inverse (\\). L’illustration suivante montre cette condition.  
  
 ![Position du catalogue : Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 Dans une source de données SQL Server, le catalogue est une base de données et les noms de schéma et de table est séparé par un point (.).  
  
 ![Position du catalogue : SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 Dans une source de données Oracle, le catalogue est également la base de données, mais suit le nom de table et est séparé à partir des noms de schéma et de table par un arobase (@).  
  
 ![Position du catalogue : Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Pour déterminer le séparateur de catalogue et l’emplacement de son nom, une application appelle **SQLGetInfo** avec les options SQL_CATALOG_NAME_SEPARATOR et SQL_CATALOG_LOCATION. Applications interopérables doivent construire des identificateurs en fonction de ces valeurs.  
  
 Lorsque les identificateurs qui contiennent plusieurs parties, les applications doivent être veiller à ne mettre entre guillemets de chaque partie séparément et pas le caractère qui sépare les identificateurs de devis. Par exemple, l’instruction suivante pour sélectionner toutes les lignes et colonnes d’une table Xbase met entre guillemets le catalogue (\XBASE\SALES\CORP) et les noms de table (Parts.dbf), mais pas le séparateur de catalogue (\\) :  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 L’instruction suivante pour sélectionner toutes les lignes et colonnes d’une table Oracle met entre guillemets le catalogue (ventes), le schéma (entreprise) et les noms de tables (parties), mais pas le catalogue (@) ou des séparateurs de schéma (.) :  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Pour plus d’informations sur les identificateurs, consultez la section suivante, [identificateurs entre guillemets](../../../odbc/reference/develop-app/quoted-identifiers.md).
