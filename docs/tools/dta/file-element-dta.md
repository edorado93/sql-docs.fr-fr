---
title: "File, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "File (élément)"
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# File, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es)
  Spécifie le fichier de charge de travail. Une charge de travail est un ensemble d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui s'exécute sur une ou plusieurs bases de données que vous souhaitez paramétrer. Les fichiers de charge de travail peuvent être des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] (.sql) ou des fichiers de trace (.trc). Pour plus d’informations, consultez [Démarrer et utiliser l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).  
  
## Syntaxe  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Utilisez le type de données **string** pour spécifier le chemin du répertoire de votre fichier de charge de travail. Par exemple :<br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> Notez que la limite de longueur est appliquée par le serveur.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois si aucun autre type de charge de travail n'est spécifié. Vous devez spécifier un élément enfant **EventString**, **File**ou **Database** pour le parent **Workload** , mais un seul type peut être utilisé. Par exemple, si vous spécifiez une charge de travail avec l’élément **File**, vous ne pouvez pas spécifier une charge de travail avec l’élément **Database** dans le même fichier d’entrée XML.|  
  
## Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Workload, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/workload-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML simple &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  