---
title: IS_OBJECTSIGNED (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IS_OBJECTSIGNED
- IS_OBJECTSIGNED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IS_OBJECTSIGNED function
ms.assetid: afbc4f7f-8266-4ee6-9802-14a2dbe69ef6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2e1c26b6e934a929fc04316c4640825ab2f1ec46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804587"
---
# <a name="isobjectsigned-transact-sql"></a>IS_OBJECTSIGNED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Indique si un objet est signé par un certificat spécifié ou une clé asymétrique.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IS_OBJECTSIGNED (   
'OBJECT', @object_id, @class, @thumbprint  
  )   
```  
  
## <a name="arguments"></a>Arguments  
 **'OBJECT'**  
 Type de la classe sécurisable.  
  
 *@object_id*  
 ID de l'objet testé. *@object_id* est de type **int**.  
  
 *@class*  
 Classe de l'objet :  
  
-   'certificate'  
  
-   'asymmetric key'  
  
 *@class* est de type **sysname**.  
  
 *@thumbprint*  
 Empreinte numérique SHA de l'objet. *@thumbprint* est de type **varbinary(32)**.  
  
## <a name="returned-types"></a>Types retournés  
 **Int**  
  
## <a name="remarks"></a>Notes   
 IS_OBJECTSIGNED retourne les valeurs suivantes :  
  
|Valeur retournée|Description|  
|------------------|-----------------|  
|NULL|L’objet n’est pas signé ou n’est pas valide.|  
|0|L’objet est signé, mais la signature n’est pas valide.|  
|1|L'objet est signé.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation VIEW DEFINITION sur le certificat ou la clé asymétrique.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. Affichage des propriétés étendues d'une base de données  
 L’exemple suivant teste si la table spt_fallback_db dans la base de données **master** est signée par le certificat de signature de schéma.  
  
```  
USE master;  
-- Declare a variable to hold a thumbprint and an object name  
DECLARE @thumbprint varbinary(20), @objectname sysname;  
  
-- Populate the thumbprint variable with the thumbprint of   
-- the master database schema signing certificate  
SELECT @thumbprint = thumbprint   
FROM sys.certificates   
WHERE name LIKE '%SchemaSigningCertificate%';  
  
-- Populate the object name variable with a table name in master  
SELECT @objectname = 'spt_fallback_db';  
  
-- Query to see if the table is signed by the thumbprint  
SELECT @objectname AS [object name],  
IS_OBJECTSIGNED(  
'OBJECT', OBJECT_ID(@objectname), 'certificate', @thumbprint  
) AS [Is the object signed?] ;  
```  
  
## <a name="see-also"></a> Voir aussi  
 [sys.fn_check_object_signatures &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-check-object-signatures-transact-sql.md)  
  
  
