---
title: sp_changearticlecolumndatatype (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d9f24f814b7ca4b160c51783f7923274fa33614e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47734937"
---
# <a name="spchangearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie le mappage du type de données de colonne d'article pour une publication Oracle. Cette procédure stockée est exécutée sur le serveur de distribution sur une base de données.  
  
> [!NOTE]  
>  Les mappages de type de données entre les types de serveur de publication pris en charge sont fournis par défaut. Utilisez **sp_changearticlecolumndatatype** uniquement lorsque vous remplacez ces paramètres par défaut.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changearticlecolumndatatype [ @publication= ] 'publication'  
    [ @article = ] 'article'   
    [ @column = ] 'column'  
    [ , [ @type = ] 'type' ]  
    [ , [ @length = ] length ]  
    [ , [ @precision = ] precision ]  
    [ , [ @scale = ] scale ]  
    [ , [ @publisher = ] 'publisher'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=** ] **'***publication***'**  
 Nom de la publication Oracle. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@article =** ] **'***article***'**  
 Nom de l'article. *article* est **sysname**, sans valeur par défaut.  
  
 [ **@column**=] **'***colonne***'**  
 Nom de la colonne pour laquelle il faut modifier le mappage du type de données. *colonne* est **sysname**, sans valeur par défaut.  
  
 [ **@type** =] **'***type***'**  
 Est le nom de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données dans la colonne de destination. *type* est **sysname**, avec NULL comme valeur par défaut.  
  
 [ **@length** =] *longueur*  
 Nom du type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la colonne de destination. *longueur* est **bigint**, avec NULL comme valeur par défaut.  
  
 [ **@precision**=] *précision*  
 Précision du type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la colonne de destination. *précision* est **bigint**, avec NULL comme valeur par défaut.  
  
 [ **@publisher**=] **'***publisher***'**  
 Spécifie un non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **Sp_changearticlecolumndatatype** est utilisée pour remplacer les mappages de type de données par défaut entre les types de serveur de publication pris en charge (Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Pour afficher ces mappages de type de données par défaut, exécutez [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 **sp_changearticlecolumndatatype** est uniquement pris en charge pour les serveurs de publication Oracle. L'exécution de cette procédure stockée sur une publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entraîne une erreur.  
  
 **sp_changearticlecolumndatatype** doit être exécutée pour chaque mappage de colonne d’article qui doit être modifié.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_changearticlecolumndatatype**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier les propriétés des publications et des articles](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
