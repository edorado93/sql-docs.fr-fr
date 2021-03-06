---
title: Des commandes avec des commandes COMPUTE intermédiaires paramétrables | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
- APPEND clause [ADO]
- COMPUTE command [ADO]
ms.assetid: 732f624f-8900-4608-9815-194302d22e8b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1675e80522feb0c0b2a46a89dfa6e3bba182198
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851639"
---
# <a name="parameterized-commands-with-intervening-compute-commands"></a>Commandes paramétrées avec des commandes COMPUTE intermédiaires
Une forme paramétrée commande APPEND contient généralement une clause qui crée un parent **Recordset** avec une commande de requête et une autre clause qui crée un enfant **Recordset** avec une commande de requête paramétrable : Autrement dit, une commande contenant un espace réservé de paramètre (un point d’interrogation « ? »). La forme résultant **Recordset** a deux niveaux, dans laquelle le parent occupé par le niveau supérieur et le niveau inférieur occupé par l’enfant.  
  
 La clause qui crée l’enfant **Recordset** peut maintenant être un nombre arbitraire de forme imbriquées commandes COMPUTE, la commande la plus profondément imbriquée contenant la requête paramétrable. La forme résultant **Recordset** a plusieurs niveaux, dans laquelle le parent occupé par le niveau le plus, l’enfant occupe le niveau de la plus basse et un nombre arbitraire de **Recordset**s générés par le commandes de mise en forme occupent les niveaux intermédiaires.  
  
 L’utilisation classique pour cette fonctionnalité consiste à appeler la fonction d’agrégation et les fonctionnalités de regroupement de shapeCOMPUTE commandes pour créer des intervenants **Recordset** objets avec des informations analytiques sur l’enfant **Recordset** . En outre, comme il s’agit d’une commande de mise en forme paramétrée, chaque fois qu’une colonne de chapitre du parent est accessible, un nouvel enfant **Recordset** peuvent être récupérés. Étant donné que les niveaux intermédiaires sont dérivés de l’enfant, ils également recalculés.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)
