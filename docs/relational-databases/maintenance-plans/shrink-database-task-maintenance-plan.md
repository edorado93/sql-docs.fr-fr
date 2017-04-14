---
title: "T&#226;che R&#233;duire la base de donn&#233;es (Plan de maintenance) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Shrink Database Task"
  - "Shrink Database(s) Task"
  - "sql13.swb.maint.shrink.f1"
helpviewer_keywords: 
  - "Tâche Réduire la base de données (boîte de dialogue)"
ms.assetid: a9874cac-cded-4145-9c38-8aafd267dbee
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# T&#226;che R&#233;duire la base de donn&#233;es (Plan de maintenance)
  Utilisez la boîte de dialogue **Tâche Réduire la base de données** pour créer une tâche qui tente de réduire la taille des bases de données sélectionnées. Utilisez les options ci-dessous pour déterminer la quantité d'espace inutilisé à conserver dans la base de données après sa réduction (plus le pourcentage est élevé, moins la base la base de données sera réduite). La valeur est calculée à partir du pourcentage des données effectivement présentes dans la base de données. Par exemple, une base de données de 100 Mo qui contiendrait 60 Mo de données et 40 Mo d'espace libre, avec un pourcentage d'espace libre de 50 %, pourrait conduire à 60 Mo de données et 30 Mo d'espace libre (en effet, 50 % de 60 Mo font 30 Mo). Seul l'espace supplémentaire de la base de données est éliminé. Les valeurs valides sont comprises entre 0 et 100.  
  
 La réduction des fichiers de données permet de récupérer de l'espace en déplaçant des pages de données de la fin du fichier vers un espace inoccupé plus proche de l'avant du fichier. Lorsqu'une quantité d'espace libre suffisante est créée à la fin du fichier, des pages de données à la fin du fichier peuvent être désallouées et retournées au système de fichiers.  
  
> [!WARNING]  
>  Les données qui sont déplacées pour réduire un fichier peuvent être dispersées à n'importe quel emplacement disponible dans le fichier. Cela provoque la fragmentation de l'index et peut ralentir les performances des requêtes qui recherchent une plage de l'index. Pour éliminer la fragmentation, reconstruisez les index dans le fichier après réduction.  
  
 Cette tâche exécute l'instruction DBCC SHRINKDATABASE.  
  
## Options  
 **Connexion**  
 Sélectionnez la connexion serveur à utiliser pour exécuter la tâche.  
  
 **Nouveau**  
 Crée une nouvelle connexion serveur à utiliser pour exécuter la tâche. La boîte de dialogue **Nouvelle connexion** est décrite ci-dessous.  
  
 **Bases de données**  
 Spécifie les bases de données faisant l'objet de cette tâche.  
  
-   **Toutes les bases de données**  
  
     Génère un plan de maintenance qui exécute les tâches de maintenance sur toutes les bases de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l’exception de tempdb.  
  
-   **Toutes les bases de données système**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur chaque base de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l'exception de tempdb. Aucune tâche de maintenance n'est exécutée sur les bases de données créées par l'utilisateur.  
  
-   **Toutes les bases de données utilisateur**  
  
     Génère un plan de maintenance qui exécute des tâches de maintenance sur toutes les bases de données créées par l'utilisateur. Aucune tâche de maintenance n'est exécutée sur les bases de données système de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Ces bases de données**  
  
     Génère un plan de maintenance qui n'exécute les tâches de maintenance que sur les bases de données sélectionnées. Si vous choisissez cette option, sélectionnez au moins une base de données.  
  
    > [!NOTE]  
    >  Les plans de maintenance sont exécutés uniquement sur des bases de données définies au niveau de compatibilité 80 ou plus. Les bases de données définies au niveau de compatibilité 70 ou moins ne sont pas affichées.  
  
 **Réduire la base de données lorsqu'elle excède**  
 Indiquez la taille de base de données (en mégaoctets) qui doit être atteinte pour que l'exécution de la tâche soit déclenchée.  
  
 **Quantité d'espace disponible restant après réduction**  
 Arrête la réduction lorsque l'espace libre dans les fichiers de base de données atteint cette taille.  
  
 **Vue T-SQL**  
 Affiche les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutées sur le serveur pour cette tâche, selon les options sélectionnées.  
  
> [!NOTE]  
>  Si le nombre d'objets impliqués est élevé, l'affichage des instructions peut prendre un temps considérable.  
  
## Boîte de dialogue Nouvelle connexion  
 **Nom de la connexion**  
 Entrez un nom pour la nouvelle connexion.  
  
 **Sélectionnez ou entrez un nom de serveur.**  
 Sélectionnez un serveur auquel établir la connexion pour exécuter la tâche.  
  
 **Actualiser**  
 Actualise la liste des serveurs disponibles.  
  
 **Entrez des informations pour vous connecter au serveur**  
 Spécifiez le mode d'authentification sur le serveur.  
  
 **Utiliser la sécurité intégrée de Windows NT**  
 Permet de se connecter à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’authentification [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Utiliser un nom d'utilisateur et un mot de passe spécifiques**  
 Permet de se connecter à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option n'est pas disponible.  
  
 **Nom d'utilisateur**  
 Fournit le nom d'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
 **Mot de passe**  
 Fournit un mot de passe à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
## Voir aussi  
 [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)  
  
  