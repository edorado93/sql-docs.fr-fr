---
title: Répertorier les informations de catégorie de travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 69abea91334f53993fec78e2204cee1573afd780
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181579"
---
# <a name="list-job-category-information"></a>Répertorier les informations de catégorie de travaux
  Comment répertorier les informations de catégorie de travaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou SQL Server Management Objects.  

  
##  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  

  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>Pour répertorier les informations de catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_help_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).  
  
  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 **Pour répertorier les informations de catégorie de travaux**  
  
 Utilisez la `JobCategory` classe à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual c# ou PowerShell... Pour plus d’informations, consultez [SQL Server Management Objects &#40;SMO&#41; Guide de programmation](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).  
  
  
  
