---
title: Créer un projet SMO Visual c# dans Visual Studio .NET | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8abffe99e34df0aa4387651775eb2a3159da8bd7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121521"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a>Créer un projet SMO Visual C# dans Visual Studio .NET
  Cette section décrit comment élaborer une application de console SMO simple.  
  
 Cet exemple importe des espaces de noms, qui permettent au programme de référencer des types SMO. L'importation de l'espace de noms `Agent` est facultative. Utilisez-le lorsque vous écrivez un programme qui utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. L'espace de noms `Common` est requis pour établir une connexion sécurisée avec l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'espace de noms `SqlClient` est utilisé pour traiter les erreurs d'exception SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Création d'un projet SMO Visual C# dans Visual Studio.NET  
  
1.  Démarrez [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (ou [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).  
  
2.  Dans le menu **Fichier**, cliquez sur **Nouveau projet**. La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans **Types de projets** boîte de dialogue, sélectionnez **Visual C#**, puis sélectionnez **Windows**. Dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] volet Modèles installés, sélectionnez **Windows Application**.  
  
4.  (Facultatif) Dans le **nom** , tapez le nom de la nouvelle application  
  
5.  Sélectionnez le type d'application Visual C#. Pour les exemples qui suivent, sélectionnez **Application Console**.  
  
6.  Dans le menu **Projet**, sélectionnez **Ajouter une référence**. La boîte de dialogue **Ajouter une référence** s’affiche.  
  
7.  Cliquez sur **Parcourir**, localisez les assemblys SMO dans le [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] dossier et sélectionnez les fichiers suivants. Il s'agit des fichiers minimum requis pour générer une application SMO :  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
    > [!NOTE]  
    >  Utilisez la touche `Ctrl` pour sélectionner plusieurs fichiers.  
  
8.  Ajoutez les autres assemblys SMO qui sont nécessaires. Par exemple, si vous programmez spécifiquement [!INCLUDE[ssSB](../../includes/sssb-md.md)], ajoutez les assemblys suivants :  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. Cliquez sur **Ouvrir**.  
  
10. Sur le **vue** menu, cliquez sur **Code**. - ou - sélectionnez le Program1.cs [Design] Windows et double-cliquez sur le windows form pour afficher la fenêtre de code.  
  
11. Dans le code, avant l'instruction d'espace de noms, tapez les instructions `using` suivantes pour qualifier les types dans l'espace de noms SMO :  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. SMO comporte différents espaces de noms sous Microsoft.SqlServer.Management.Smo, par exemple Microsoft.SqlServer.Management.Smo.Agent. Ajoutez ces espaces de noms lorsqu'ils sont requis.  
  
13. Vous pouvez à présent ajouter votre code SMO.  
  
  
