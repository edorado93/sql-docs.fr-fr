---
title: sp_revokelogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 57c7ef9242b6c974c8043f8f6ab237b0fbe07941
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706651"
---
# <a name="sprevokelogin-transact-sql"></a>sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime les entrées de connexion à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour un utilisateur de Windows ou d’un groupe créé à l’aide de CREATE LOGIN, **sp_grantlogin**, ou **sp_denylogin**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@loginame=**] **'***connexion***'**  
 Nom de l'utilisateur ou du groupe Windows. *connexion* est **sysname**, sans valeur par défaut. *connexion* peut être n’importe quel nom d’utilisateur Windows existant ou un groupe sous la forme *nom de l’ordinateur*\\*utilisateur ou un domaine*\\*utilisateur*.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_revokelogin** désactive les connexions à l’aide de compte spécifié par le *connexion* paramètre. Cependant, les utilisateurs Windows qui ont l'autorisation d'accéder à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par l'intermédiaire de leur appartenance à un groupe Windows peuvent néanmoins se connecter par le groupe une fois leur accès individuel supprimé. De même, si le *connexion* paramètre spécifie le nom d’un groupe Windows, les membres de ce groupe qui ont été séparément accordé l’accès à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera en mesure de se connecter.  
  
 Par exemple, si les utilisateurs Windows **ADVWORKS\john** est un membre du groupe Windows **ADVWORKS\Admins**, et **sp_revokelogin** révoque l’accès de `ADVWORKS\john`:  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 Utilisateur **ADVWORKS\john** peut toujours se connecter si **ADVWORKS\Admins** a été accordé l’accès à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. De même, si le groupe de Windows **ADVWORKS\Admins** est refusé, mais **ADVWORKS\john** a accès, **ADVWORKS\john** peut toujours se connecter.  
  
 Utilisez **sp_denylogin** pour empêcher explicitement les utilisateurs de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], quelle que soit leur appartenance aux groupes de Windows.  
  
 **sp_revokelogin** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER ANY LOGIN sur le serveur.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant supprime les entrées de connexion pour l’utilisateur Windows `Corporate\MollyA`.  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 ou  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
