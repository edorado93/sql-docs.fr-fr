---
title: "Supprimer un pool de ressources | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Resource Governor, suppression de pools de ressources"
  - "pools de ressources [SQL Server], supprimer"
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Supprimer un pool de ressources
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vous pouvez supprimer un pool de ressources à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de Transact-SQL.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions), [Autorisations](#Permissions)  
  
-   **Pour supprimer un pool de ressources, utilisez :** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 Vous ne pouvez pas supprimer un pool de ressources s'il contient des groupes de charge de travail.  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Vous ne pouvez pas supprimer les pools de ressources par défaut ou internes de Resource Governor. Vous ne pouvez pas supprimer un pool de ressources s'il contient des groupes de charge de travail. Pour plus d’informations, consultez [Delete a Workload Group](../../relational-databases/resource-governor/delete-a-workload-group.md).  
  
###  <a name="Permissions"></a> Autorisations  
 La suppression d'un pool de ressources requiert l'autorisation CONTROL SERVER.  
  
##  <a name="DelRPSSMS"></a> Supprimer un pool de ressources à l'aide de l'Explorateur d'objets  
 **Pour supprimer un pool de ressources à l'aide de SQL Server Management Studio**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'Explorateur d'objets et développez de manière récursive le nœud **Gestion** jusqu'à **Resource Governor** inclus.  
  
2.  Cliquez avec le bouton droit sur le pool de ressources à supprimer, puis sélectionnez **Supprimer**.  
  
3.  Dans la fenêtre **Supprimer un objet** , le pool de ressources est répertorié dans la liste **Objet à supprimer** . Pour supprimer le pool de ressources, cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Si le pool de ressources que vous cherchez à supprimer contient un groupe de charge de travail, l'action échoue.  
  
##  <a name="DelRPTSQL"></a> Supprimer un pool de ressources à l'aide de Transact-SQL  
 **Pour supprimer un pool de ressources à l'aide de Transact-SQL**  
  
1.  Exécutez l’instruction **DROP RESOURCE POOL** ou **DROP EXTERNAL RESOURCE POOL** en spécifiant le nom du pool de ressources à supprimer.  
  
2.  Exécutez l'instruction **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### Exemple (Transact-SQL)  
 L'exemple suivant supprime un groupe de charge de travail nommé `poolAdhoc`.  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## Voir aussi  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Pool de ressources de Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Créer un pool de ressources](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Modifier les paramètres de pool de ressources](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [Groupe de charge de travail de Resource Governor](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Fonction classifieur de Resource Governor](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  