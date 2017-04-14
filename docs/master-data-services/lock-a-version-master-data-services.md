---
title: "Verrouiller une version (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "versions [Master Data Services], verrouillage"
  - "verrouillage de versions [Master Data Services]"
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Verrouiller une version (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], verrouillez une version d’un modèle pour empêcher que des modifications ne soient apportées aux membres du modèle et à leurs attributs.  
  
> [!NOTE]  
>  Quand une version est verrouillée, les super utilisateurs et les administrateurs de modèle peuvent continuer à ajouter, à modifier et à supprimer des membres. Les autres utilisateurs qui ont une autorisation sur le modèle peuvent consulter les membres uniquement.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   L’état de la version doit être **Ouvert**.  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle Gestion des versions. Pour plus d’informations, consultez [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### Pour verrouiller une version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions**, sélectionnez la ligne de la version à verrouiller.  
  
3.  Cliquez sur **Verrouiller**.  
  
4.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
## Étapes suivantes  
  
-   [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Activer une version &#40;Master Data Services&#41;](../master-data-services/commit-a-version-master-data-services.md)  
  
## Voir aussi  
 [Versions &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [Déverrouiller une version &#40;Master Data Services&#41;](../master-data-services/unlock-a-version-master-data-services.md)  
  
  