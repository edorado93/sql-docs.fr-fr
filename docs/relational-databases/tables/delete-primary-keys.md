---
title: "Supprimer des cl&#233;s primaires | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "retrait des clés primaires"
  - "suppression des clés primaires"
  - "clés primaires [SQL Server], suppression"
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Supprimer des cl&#233;s primaires
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Vous pouvez supprimer une clé primaire dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Lorsque la clé primaire est supprimée, l'index correspondant l'est également.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une clé primaire à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour supprimer une contrainte de clé primaire à l'aide de l'Explorateur d'objets  
  
1.  Dans l'Explorateur d'objets, développez la table qui contient la clé primaire, puis développez **Clés**.  
  
2.  Cliquez avec le bouton droit sur la clé, puis sélectionnez **Supprimer**.  
  
3.  Dans la boîte de dialogue **Supprimer un objet** , vérifiez que la clé correcte est spécifiée et cliquez sur **OK**.  
  
#### Pour supprimer une contrainte de clé primaire à l'aide du Concepteur de tables  
  
1.  Dans l’Explorateur d'objets, cliquez avec le bouton droit sur la table avec la clé primaire, puis cliquez sur **Conception**.  
  
2.  Dans la grille de la table, cliquez avec le bouton droit sur la ligne contenant la clé primaire et choisissez **Supprimer la clé primaire** pour désactiver le paramètre.  
  
    > [!NOTE]  
    >  Pour annuler cette action, fermez la table sans enregistrer les modifications. La suppression d'une clé primaire ne peut pas être annulée sans perdre toutes les autres modifications apportées à la table.  
  
3.  Dans le menu **Fichier**, cliquez sur **Enregistrer***nom de la table*.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour supprimer une contrainte de clé primaire  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple identifie d'abord le nom de la contrainte de clé primaire et supprime ensuite la contrainte.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE&#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md) et [sys.key_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)  
  
###  <a name="TsqlExample"></a>  