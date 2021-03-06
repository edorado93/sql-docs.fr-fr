---
title: sp_enum_login_for_proxy (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_login_for_proxy_TSQL
- sp_enum_login_for_proxy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_login_for_proxy
ms.assetid: 62a75019-248a-44c8-a5cc-c79f55ea3acf
ms.author: vanto
manager: craigg
ms.openlocfilehash: 9250f4c7da207561c935d7aa1c72ac4df7104526
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799434"
---
# <a name="spenumloginforproxy-transact-sql"></a>sp_enum_login_for_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie des associations entre les principaux de sécurité et les proxys.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_enum_login_for_proxy  
    [ @name = ] 'name'  
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@name**=] '*nom*'  
 Le nom d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entité de sécurité, login, rôle de serveur, ou **msdb** rôle de base de données pour énumérer les serveurs proxy. Le nom est **nvarchar (256)**, avec NULL comme valeur par défaut.  
  
 [ **@proxy_id**=] *id*  
 Numéro d'identification du serveur proxy pour lequel énumérer les informations. Le *proxy_id* est **int**, avec NULL comme valeur par défaut. Soit le *id* ou *proxy_name* peut être spécifié.  
  
 [ **@proxy_name**=] **'***proxy_name***'**  
 Nom du serveur proxy pour lequel énumérer les informations. Le *proxy_name* est **sysname**, avec NULL comme valeur par défaut. Soit le *id* ou *proxy_name* peut être spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**Int**|Numéro d'identification du proxy.|  
|**proxy_name**|**sysname**|Nom du proxy.|  
|**nom**|**sysname**|Nom du principal de sécurité pour l'association.|  
|**flags**|**Int**|Type du principal de sécurité.<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion<br /><br /> **1** = rôle de système fixe<br /><br /> **2** = rôle de base de données dans **msdb**|  
  
## <a name="remarks"></a>Notes  
 Lorsque aucun paramètre n’est fourni, **sp_enum_login_for_proxy** répertorie des informations sur toutes les connexions dans l’instance pour chaque serveur proxy.  
  
 Lorsqu’un id ou un nom de proxy est fourni, **sp_enum_login_for_proxy** répertorie les connexions qui ont accès au proxy. Lorsqu’un nom de connexion est fourni, **sp_enum_login_for_proxy** les proxys auxquels la connexion peut accéder à des listes.  
  
 Lorsque des informations de proxy et un nom de connexion sont fournis, le jeu de résultats renvoie une ligne si la connexion spécifiée dispose d'un accès au proxy spécifié.  
  
 Cette procédure stockée se trouve dans **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Autorisations d’exécution pour cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-listing-all-associations"></a>A. Création de la liste de toutes les associations  
 L'exemple suivant répertorie toutes les autorisations établies entre des connexions et des proxys dans l'instance en cours.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy ;  
GO  
```  
  
### <a name="b-listing-proxies-for-a-specific-login"></a>B. Création de la liste des proxys pour une connexion spécifique  
 L'exemple suivant répertorie les proxys auxquels la connexion `terrid` peut accéder.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy  
    @name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_help_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
