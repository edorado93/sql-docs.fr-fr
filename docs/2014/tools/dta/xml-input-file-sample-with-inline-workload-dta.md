---
title: Exemple de fichier d’entrée XML avec une charge de travail inline (Assistant Paramétrage de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d031b9042ef1a3ca4d6c7200cce4f6966e61ab02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121449"
---
# <a name="xml-input-file-sample-with-inline-workload-dta"></a>Exemple de fichier d'entrée XML avec une charge de travail Inline (Assistant Paramétrage de base de données)
  Copiez et collez cet exemple de fichier d'entrée XML qui spécifie une charge de travail avec l'élément **EventString** dans votre éditeur XML ou de texte favori. Vous pouvez utiliser l'élément **EventString** pour spécifier une charge de travail de script [!INCLUDE[tsql](../../includes/tsql-md.md)] dans le fichier d'entrée XML (au lieu d'un fichier de travail distinct). Une fois cet exemple copié dans votre outil d'édition, remplacez les valeurs spécifiées pour les éléments **Server**, **Database**, **Schema**, **Table**, **Workload**, **EventString**et **TuningOptions** par celles dont vous avez besoin pour votre session de paramétrage. Pour plus d’informations sur tous les attributs et éléments enfants que vous pouvez utiliser avec ces éléments, consultez la [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md) L'exemple ci-dessous utilise uniquement un sous-ensemble des options d'attributs et d'éléments enfants disponibles.  
  
## <a name="code"></a>Code  
 [!code-xml[InputFileSamples#InlineWorkloadInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#inlineworkloadinputfile)]  
  
## <a name="comments"></a>Commentaires  
 `USE database_name` peuvent être spécifiées dans la charge de travail inline contenue dans l'élément **EventString** .  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer et utiliser l'Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [Afficher et utiliser la sortie de l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)   
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
