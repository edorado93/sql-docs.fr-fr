---
title: SQLRowCount | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2610d8691748e316396ccd7babcc0c9e4991aa29
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796927"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Lorsque des tableaux de valeurs de paramètre sont liés pour l'exécution d'une instruction, **SQLRowCount** retourne SQL_ERROR si une ligne de valeurs de paramètre génère une condition d'erreur dans l'exécution d'une instruction. Aucune valeur n'est retournée via l'argument *RowCountPtr* de la fonction.  
  
 L'application peut tirer parti de l'attribut d'instruction SQL_ATTR_PARAMS_PROCESSED_PTR pour capturer le nombre de paramètres traités avant l'erreur.  
  
 En outre, l'application peut utiliser un tableau de valeurs d'état, lié via l'utilisation de l'attribut d'instruction SQL_ATTR_PARAM_STATUS_PTR, pour capturer les décalages des lignes de paramètres incriminées du tableau. L'application peut parcourir le tableau de valeurs d'état pour déterminer le nombre réel de lignes traitées.  
  
 Quand un [!INCLUDE[tsql](../../includes/tsql-md.md)] une instruction INSERT, UPDATE, DELETE ou MERGE avec une clause OUTPUT est exécutée, SQLRowCount ne retourne pas le nombre de lignes affectées tant que toutes les lignes du jeu de résultats généré par la clause OUTPUT ont été consommées. Pour consommer ces lignes, vous devez appeler SQLFetch ou SQLFetchScroll. SQLResultCols retourne -1 tant que toutes les lignes de résultat ont été consommées. SQLFetch ou SQLFetchScroll retourne SQL_NO_DATA, l’application doit appeler SQLRowCount pour déterminer le nombre de lignes affectées avant l’appel de SQLMoreResults pour atteindre le résultat suivant.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLRowCount, fonction](http://go.microsoft.com/fwlink/?LinkId=59367)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
