---
title: Sys.fulltext_semantic_languages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_semantic_languages
- fulltext_semantic_languages_TSQL
- sys.fulltext_semantic_languages
- sys.fulltext_semantic_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_languages catalog view
ms.assetid: b42a85e6-1db9-4a22-8a70-014574c95198
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb609936d7f86728fca53021f96afcbaed412c2e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47604210"
---
# <a name="sysfulltextsemanticlanguages-transact-sql"></a>sys.fulltext_semantic_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque langue dont le modèle statistique est inscrit avec l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsqu'un modèle linguistique est inscrit, cette langue est activée pour l'indexation sémantique.  
  
 Cet affichage catalogue est similaire à [sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
    
||||  
|-|-|-|  
|**Nom de colonne**|**Type**|**Description**|  
|lcid|INT|Identificateur des paramètres régionaux (LCID) Microsoft Windows de la langue.|  
|NAME|sysname|Représente la valeur de l’alias dans [sys.syslanguages &#40;Transact-SQL&#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) correspondant à la valeur de **lcid**, ou la représentation sous forme de chaîne du LCID numérique.|  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Pour plus d’informations, consultez [Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d’informations sur la base de données de statistiques linguistiques de sémantique installée pour prendre en charge l’indexation sémantique, interrogez l’affichage catalogue [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 La visibilité des métadonnées dans les affichages catalogue est limitée aux éléments sécurisables qu'un utilisateur détient ou pour lesquels des autorisations lui ont été accordées.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment interroger **sys.fulltext_semantic_languages** pour obtenir des informations sur tous les modèles linguistiques inscrits pour l’indexation sémantique sur l’instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT * FROM sys.fulltext_semantic_languages;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
