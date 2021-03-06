---
title: sp_remove_job_from_targets (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_remove_job_from_targets_TSQL
- sp_remove_job_from_targets
dev_langs:
- TSQL
helpviewer_keywords:
- sp_remove_job_from_targets
ms.assetid: b8171fb1-c11d-4244-8618-a12e28a150ce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5223c0d48d1baacdd8660a4fcc006d13115f1f4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732217"
---
# <a name="spremovejobfromtargets-transact-sql"></a>sp_remove_job_from_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime le travail spécifié des serveurs cibles ou des groupes de serveurs cibles donnés.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_remove_job_from_targets [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name'   
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_id =**] *job_id*  
 Numéro d'identification de tâche du travail à partir duquel doivent être supprimés les serveurs cibles ou les groupes de serveurs cibles spécifiés. Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
 [  **@job_name =**] **'***nom_travail***'**  
 Nom du travail à partir duquel doivent être supprimés les serveurs cibles ou les groupes de serveurs cibles spécifiés. Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
 [ **@target_server_groups =**] **'***target_server_groups***'**  
 Liste séparée par des virgules de groupes de serveurs cibles à supprimer du travail spécifié. *groupes_serveurs_cibles* est **nvarchar (1024)**, avec NULL comme valeur par défaut.  
  
 [  **@target_servers =**] **'***serveurs_cibles***'**  
 Liste séparée par des virgules de serveurs cibles à supprimer du travail spécifié. *serveurs_cibles* est **nvarchar (1024)**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="permissions"></a>Permissions  
 Les autorisations d'exécution de cette procédure sont accordées par défaut aux membres du rôle de serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 Dans cet exemple, le travail `Weekly Sales Backups`, créé au préalable, est supprimé du groupe de serveurs cibles `Servers Processing Customer Orders` et des serveurs `SEATTLE1` et `SEATTLE2`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_remove_job_from_targets  
    @job_name = N'Weekly Sales Backups',  
    @target_server_groups = N'Servers Processing Customer Orders',   
    @target_servers = N'SEATTLE2,SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_apply_job_to_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
