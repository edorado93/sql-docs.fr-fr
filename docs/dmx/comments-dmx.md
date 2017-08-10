---
title: Commentaires (DMX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- comments [DMX]
- Data Mining Extensions [Analysis Services], comments
- double forward slashes
- commenting characters
- text strings [SQL Server]
- remarks [DMX]
- forward slash-asterisk character pairs
- DMX [Analysis Services], comments
- /*...*/ (comment)
- double hyphens
- // (comment)
- -- (comment character)
ms.assetid: 64d10eb5-4fe8-42c6-b387-eff336315e56
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 012feb6b830b18151708a85259a0d52ba195788f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="comments-dmx"></a>Commentaires (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Commentaires dans les Extensions DMX (Data Mining) sont des chaînes de texte dans un programme de code qui [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne s’exécute pas. Les commentaires sont également appelés remarques. Vous pouvez utiliser les commentaires pour documenter du code ou pour désactiver temporairement les composants d'une instruction ou d'un script DMX lorsque vous analysez le code.  
  
 L'utilisation des commentaires pour documenter votre code programme facilitera la gestion du code.  En effet, les commentaires permettent d'enregistrer des détails tels que le nom du programme, le nom du développeur qui a écrit le code, et les dates des principales modifications du code. Vous pouvez également aussi les utiliser pour décrire des calculs complexes ou pour commenter une méthode de programmation.  
  
 Voici les règles de bases de l'écriture des commentaires :  
  
-   Vous pouvez utiliser tous les caractères ou symboles alphanumériques dans un commentaire. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignore tous les caractères figurant au sein d'un commentaire.  
  
-   La longueur d'un commentaire dans une instruction ou un script n'est pas limitée. Un commentaire peut être constitué d’une ou plusieurs lignes.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge les types de caractères de commentaire suivants :  
  
-   **(doubles barres obliques).** Ces caractères de commentaire permettent d'écrire un commentaire sur la même ligne que le code à exécuter, ou d'écrire un commentaire sur une ligne séparée. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère tout ce qui est situé à partir des doubles barres obliques jusqu'à la fin de la ligne comme étant le commentaire. Pour créer un commentaire sur plusieurs lignes, utilisez les doubles barres obliques au début de chaque ligne de commentaire. Pour plus d’informations sur ce caractère de commentaire, consultez [barre oblique de Double &#40; Commentaire &#41; &#40; DMX &#41; ](../dmx/double-slash-comment-dmx.md).  
  
-   **--(double trait d’union).** Ces caractères de commentaire permettent d'écrire un commentaire sur la même ligne que le code à exécuter, ou d'écrire un commentaire sur une ligne séparée. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère tout ce qui est situé à partir du double trait d'union jusqu'à la fin de la ligne comme étant le commentaire. Pour créer un commentaire sur plusieurs lignes, utilisez le double trait d'union au début de chaque ligne de commentaire. Pour plus d’informations sur ce caractère de commentaire, consultez [--&#40; Commentaire &#41; &#40; DMX &#41; Résumé](../dmx/comment-dmx-summary.md).  
  
-   **/\*... \*/ (barre oblique-astérisque paires de caractères).** Ces caractères de commentaire permettent d'écrire un commentaire sur la même ligne que le code à exécuter, d'écrire un commentaire sur une ligne séparée ou même d'écrire des commentaires dans du code exécutable. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]évalue tous les éléments dans le commentaire ouvrant (/ *) pour le commentaire fermant (\*/) en tant que partie du commentaire. Pour créer un commentaire de plusieurs lignes, commencez le commentaire par la paire de caractères de commentaire (/\*) et la fin du commentaire la paire de caractères de commentaire (\*/). Aucun autre caractère de commentaire ne doit être inclus dans les lignes de commentaire. Pour plus d’informations sur ce caractère de commentaire, consultez [étoile de barre oblique &#40; Commentaire &#41; &#40; DMX &#41; ](../dmx/slash-star-comment-dmx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence](../dmx/data-mining-extensions-dmx-reference.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Fonctions de prédiction générales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
