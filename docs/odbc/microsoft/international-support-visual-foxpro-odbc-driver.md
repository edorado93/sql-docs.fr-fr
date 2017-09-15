---
title: Prise en charge internationale (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 322246bbb6634386955c8655c2e20e3cfe5b6fed
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Prise en charge internationale (le pilote ODBC Visual FoxPro)
Le pilote ODBC Microsoft Visual FoxPro prend en charge :  
  
-   Les jeux de caractères de codés sur deux octets (DBCS)  
  
-   Plusieurs séquences de classement  
  
 Une séquence de classement définit le *l’ordre de tri* pour les données stockées dans une table Visual FoxPro ou d’une base de données. Par défaut, le pilote est configuré pour utiliser les séquences de classement qui prennent en charge la version linguistique de votre système d’exploitation.  
  
 Pour obtenir la liste des séquences de classement pris en charge, consultez [définir COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>paramètres régionaux  
 Le jeu d’informations qui correspond à une langue donnée et le pays/région. Paramètres régionaux indique des paramètres spécifiques comme séparateurs décimaux, date et formats d’heure et l’ordre de tri des caractères.  
  
## <a name="sort-order"></a>ordre de tri  
 Ordres de tri intègrent les règles de tri de différentes *paramètres régionaux*s, ce qui vous permet de trier correctement les données dans ces langues. Dans Visual FoxPro, l’ordre de tri actuelle détermine les résultats des comparaisons d’expression de caractères et l’ordre dans lequel les enregistrements apparaissent dans indexée ou du tri des tables.