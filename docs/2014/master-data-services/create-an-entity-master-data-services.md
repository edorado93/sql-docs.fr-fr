---
title: Créer une entité (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1fdca5fb5b8600664d22aabb0b87f458a84f0937
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129559"
---
# <a name="create-an-entity-master-data-services"></a>Créer une entité (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une entité destinée à contenir des membres et leurs attributs.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Un modèle doit exister. Pour plus d’informations, consultez [Créer un modèle &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).  
  
### <a name="to-create-an-entity"></a>Pour créer une entité  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Cliquez sur **ajouter une entité**.  
  
5.  Dans le **nom de l’entité** , tapez le nom de l’entité.  
  
6.  Dans le **nom des tables intermédiaires** , tapez un nom pour la table intermédiaire.  
  
    > [!TIP]  
    >  Utilisez le nom du modèle dans le nom de la table de mise en lots, par exemple *NomModèle_NomEntité*. Cela facilite la recherche de tables dans la base de données. Pour plus d’informations sur les tables intermédiaires, consultez [importation des données &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
7.  Facultatif. Activez la case à cocher **Créer automatiquement les valeurs de code** . Pour plus d’informations, consultez [Création automatique de code &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md).  
  
8.  À partir de la **activer les hiérarchies explicites et collections** liste, sélectionnez une des options suivantes :  
  
    -   **Ne**. Sélectionnez cette option si vous n'avez pas besoin d'activer l'entité pour les hiérarchies et les collections explicites. Vous pouvez changer ce paramètre ultérieurement si nécessaire.  
  
    -   **Oui**. Sélectionnez cette option lorsque vous souhaitez activer l'entité pour les hiérarchies et collections explicites. Dans le **nom de la hiérarchie explicite** , tapez un nom. Si vous le souhaitez, sélectionnez **hiérarchie obligatoire (tous les membres feuille sont inclus** pour rendre la hiérarchie explicite obligatoire.  
  
9. Cliquez sur **enregistrer l’entité**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Créer un attribut de texte &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [Créer un attribut basé sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [Créer un attribut de fichier &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Entités &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)   
 [Hiérarchies explicites &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [Modifier un nom d’entité &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md)   
 [Supprimer une entité &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  
