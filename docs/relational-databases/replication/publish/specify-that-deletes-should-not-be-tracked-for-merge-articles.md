---
title: Indiquer que les suppressions ne doivent pas être suivies pour les articles de fusion | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d11badc932d1b759dca4ea9675d15a0b9cb7b773
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796421"
---
# <a name="specify-that-deletes-should-not-be-tracked-for-merge-articles"></a>Indiquer que les suppressions ne doivent pas être suivies pour les articles de fusion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Par défaut, la réplication de fusion synchronise les commandes DELETE entre le serveur de publication et l'Abonné. La réplication de fusion vous permet de conserver des lignes qui ont été supprimées de la publication dans la base de données d'abonnement, et vice versa. Vous pouvez spécifier par programme que les commandes DELETE doivent être ignorées lors de la création d'un article ou vous pouvez activer cette fonctionnalité ultérieurement à l'aide de procédures stockées de réplication.  
  
> [!IMPORTANT]  
>  L'activation de cette fonctionnalité conduit à une non-convergence ; autrement dit, les données présentes au niveau de l'Abonné ne reflèteront pas correctement les données présentes au niveau du serveur de publication. Vous devez implémenter votre propre mécanisme de manière à supprimer manuellement les lignes supprimées.  
  
### <a name="to-specify-that-deletes-be-ignored-for-a-new-merge-article"></a>Pour spécifier que les suppressions doivent être ignorées pour un nouvel article de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Affectez la valeur **false** à **@delete_tracking**. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Si la table source d'un article est déjà publiée dans une autre publication, la valeur de **delete_tracking** doit être la même pour les deux articles.  
  
### <a name="to-specify-that-deletes-be-ignored-for-an-existing-merge-article"></a>Pour spécifier que les suppressions doivent être ignorées pour un article de fusion existant  
  
1.  Pour déterminer si la compensation d’erreur est activée pour un article, exécutez [sp_helpmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) et notez la valeur de **delete_tracking** dans le jeu de résultats. Si cette valeur est **0**, les suppressions sont déjà ignorées.  
  
2.  Si la valeur à l’étape 1 est **1**, exécutez [sp_changemergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) sur la base de données de publication au niveau du serveur de publication. Affectez la valeur **delete_tracking** à **@property**et la valeur **false** à **@value**.  
  
    > [!NOTE]  
    >  Si la table source d'un article est déjà publiée dans une autre publication, la valeur de **delete_tracking** doit être la même pour les deux articles.  
  
## <a name="see-also"></a> Voir aussi  
 [Optimiser les performances de la réplication de fusion avec le suivi conditionnel des suppressions](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
