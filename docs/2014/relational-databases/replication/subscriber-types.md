---
title: Types d’abonnés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e40209c05e42b7da8f46b5c1e40b287a79669418
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194019"
---
# <a name="subscriber-types"></a>Types d'Abonnés
  La réplication de fusion vous permet de préciser les types d'Abonnés qu'une publication doit prendre en charge. La sélection des ensembles de types d'Abonnés définit le *niveau de compatibilité de la publication*ce qui détermine les fonctionnalités pouvant être utilisées par la publication.  
  
 Après un instantané de publication, le niveau de compatibilité de la publication peut alors être rehaussé (en d'autres termes, rendue plus restrictif) dans la page **Général** de la boîte de dialogue **Propriétés de la publication** ; le niveau de compatibilité ne peut cependant pas être réduit.  
  
## <a name="options"></a>Options  
 Sélectionnez chaque type d'Abonné que votre publication doit prendre en charge.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 La publication peut utiliser toutes les fonctionnalités.  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 La publication requiert que les fichiers d'instantané soient au format caractère (ceci est géré automatiquement par l'Agent d'instantané). [!INCLUDE[ssEW](../../includes/ssew-md.md)] est également limité par un certain nombre de restrictions indépendantes du niveau de compatibilité.  
  
 Si cette option est sélectionnée, l'option de synchronisation Web est alors activée pour la publication en question. Pour plus d'informations sur la synchronisation Web, consultez [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)   
 [Référence des propriétés &#40;réplication&#41;](properties-reference-replication.md)  
  
  
