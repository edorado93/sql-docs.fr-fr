---
title: Sélectionner des tables et des colonnes Oracle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- selTabCol
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3c02f4a98ad0ee4d7b73fe20041a03b53b34b2b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051372"
---
# <a name="select-oracle-tables-and-columns"></a>Sélectionner des tables et des colonnes Oracle
  Utilisez la page Sélectionner des tables et des colonnes Oracle pour sélectionner les tables de la base de données source Oracle dans laquelle les modifications sont capturées. Cette page contient les éléments suivants :  
  
## <a name="options"></a>Options  
 **Liste de tables**  
 La liste de tables comporte trois colonnes :  
  
-   **Nom de la table Oracle**: nom de la table, y compris du schéma de la table.  
  
-   **Instance de capture**: nom de l’instance de capture utilisée pour nommer les objets de capture de données modifiées spécifiques à l’instance. L'instance de capture ne peut pas être NULL.  
  
     S'il n'est pas spécifié, le nom est dérivé du nom du schéma d'origine plus le nom de la table source au format `<schema-name>_<table-name>`. Le nom de l'instance de capture ne peut pas dépasser 100 caractères et doit être unique dans la base de données.  
  
     Vous pouvez cliquer dans n’importe quelle cellule de cette colonne pour modifier manuellement **capture_instance**.  
  
-   **Rôle de sécurité**: nom du rôle de régulation de base de données utilisé pour contrôler l'accès aux données modifiées.  
  
     Vous pouvez cliquer dans n’importe quelle cellule de cette colonne pour modifier manuellement **security_role**.  
  
 **Ajouter des tables**  
 Cliquez sur **Ajouter des tables** pour ouvrir la boîte de dialogue Sélection de table dans laquelle vous pouvez [sélectionner des tables Oracle pour capturer des modifications](select-oracle-tables-for-capturing-changes.md).  
  
 **Modifier**  
 Sélectionnez une table dans la liste et cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Propriétés** de cette table dans laquelle vous pouvez [apporter des modifications aux tables sélectionnées pour capturer les modifications](make-changes-to-the-tables-selected-for-capturing-changes.md).  
  
 **Supprimer**  
 Sélectionnez une table dans la liste et cliquez sur **Supprimer** pour supprimer la table de l’instance CDC.  
  
 Après avoir [sélectionné des tables Oracle pour capturer des modifications](select-oracle-tables-for-capturing-changes.md) et/ou [apporté des modifications aux tables sélectionnées pour capturer les modifications](make-changes-to-the-tables-selected-for-capturing-changes.md) à l’aide des boîtes de dialogue appropriées, cliquez sur **Suivant** pour [générer et exécuter le script de journalisation supplémentaire](generate-and-run-the-supplemental-logging-script.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer l’Instance de base de données de modifications SQL Server](how-to-create-the-sql-server-change-database-instance.md)   
 [Modifier des tables](edit-tables.md)   
 [Ajouter des tables à une instance CDC](add-tables-to-a-cdc-instance.md)   
 [Modifier les propriétés d’une table](edit-the-table-properties.md)  
  
  
