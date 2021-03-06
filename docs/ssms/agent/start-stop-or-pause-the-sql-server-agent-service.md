---
title: Démarrer, arrêter ou suspendre le service SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 59821dc7a1a9824d630d174937e04272af014cab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705127"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>Start, Stop, or Pause the SQL Server Agent Service
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment démarrer, arrêter ou redémarrer le service de l'Agent SQL Server dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Vous pouvez configurer le service l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour qu'il démarre automatiquement lorsque le système d'exploitation démarre, ou vous pouvez le démarrer manuellement lorsque vous avez besoin d'exécuter des travaux. Vous pouvez arrêter ou interrompre le service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour interrompre les travaux, les notifications de l'opérateur et les alertes.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   [Pour démarrer, arrêter ou redémarrer le service de l'Agent SQL Server à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être exécuté en tant que service pour automatiser les tâches administratives. Pour plus d’informations, consultez [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).  
  
-   Cependant, l'Explorateur d'objets affiche le nœud [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent uniquement si vous avez l'autorisation de l'utiliser.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
Pour plus d’informations sur les autorisations Windows nécessaires pour le compte de service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consultez [Sélectionner un compte pour le service SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) et [Setting Up Windows Service Accounts](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)(Configuration des comptes de service Windows).  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>Pour démarrer, arrêter ou redémarrer le service de l'Agent SQL Server  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez gérer le service de l'Agent SQL Server.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis sélectionnez **Démarrer**, **Arrêter**ou **Redémarrer**.  
  
3.  Dans la boîte de dialogue **Contrôle de compte d'utilisateur** , cliquez sur **Oui**.  
  
4.  Lorsque vous y êtes invité, et si vous souhaitez exécuter l'action, cliquez sur **Oui**.  
  
Pour plus d'informations, consultez :  
  
-   [Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](http://msdn.microsoft.com/32660a02-e5a1-411a-9e57-7066ca459df6)  
  
-   [Démarrer automatiquement SQL Server Agent &#40;SQL Server Management Studio&#41;](../../ssms/agent/autostart-sql-server-agent-sql-server-management-studio.md)  
  
