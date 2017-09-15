---
title: USER_ID (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USER_ID
- USER_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- USER_ID function
- identification numbers [SQL Server]
- IDs [SQL Server], databases
- users [SQL Server], database ID numbers
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
ms.assetid: 67fd29bc-eda9-4d4d-b148-5d3659181a43
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a40853c10e17969c78ef88e4b75995e77b8a1bac
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="userid-transact-sql"></a>USER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le numéro d'identification d'un utilisateur de la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez [DATABASE_PRINCIPAL_ID](../../t-sql/functions/database-principal-id-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
USER_ID ( [ 'user' ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *utilisateur*  
 Nom d'utilisateur à utiliser. *utilisateur* est **nchar**. Si un **char** valeur est spécifiée, il est converti implicitement en **nchar**. Les parenthèses sont obligatoires.  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 Lorsque *utilisateur* est omis, l’utilisateur actuel est supposé. Si le paramètre contient le mot NULL, retourne NULL. Lorsque USER_ID est appelé après EXECUTE AS, USER_ID retourne l'ID du contexte représenté.  
  
 Lorsqu'un principal Windows qui n'est pas mappé à un utilisateur spécifique accède à une base de données parce qu'il appartient à un groupe, USER_ID retourne 0 (l'identificateur de public). Si un tel principal crée un objet sans spécifier de schéma, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créera un utilisateur implicite et un schéma mappés au principal Windows. L'utilisateur ainsi créé ne peut pas être utilisé pour une connexion à la base de données. Les appels à USER_ID effectués par un principal Windows mappé à un utilisateur implicite retourneront l'identificateur de cet utilisateur implicite.  
  
 USER_ID peut être utilisé dans une liste de sélection, dans une clause WHERE, et partout où une expression est autorisée. Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la valeur retournée est le numéro d'identification de l'utilisateur `AdventureWorks2012` de `Harold`.  
  
```  
USE AdventureWorks2012;  
SELECT USER_ID('Harold');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [User_name &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [DATABASE_PRINCIPAL_ID &#40; Transact-SQL &#41;](../../t-sql/functions/database-principal-id-transact-sql.md)   
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  