---
title: Bit de confiance | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c06f56177d2968955439d88e2ff8f56449d7127e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47609907"
---
# <a name="trustworthy-bit"></a>Bit de confiance
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle détermine si le rôle dbo d'une base de données est affecté au rôle serveur fixe sysadmin et si le bit de confiance de la base de données a la valeur ON.  
  
 Si ces conditions sont réunies, un utilisateur de base de données doté de privilèges peut élever les privilèges au rôle sysadmin. Dans ce rôle, l'utilisateur peut créer et exécuter des assemblys non sécurisés qui compromettent le système.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Désactivez le bit de confiance ou révoquez les autorisations sysadmin du rôle de base de données dbo.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
