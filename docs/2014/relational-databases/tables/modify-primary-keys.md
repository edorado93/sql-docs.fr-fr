---
title: Modifier des clés primaires | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- modifying primary keys
- primary keys [SQL Server], modifying
ms.assetid: 8e2a15ba-1cd1-4408-b860-16c3ee37d635
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c2545253d94418727e2c8945c96f891c089918b9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061579"
---
# <a name="modify-primary-keys"></a>Modifier des clés primaires
  Vous pouvez modifier une clé primaire dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Vous pouvez modifier la clé primaire d'une table en changeant l'ordre des colonnes, le nom de l'index, l'option clustered ou le facteur de remplissage.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour modifier une clé primaire à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-a-primary-key"></a>Pour modifier une clé primaire  
  
1.  Ouvrez le Concepteur de tables pour la table dont vous souhaitez modifier la clé primaire, cliquez avec le bouton droit dans le Concepteur de tables, puis cliquez sur **Index/Clés** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Index/Clés** , sélectionnez l’index de clé primaire dans la liste **Index ou clé unique/primaire sélectionné(e)** .  
  
3.  Effectuez l'une des actions décrites dans le tableau suivant :  
  
    |Pour|Procédez comme suit|  
    |--------|------------------------|  
    |Renommer la clé primaire|Tapez un nouveau nom dans la zone **Nom** . Assurez-vous que le nouveau nom n’existe pas déjà dans la liste **Index ou clé unique/primaire sélectionné(e)** .|  
    |Définir l'option clustered|Pour créer un index cluster pour la clé primaire, sélectionnez **Créer comme CLUSTERED**, puis sélectionnez l’option dans la zone de liste déroulante. Il ne peut exister qu'un seul index cluster par table. Si cette option n'est pas disponible pour votre index, désactivez d'abord ce paramètre sur l'index cluster existant.<br /><br /> Si cette option n'est pas sélectionnée, un index non-cluster unique est créé.|  
    |Définir un taux de remplissage|Développez la catégorie **Spécification du remplissage** et tapez un entier compris entre 0 et 100 dans la zone **Taux de remplissage** . Pour plus d’informations sur les facteurs de remplissage et leurs utilisations, consultez [Spécifier un facteur de remplissage pour un index](../indexes/specify-fill-factor-for-an-index.md).|  
    |Changer l'ordre des colonnes|Sélectionnez **Colonnes**, puis cliquez sur le bouton de sélection **(…)** situé à droite de la propriété. Dans la boîte de dialogue  **Colonnes d'index** , supprimez les colonnes de la clé primaire. Rajoutez-les ensuite dans l'ordre voulu. Pour supprimer une colonne clé, retirez simplement le nom de la colonne de la liste **Nom de la colonne** .|  
  
4.  Dans le menu **Fichier**, cliquez sur **Enregistrer***nom de la table*.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour modifier une clé primaire**  
  
 Pour modifier une contrainte PRIMARY KEY à l'aide de Transact-SQL, vous devez supprimer auparavant la contrainte PRIMARY KEY existante, puis la créer à nouveau en précisant sa nouvelle définition. Pour plus d'informations, consultez [Delete Primary Keys](delete-primary-keys.md) et [Create Primary Keys](create-primary-keys.md).  
  
###  <a name="TsqlExample"></a>  
