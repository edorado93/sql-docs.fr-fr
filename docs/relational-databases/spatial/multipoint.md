---
title: MultiPoint | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology:
- dbe-spatial
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b093d9c3864bd8ce2f59a01a971295e96b975618
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47781807"
---
# <a name="multipoint"></a>MultiPoint
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Un **MultiPoint** est une collection de zéro ou plusieurs points. La limite d'une instance **MultiPoint** est vide.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `geometry MultiPoint` avec un SRID 23 et deux points : un point avec les coordonnées (2, 3), un point avec les coordonnées (7, 8) et une valeur Z de 9.5.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 Cette instance `MultiPoint` peut également être exprimée à l'aide de `STMPointFromText()` comme illustré ci-dessous.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 L'exemple suivant utilise la méthode `STGeometryN()` pour extraire une description du premier point dans la collection.  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Point](../../relational-databases/spatial/point.md)   
 [Données spatiales &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
