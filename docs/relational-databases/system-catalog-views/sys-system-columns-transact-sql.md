---
title: Sys.system_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- system_columns_TSQL
- system_columns
- sys.system_columns
- sys.system_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_columns catalog view
ms.assetid: 4ab1d48a-d57a-4e76-a08c-9627eeaf4588
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2bc916f827fb190142dd07b56485b8a9d6005d94
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775257"
---
# <a name="syssystemcolumns-transact-sql"></a>sys.system_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque colonne des objets système ayant des colonnes.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|Identificateur de l'objet auquel appartient cette colonne.|  
|**nom**|**sysname**|Nom de la colonne. Unique dans l'objet.|  
|**column_id**|**Int**|ID de la colonne. Unique dans l'objet.<br /><br /> Les ID de colonnes peuvent ne pas être séquentiels.|  
|**system_type_id**|**tinyint**|ID du type de système de la colonne|  
|**user_type_id**|**Int**|ID du type de colonne tel que défini par l'utilisateur.<br /><br /> Pour retourner le nom du type, joindre à la [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) vue sur cette colonne de catalogue.|  
|**max_length**|**smallint**|Longueur maximale (en octets) de colonne.<br /><br /> -1 = la colonne est de type de données **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, ou **xml**.<br /><br /> Pour **texte** colonnes, le **max_length** valeur sera 16 ou la valeur définie par **sp_tableoption** 'text in row'.|  
|**Précision**|**tinyint**|Précision de la colonne si elle est numérique ; Sinon, 0.|  
|**Mise à l’échelle**|**tinyint**|Échelle de la colonne si numérique ; sinon, 0.|  
|**collation_name**|**sysname**|Nom du classement de la colonne si elle est basée sur des caractères ; Sinon, NULL.|  
|**is_nullable**|**bit**|1 = La colonne accepte les valeurs NULL.|  
|**is_ansi_padded**|**bit**|1 = La colonne utilise le comportement ANSI_PADDING ON si elle est de type caractère, binaire ou variant.<br /><br /> 0 = La colonne n'est pas de type caractère, binaire ou variant.|  
|**is_rowguidcol**|**bit**|1 = La colonne est un ROWGUIDCOL déclaré.|  
|**is_identity**|**bit**|1 = La colonne comporte des valeurs d'identité.|  
|**is_computed**|**bit**|1 = La colonne est calculée.|  
|**is_filestream**|**bit**|1 = La colonne est déclarée utiliser un stockage de flux de fichier.|  
|**is_replicated**|**bit**|1 = La colonne est répliquée.|  
|**is_non_sql_subscribed**|**bit**|1 = La colonne possède un abonné non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**is_merge_published**|**bit**|1 = La colonne est associée à une publication fusionnée.|  
|**is_dts_replicated**|**bit**|1 = La colonne est répliquée à l'aide de [!INCLUDE[ssIS](../../includes/ssis-md.md)].|  
|**is_xml_document**|**bit**|1 = Le contenu est un document XML complet.<br /><br /> 0 = le contenu est un fragment de document ou le type de données de colonne n’est pas **xml**.|  
|**xml_collection_id**|**Int**|Valeur différente de zéro si le type de données de colonne est **xml** et le code XML est tapé. La valeur correspondra à l'ID de la collection qui contient l'espace de noms de schéma XML de validation de la colonne.<br /><br /> 0 = Aucune collection de schéma XML.|  
|**default_object_id**|**Int**|ID de l’objet par défaut, qu’il s’agisse autonome [sys.sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md), ou une ligne, la contrainte de valeur par défaut au niveau des colonnes. Le **parent_object_id** colonne d’un objet de valeur par défaut au niveau des colonnes inline est une référence à la table elle-même. Il aura la valeur 0 en l'absence de valeur par défaut.|  
|**rule_object_id**|**Int**|ID de la règle autonome liée à la colonne à l’aide de **sys.sp_bindrule**.<br /><br /> 0 = Aucune règle autonome.<br /><br /> Pour les contraintes de validation au niveau des colonnes, consultez [sys.check_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|**bit**|1 = La colonne est éparse. Pour plus d’informations, consultez [Utiliser des colonnes éparses](../../relational-databases/tables/use-sparse-columns.md).|  
|is_column_set|**bit**|1 = La colonne est un jeu de colonnes. Pour plus d’informations, consultez [Utiliser des jeux de colonnes](../../relational-databases/tables/use-column-sets.md).|  
|generated_always_type|**tinyint**|La valeur numérique représentant le type de colonne :<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END|  
|generated_always_type_desc|**nvarchar(60)**|La description textuelle du type de colonne :<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END<br /><br /> **S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Interrogation des catalogues système SQL Server FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [Sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
  
  
