---
title: Instantanés des publications de fusion avec des filtres paramétrés | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], snapshots
- snapshots [SQL Server replication], parameterized filters and
- filters [SQL Server replication], parameterized
- merge replication [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 99d7ae15-5457-4ad4-886b-19c17371f72c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 621966b18de4f7b1d8e48c755b9c52edfa5afe77
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052039"
---
# <a name="snapshots-for-merge-publications-with-parameterized-filters"></a>Instantanés des publications de fusion avec des filtres paramétrés
  Lorsque vous utilisez des filtres de lignes paramétrés dans les publications de fusion, la réplication initialise chaque abonnement avec un instantané en deux parties. Un instantané est d'abord créée. Il contient tous les objets nécessaires à la publication ainsi que le schéma des objets publiés mais pas les données. Ensuite, chaque abonnement est initialisé avec un instantané qui comprend les objets et le schéma provenant de l'instantané du schéma ainsi que les données appartenant à la partition de l'abonnement. Si plusieurs abonnements reçoivent une partition donnée (en d'autres termes, s'ils reçoivent les mêmes schéma et données), l'instantané de cette partition n'est créé qu'une seule fois ; plusieurs abonnements sont initialisés à l'aide du même instantané. Pour plus d'informations sur les filtres de lignes paramétrés, consultez [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
 Pour créer des instantanés de publication avec des filtres paramétrés, trois méthodes sont possibles :  
  
-   Vous pouvez prégénérer des instantanés pour chaque partition. Cette option vous permet de contrôler le moment où les instantanés sont générés.  
  
     Vous pouvez également choisir d'actualiser les instantanés selon une planification définie. Les nouveaux Abonnés à une partition dont vous avez créé un instantané reçoivent un instantané à jour.  
  
-   Vous pouvez autoriser les Abonnés à demander la génération et l'application d'un instantané lors de leur première synchronisation. Cette option permet aux nouveaux Abonnés de se synchroniser sans intervention d'un administrateur (l'Agent[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en cours d'exécution sur le serveur de publication pour que l'instantané puisse être généré).  
  
    > [!NOTE]  
    >  Si le filtrage d'un ou plusieurs articles de la publication donne des partitions qui ne se chevauchent pas et sont uniques pour chaque abonnement, les métadonnées sont nettoyées à chaque exécution de l'Agent de fusion. Cela signifie que l'instantané partitionné expire plus rapidement. Lorsque vous optez pour cette méthode, envisagez d'autoriser les Abonnées à initialiser la génération et la remise d'instantané. Pour plus d'informations sur les options de filtrage, consultez [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
-   Vous pouvez générer manuellement un instantané pour chaque Abonné avec l'Agent d'instantané. L'Abonné doit alors fournir l'emplacement de l'instantané à l'Agent de fusion afin qu'il puisse extraire et appliquer l'instantané approprié.  
  
    > [!NOTE]  
    >  Cette option est prise en charge pour assurer la compatibilité descendante et n'autorise pas les partages d'instantanés FTP.  
  
 L'approche la plus souple est celle qui consiste à combiner les options d'instantané prégénéré et d'instantané demandé par l'Abonné : les instantanés sont prégénérés et actualisés à intervalles planifiés (généralement pendant les heures creuses), mais un Abonné peut générer son propre instantané en cas de création d'un abonnement nécessitant une nouvelle partition.  
  
 Prenons l'exemple de [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], qui possède une force de vente nomade chargée d'approvisionner en stock différents magasins. Chaque commercial reçoit un abonnement basé sur son nom de connexion, lequel extrait les données relatives aux magasins dont le commercial est responsable. L'administrateur choisit de prégénérer des instantanés et de les actualiser tous les dimanches. De temps à autre, un nouvel utilisateur est ajouté au système et a besoin de données pour une partition dont il n'existe aucun instantané disponible. L'administrateur décide par ailleurs d'autoriser les instantanés initialisés par l'Abonné pour éviter que ce dernier se retrouve dans une situation où il est incapable de s'abonner à la publication car aucun instantané n'est disponible. Lorsque le nouvel Abonné se connecte pour la première fois, l'instantané est généré pour la partition spécifiée et appliqué à l'Abonné (l'Agent[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en cours d'exécution sur le serveur de publication pour que l'instantané puisse être généré).  
  
 Pour créer un instantané d'une publication avec des filtres paramétrés, consultez [Créer un instantané d'une publication de fusion avec des filtres paramétrés](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## <a name="security-settings-for-the-snapshot-agent"></a>Paramètres de sécurité de l'Agent d'instantané  
 L'Agent d'instantané crée des instantanés de chaque partition. Pour les instantanés prégénérés et ceux demandés par un Abonné, l'Agent s'exécute et se connecte avec les informations d'identification spécifiées au moment de la création du travail de l'Agent d'instantané pour la publication (ce travail est créé par l'Assistant Nouvelle publication ou par **sp_addpublication_snapshot**). Pour modifier les informations d'identification, utilisez **sp_changedynamicsnapshot_job**. Pour plus d’informations, consultez [sp_changedynamicsnapshot_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changedynamicsnapshot-job-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md)   
 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)   
 [Sécuriser le dossier d’instantanés](security/secure-the-snapshot-folder.md)  
  
  
