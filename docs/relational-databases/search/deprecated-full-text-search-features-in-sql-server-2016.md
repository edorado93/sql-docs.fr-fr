---
title: "Fonctionnalit&#233;s de recherche en texte int&#233;gral d&#233;conseill&#233;es dans SQL&#160;Server&#160;2016 | Microsoft Docs"
ms.custom: ""
ms.date: "08/19/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fonctionnalités déconseillées [recherche en texte intégral]"
  - "recherche en texte intégral [SQL Server], fonctionnalités déconseillées"
  - "requêtes de texte intégral [SQL Server], proximité"
ms.assetid: ab0d799c-ba79-4459-837b-c4862730dafd
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# Fonctionnalit&#233;s de recherche en texte int&#233;gral d&#233;conseill&#233;es dans SQL&#160;Server&#160;2016
  Cette rubrique décrit les fonctionnalités de la recherche en texte intégral déconseillées toujours disponibles dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N’utilisez pas de fonctions déconseillées dans les nouvelles applications.  
  
 Vous pouvez surveiller l’utilisation des fonctionnalités déconseillées à l’aide du compteur de performance Objet **SQL Server : fonctionnalités déconseillées** et des événements de suivi. Pour plus d’informations, consultez [Utilisation des objets SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).  
  
## Fonctionnalités non prises en charge dans la prochaine version de SQL Server  

  
|Fonctionnalité déconseillée|Remplacement|Nom de la fonctionnalité|ID de la fonctionnalité|  
|------------------------|-----------------|------------------|----------------|  
|Propriété FULLTEXTCATALOGPROPERTY : LogSize|Aucun.|FULLTEXTCATALOGPROPERTY**('LogSize')**|211|  
|Propriété FULLTEXTSERVICEPROPERTY :<br /><br /> ConnectTimeout<br /><br /> DataTimeout|Aucun.|FULLTEXTSERVICEPROPERTY**('ConnectTimeout')**<br /><br /> FULLTEXTSERVICEPROPERTY**('DataTimeout'**)|210<br /><br /> 209|  
|sp_fulltext_catalog|CREATE FULL CATALOG<br /><br /> ALTER FULLTEXT CATALOG<br /><br /> DROP FULLTEXT CATALOG|sp_fulltext_catalog|84|  
|sp_fulltext_column<br /><br /> sp_fulltext_database<br /><br /> sp_fulltext_table|CREATE FULL INDEX<br /><br /> ALTER FULLTEXT INDEX<br /><br /> DROP FULLTEXT INDEX|sp_fulltext_column<br /><br /> sp_fulltext_database<br /><br /> sp_fulltext_table|86<br /><br /> 87<br /><br /> 85 %|  
|sp_help_fulltext_catalogs<br /><br /> sp_help_fulltext_catalog_components<br /><br /> sp_help_fulltext_catalogs_cursor<br /><br /> sp_help_fulltext_columns<br /><br /> sp_help_fulltext_columns_cursor<br /><br /> sp_help_fulltext_tables<br /><br /> sp_help_fulltext_tables_cursor|sys.fulltext_catalogs<br /><br /> sys.fulltext_index_columns<br /><br /> sys.fulltext_indexes|sp_help_fulltext_catalogs<br /><br /> sp_help_fulltext_catalog_components<br /><br /> sp_help_fulltext_catalogs_cursor<br /><br /> sp_help_fulltext_columns<br /><br /> sp_help_fulltext_columns_cursor<br /><br /> sp_help_fulltext_table<br /><br /> sp_help_fulltext_tables_cursor|88<br /><br /> 203<br /><br /> 90<br /><br /> 92<br /><br /> 93<br /><br /> 91<br /><br /> 89|  
|Valeurs d’action sp_fulltext_service : clean_up, connect_timeout et data_timeout retournent la valeur zéro|Aucune|sp_fulltext_service @action=clean_up<br /><br /> sp_fulltext_service @action=connect_timeout<br /><br /> sp_fulltext_service @action=data_timeout|116<br /><br /> 117<br /><br /> 118|  
|Colonnes sys.dm_fts_active_catalogs :<br /><br /> is_paused<br /><br /> previous_status<br /><br /> previous_status_description<br /><br /> row_count_in_thousands<br /><br /> status<br /><br /> status_description<br /><br /> worker_count|Aucun.|dm_fts_active_catalogs.is_paused<br /><br /> dm_fts_active_catalogs.previous_status<br /><br /> dm_fts_active_catalogs.previous_status_description<br /><br /> dm_fts_active_catalogs.row_count_in_thousands<br /><br /> dm_fts_active_catalogs.status<br /><br /> dm_fts_active_catalogs.status_description<br /><br /> dm_fts_active_catalogs.worker_count|218<br /><br /> 221<br /><br /> 222<br /><br /> 224<br /><br /> 219<br /><br /> 220<br /><br /> 223|  
|Colonne sys.dm_fts_memory_buffers :<br /><br /> row_count|Aucun.|dm_fts_memory_buffers.row_count|225|  
|Colonnes sys.fulltext_catalogs :<br /><br /> path<br /><br /> data_space_id<br /><br /> Colonnes file_id|Aucun.|fulltext_catalogs.path<br /><br /> fulltext_catalogs.data_space_id<br /><br /> fulltext_catalogs.file_id|215<br /><br /> 216<br /><br /> 217|  
  
## Fonctionnalités non prises en charge dans une future version de SQL Server  
 Les fonctionnalités suivantes de recherche en texte intégral sont prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais seront supprimées dans une version ultérieure. La version spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas été déterminée.  
  
 La valeur **Nom de la fonctionnalité** apparaît dans les événements de suivi comme ObjectName et dans les compteurs de performance et sys.dm_os_performance_counters comme nom de l’instance. La valeur **ID de la fonctionnalité** apparaît dans les événements de suivi comme ObjectId.  
  
|Fonctionnalité déconseillée|Remplacement|Nom de la fonctionnalité|ID de la fonctionnalité|  
|------------------------|-----------------|------------------|----------------|  
|Opérateur NEAR générique CONTAINS et CONTAINSTABLE :<br /><br /> {<terme_simple> &#124; <terme_préfixe>}<br /><br /> {<br /><br /> { { NEAR &#124; ~ }    {<terme_simple> &#124; <terme_préfixe>} } [...*n*]<br /><br /> }|Opérateur NEAR personnalisé :<br /><br /> NEAR(<br /><br /> {   {<terme_simple> &#124; <terme_préfixe>} [ ,…*n* ]<br /><br /> &#124; ( {<terme_simple> &#124; <terme_préfixe>} [,…*n*] )<br /><br /> [,\<distance> [,\<order>] ]<br /><br /> }<br /><br /> )<br /><br /> \<distance> ::= {*integer* &#124; **MAX**}<br /><br /> \<order> ::= {TRUE &#124; **FALSE**}|FULLTEXT_OLD_NEAR_SYNTAX|247|  
|Option CREATE FULLTEXT CATALOG :<br /><br /> IN PATH '*chemin_racine*'<br /><br /> ON FILEGROUP *filegroup*|Aucun.|CREATE FULLTEXT CATLOG IN PATH<br /><br /> Aucun.<sup>*</sup>|237<br /><br /> Aucun.*|  
|Propriété DATABASEPROPERTYEX : IsFullTextEnabled|Aucun.|DATABASEPROPERTYEX**('IsFullTextEnabled')**|202|  
|Option sp_detach_db :<br /><br /> [ @keepfulltextindexfile = ] '*KeepFulltextIndexFile*'|Aucun.|sp_detach_db @keepfulltextindexfile|226|  
|Valeurs d’action sp_fulltext_service : resource_usage n’a pas de fonction.|Aucune|sp_fulltext_service @action=resource_usage|200|  
  
 \** L’objet **SQL Server : fonctionnalités déconseillées** ne surveille pas les occurrences de CREATE FULLTEXT CATLOG ON FILEGROUP *groupe de fichiers*.  
  
  