---
title: "Consid&#233;rations et limitations li&#233;es aux tables temporelles | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/24/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8a21481-0f0e-41e3-a1ad-49a84091b422
caps.latest.revision: 18
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 17
---
# Consid&#233;rations et limitations li&#233;es aux tables temporelles
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Certaines considérations et limitations sont pertinentes lorsque vous travaillez avec des tables temporelles en raison de la nature du contrôle de version du système.  
  
 Prenez les points suivants en compte lorsque vous travaillez avec des tables temporelles  
  
-   Une table temporelle doit avoir une clé primaire définie afin de mettre en corrélation les enregistrements de la table actuelle et la table d’historique. Et la table d’historique ne peut pas avoir une clé primaire définie.  
  
-   Les colonnes de période SYSTEM_TIME utilisées pour enregistrer les valeurs **SysStartTime** et **SysEndTime** doivent être définies avec le type de données datetime2.  
  
-   Si le nom d’une table d’historique est spécifié lors de sa création, vous devez spécifier le nom du schéma et de la table.  
  
-   Par défaut, la table d’historique est **PAGE** compressée.  
  
-   Si la table actuelle est partitionnée, la table d’historique est créée sur le groupe de fichiers par défaut car la configuration du partitionnement n’est pas répliquée automatiquement de la table actuelle dans la table d’historique.  
  
-   Les tables temporelle et d’historique ne peuvent pas être **FILETABLE** et peuvent contenir des colonnes de n’importe quel type de données pris en charge autre que **FILESTREAM**, car **FILETABLE** et **FILESTREAM** permettent de manipuler des données en dehors de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ce qui ne garantit pas le contrôle de version du système.  
  
-   Même si les tables temporelles prennent en charge les types de données blob, tels que **(n)varchar(max)**, **varbinary(max)**, **(n)text** et **image**, elles entraînent des coûts de stockage importants et ont un impact sur les performances en raison de leur taille. Par conséquent, il convient de prendre des précautions lorsque vous concevez votre système si vous souhaitez utiliser ces types de données .  
  
-   La table d’historique doit être créée dans la même base de données que le tableau actuel. L’interrogation temporelle par l’intermédiaire de **Linked Server** n’est pas prise en charge.  
  
-   La table d’historique ne peut pas avoir de contraintes (clé primaire, clé étrangère, contraintes de table ou de colonne).  
  
-   Les vues indexées ne sont pas prises en charge sur les requêtes temporelles (requêtes qui utilisent la clause **FOR SYSTEM_TIME** )  
  
-   L’option Online (**WITH (ONLINE = ON**) n’a aucun effet sur **ALTER TABLE ALTER COLUMN** si la version de table temporelle est contrôlée par le système. L’opération ALTER n’est pas effectuée en ligne, quelle que soit la valeur spécifiée pour l’option ONLINE.  
  
-   Les instructions **INSERT** et **UPDATE** ne peuvent pas faire référence à des colonnes de période SYSTEM_TIME. Les tentatives d’insertion de valeurs directement dans ces colonnes sont bloquées.  
  
-   **TRUNCATE TABLE** n’est pas pris en charge quand **SYSTEM_VERSIONING** a la valeur **ON**.  
  
-   La modification directe des données dans une table d’historique n’est pas autorisée.  
  
-   **ON DELETE CASCADE** et **ON UPDATE CASCADE** ne sont pas autorisées dans la table actuelle. En d’autres termes, quand la table temporelle fait référence à la table dans la relation de clé étrangère (correspondant à *parent_object_id* dans sys.foreign_keys), les options CASCADE ne sont pas autorisées. Pour contourner cette limitation, utilisez une logique d’application ou des déclencheurs After pour maintenir la cohérence en cas de suppression dans la table de clé primaire (correspondant à *referenced_object_id* dans sys.foreign_keys). Si la table de clé primaire est temporelle alors que la table de référence ne l’est pas, il n’existe aucune limitation de ce type.  
  
-   Les déclencheurs**INSTEAD OF** ne sont pas autorisés sur la table actuelle ou sur la table d’historique pour éviter l’invalidation de la logique DML. Les déclencheurs**AFTER** sont autorisés uniquement dans la table actuelle. Ils sont bloqués dans la table d’historique afin d’éviter l’invalidation de la logique DML.  
  
-   L’utilisation de technologies de réplication est limitée.  
  
    -   **Always On (Toujours active)** : entièrement prise en charge  
  
    -   **Capture de données modifiées et Suivi des modifications de données** : uniquement prises en charge dans la table actuelle  
  
    -   **Capture instantanée et réplication transactionnelle**: uniquement prise en charge pour un serveur de publication unique sans activation de Temporal et un abonné avec Temporal activé. Dans ce cas, le serveur de publication est utilisé pour une charge de travail OLTP tandis que l’abonné est utilisé pour le déchargement de rapports (y compris l’interrogation « AS OF »).    
        L’utilisation de plusieurs abonnés n’est pas prise en charge car ce scénario peut entraîner une incohérence des données temporelles, chacune d’elles dépendant de l’horloge système locale.  
  
    -   **Réplication de fusion** : non prise en charge pour les tables temporelles  
  
-   Les requêtes régulières affectent uniquement les données dans la table actuelle. Pour interroger des données dans la table d’historique, vous devez utiliser des requêtes temporelles. Ces points sont abordés dans ce document dans la section Interrogation des données temporelles.  
  
-   Une stratégie d’indexation optimale inclut stockage de colonnes d’index en cluster et / ou un index rowstore d’arbre B (B-tree) dans la table actuelle et un index columnstore en cluster dans la table d’historique pour des performances et une taille de stockage optimales. Si vous créez / utilisez votre propre table d’historique, nous vous recommandons vivement de créer ce type d’index comportant des colonnes de période en commençant à la fin de la colonne de période pour accélérer le traitement des requêtes temporelles et des requêtes qui font partie de la vérification de cohérence des données. La table d’historique par défaut a un index rowstore en cluster créé selon les colonnes de période (début, fin). Nous recommandons au minimum un index rowstore non-cluster.  
  
-   Les objets/propriétés suivantes ne sont pas répliquées à partir à la table d’historique actuelle lors de la création de la table d’historique  
  
    -   Définition de la période  
  
    -   Définition de l’identité  
  
    -   Index  
  
    -   Statistiques  
  
    -   Contraintes de validation  
  
    -   Déclencheurs  
  
    -   Configuration du partitionnement  
  
    -   Autorisations  
  
    -   Prédicats de sécurité au niveau des lignes  
  
-   Une table d’historique ne peut pas être configurée en tant que table actuelle d’une chaîne de tables d’historique.  
  
## Cet article vous a-t-il été utile ? Nous sommes à votre écoute  
 Quels renseignements souhaitez-vous obtenir ? Avez-vous trouvé ce que vous cherchiez ? Nous tenons compte de vos commentaires pour améliorer le contenu de nos articles. Veuillez envoyer vos commentaires à l’adresse suivante : [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Table%20Considerations%20and%20Limitations%20page).  
  
## Voir aussi  
 [Tables temporelles](../../relational-databases/tables/temporal-tables.md)   
 [Prise en main des tables temporelles de contrôle de version du système](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Vérifications de cohérence système des tables temporelles](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Partitionnement des tables temporelles](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [Sécurité de la table temporelle](../../relational-databases/tables/temporal-table-security.md)   
 [Gérer la rétention des données d’historique dans les tables temporelles avec version gérée par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tables temporelles à système par version avec tables optimisées en mémoire](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Vues et fonctions de métadonnées de table temporelle](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  