---
title: Propriétés de la base de données de distribution | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distdbproperties.f1
helpviewer_keywords:
- Distribution Database Properties dialog box
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0412108c9b08e8b3345f4930b4076e10c96ec2ce
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207709"
---
# <a name="distribution-database-properties"></a>Propriétés de la base de données de distribution
  La boîte de dialogue **Propriétés de la base de données de distribution** vous permet d'afficher certaines propriétés et de définir la période de rétention de transaction ainsi que la période de rétention d'historique pour la base de données.  
  
## <a name="options"></a>Options  
 **Nom**  
 Nom de la base de données de distribution, dont la valeur par défaut est « distribution » (en lecture seule).  
  
 **Emplacements des fichiers**  
 Emplacement du fichier de base de données et du fichier journal (en lecture seule).  
  
 **Période de rétention des transactions**  
 Également appelée période de rétention de distribution. Durée de stockage des transactions pour une réplication transactionnelle. Pour plus d'informations, voir [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
 **Période de rétention de l'historique**  
 Durée de stockage des métadonnées de l'historique pour tous les types de réplications.  
  
 **Sécurité de l'Agent de lecture de la file d'attente**  
 L'Agent de lecture de la file d'attente est utilisé par la réplication transactionnelle avec les abonnements mis à jour en file d'attente. Un Agent de lecture de la file d'attente est créé automatiquement si vous sélectionnez l'option **Publication transactionnelle avec abonnements pouvant être mis à jour** dans la page **Type de publication** de l'Assistant Nouvelle publication. Cliquez sur **Paramètres de sécurité…** pour modifier le compte sous lequel l'Agent est exécuté et effectue des connexions avec le serveur de distribution.  
  
 Un Agent de lecture de la file d'attente peut également être créé en sélectionnant l'option **Créer un Agent de lecture de la file d'attente** dans cette page (cette option est désactivée si l'Agent a déjà été créé).  
  
 Des informations de connexion supplémentaires pour l'Agent de lecture de la file d'attente sont spécifiées dans deux endroits :  
  
-   L'Agent se connecte au serveur de publication à l'aide des informations d'identification spécifiées dans la boîte de dialogue **Propriétés du serveur de publication** , qui est accessible à partir de la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution** .  
  
-   L'Agent se connecte à l'Abonné à l'aide des informations d'identification spécifiées pour l'Agent de distribution dans l'Assistant Nouvel abonnement.  
  
 Pour plus d’informations, consultez  \\[Replication Agent Security Model](security/replication-agent-security-model.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](configure-distribution.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Créer un abonnement par émission de données](create-a-push-subscription.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)  
  
  
