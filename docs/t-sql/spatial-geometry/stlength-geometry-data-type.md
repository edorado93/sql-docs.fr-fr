---
title: STLength (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STLength_TSQL
- STLength (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STLength (geometry Data Type)
ms.assetid: e34dc620-2a65-4248-b099-fff91830ab98
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 309b74e21d131b47e94f4890ace0072f0b85e64e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678118"
---
# <a name="stlength-geometry-data-type"></a>STLength (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne la longueur totale des éléments d’une instance **geometry**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes   
 Si une instance **geometry** est fermée, sa longueur est calculée en tant que longueur totale autour de l’instance ; la longueur d’un polygone correspond à son périmètre et la longueur d’un point est 0. La longueur d’un type **geometrycollection** correspond à la somme des longueurs des instances **geometry** qu’il contient.  
  
 STLength () fonctionne sur LineStrings valide et non valide. Généralement, un LineString n'est pas valide à cause du chevauchement des segments, qui peut être provoqué par des anomalies telles que des traces de longitude GPS inexactes. STLength () ne supprime pas les segments chevauchés ou non valides. Il les inclut dans la valeur de longueur retournée. La méthode MakeValid () peut supprimer les segments chevauchés d'un LineString.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `LineString` et utilise `STLength()` pour déterminer la longueur de l'instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

