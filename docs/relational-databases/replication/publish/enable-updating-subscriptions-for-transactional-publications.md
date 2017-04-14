---
title: "Activer les abonnements pouvant &#234;tre mis &#224; jour pour les publications transactionnelles | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transactional replication, updatable subscriptions"
  - "updatable subscriptions, enabling"
  - "abonnements [réplication SQL Server], pouvant être mis à jour"
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Activer les abonnements pouvant &#234;tre mis &#224; jour pour les publications transactionnelles
  Cette rubrique explique comment activer les abonnements de mise à jour pour les publications transactionnelles dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
> **REMARQUE !!** [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  

##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Activez la mise à jour d'abonnements pour les publications transactionnelles dans la page **Type de publication** de l'Assistant Nouvelle publication.  
  
 Pour utiliser les abonnements mis à jour, vous devez aussi configurer des options dans l'Assistant Nouvel abonnement.  
  
#### Pour activer les abonnements mis à jour  
  
1.  Dans la page **Type de publication** de l'Assistant Nouvelle publication, sélectionnez **Publication transactionnelle avec abonnements pouvant être mis à jour**.  
  
2.  Dans la page **Sécurité de l'Agent** , spécifiez des paramètres de sécurité pour l'Agent de lecture de file d'attente, en plus de l'Agent d'instantané et de l'Agent de lecture du journal. Pour plus d'informations sur les autorisations nécessaires pour le compte sour lequel s'exécute l'Agent de lecture de file d'attente, consultez [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    > **Remarque :** l’Agent de lecture de file d’attente est configurée, même si vous utilisez uniquement les abonnements avec mise à jour immédiate.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Lors de la création d'une publication transactionnelle par programme à l'aide de procédures stockées de réplication, vous pouvez activer les abonnements avec mise à jour immédiate ou avec mise à jour en file d'attente.  
  
#### Pour créer une publication qui prend en charge les abonnements avec mise à jour immédiate  
  
1.  Si nécessaire, créez un travail de l'Agent de lecture du journal pour la base de données de publication.  
  
    -   Si un travail de l’Agent de lecture du journal existe déjà pour la base de données de publication, passez à l’étape 2.  
  
    -   Si vous ne savez pas si un travail d’Agent de lecture du journal existe pour une base de données publiée, exécutez [sp_helplogreader_agent &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) sur la base de données de publication de l’éditeur. Si le jeu de résultats est vide, un travail de l'Agent de lecture du journal doit être créé.  
  
    -   Sur le serveur de publication, exécutez [sp_addlogreader_agent &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Spécifiez le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] informations d’identification Windows sous lequel l’agent s’exécute pour **@job_name** et **@password**. Si l’agent doit utiliser l’authentification SQL Server lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informations de connexion pour **@publisher_login** et **@publisher_password**.  
  
2.  Exécutez [sp_addpublication &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), la valeur **true** pour le paramètre **@allow_sync_tran**.  
  
3.  Sur le serveur de publication, exécutez [sp_addpublication_snapshot &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Spécifiez le nom de publication utilisé à l’étape 2 pour **@publication** et les informations d’identification Windows sous lequel l’Agent de capture instantanée s’exécute pour **@job_name** et **@password**. Si l’agent doit utiliser l’authentification SQL Server lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les informations de connexion pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication.  
  
4.  Ajoutez des articles à la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
5.  Au niveau de l'Abonné, créez un abonnement avec mise à jour à cette publication.   
  
#### Pour créer une publication qui prend en charge les abonnements avec mise à jour en file d'attente  
  
1.  Si nécessaire, créez un travail de l'Agent de lecture du journal pour la base de données de publication.  
  
    -   Si un travail de l’Agent de lecture du journal existe déjà pour la base de données de publication, passez à l’étape 2.  
  
    -   Si vous ne savez pas si un travail d’Agent de lecture du journal existe pour une base de données publiée, exécutez [sp_helplogreader_agent &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) sur la base de données de publication de l’éditeur. Si le jeu de résultats est vide, un travail de l'Agent de lecture du journal doit être créé.  
  
    -   Sur le serveur de publication, exécutez [sp_addlogreader_agent &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Spécifiez les informations d’identification Windows sous lequel l’agent s’exécute pour **@job_name** et **@password**. Si l’agent doit utiliser l’authentification SQL Server lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les informations de connexion pour **@publisher_login** et **@publisher_password**.  
  
2.  Si nécessaire, créez un travail de l'Agent de lecture de la file d'attente pour le serveur de distribution.  
  
    -   Si un travail de l'Agent de lecture de la file d'attente existe déjà pour la base de données de distribution, passez à l'étape 3.  
  
    -   Si vous ne savez pas si un travail de l’Agent de lecture de file d’attente existe pour la base de données de distribution, exécutez [sp_helpqreader_agent &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md) sur la base de données de distribution du distributeur. Si le jeu de résultats est vide, un travail de l'Agent de lecture de la file d'attente doit être créé.  
  
    -   Sur le serveur de distribution, exécutez [sp_addqreader_agent &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md). Spécifiez les informations d’identification Windows sous lequel l’agent s’exécute pour **@job_name** et **@password**. Ces informations d'identification sont utilisées lorsque l'Agent de lecture de la file d'attente se connecte au serveur de publication et à l'Abonné. Pour plus d’informations, consultez [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
3.  Exécutez [sp_addpublication &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), la valeur **true** pour le paramètre **@allow_queued_tran** et la valeur **wins de pub**, **sub reinit**, ou **sub wins** pour **@conflict_policy**.  
  
4.  Sur le serveur de publication, exécutez [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Spécifiez le nom de publication utilisé à l’étape 3 pour **@publication** et les informations d’identification Windows sous lequel l’Agent de capture instantanée s’exécute pour **@snapshot_job_name** et **@password**. Si l’agent doit utiliser l’authentification SQL Server lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les informations de connexion pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication.  
  
5.  Ajoutez des articles à la publication. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Au niveau de l'Abonné, créez un abonnement avec mise à jour à cette publication.  
  
#### Pour modifier la stratégie de conflit pour une publication qui autorise les abonnements avec mise à jour en file d'attente  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changepublication &#40 ; Transact-SQL &#41 ;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Spécifiez la valeur **conflict_policy** pour **@property** et le mode de stratégie de conflit souhaité de **wins de pub**, **sub reinit**, ou **sub wins** pour **@value**.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 Cet exemple crée une publication qui prend en charge les abonnements par extraction avec mise à jour immédiate et mise à jour en file d'attente.  
  
 [!code-sql[HowTo#sp_createtranupdatingpub](../../../relational-databases/replication/codesnippet/tsql/enable-updating-subscrip_1.sql)]  
  
## Voir aussi  
 [Définir les Options de résolution de conflit mise à jour en file d’attente &#40 ; SQL Server Management Studio &#41 ;](../../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)   
 [Types de publication pour la réplication transactionnelle](../../../relational-databases/replication/transactional/publication-types-for-transactional-replication.md)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](https://msdn.microsoft.com/library/mt740635.aspx)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Utiliser sqlcmd avec des variables de script](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  