---
title: Traiter les Partitions de modèles tabulaires (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 6c498d2b-22d6-4661-bc21-2ee708336c8b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e113f931e318c501f69540ec19e97e3ae72b553f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130539"
---
# <a name="process-tabular-model-partitions-ssas-tabular"></a>Traiter les partitions de modèles tabulaires (SSAS Tabulaire)
  Les partitions divisent une table en sections logiques. Chaque partition peut ensuite être traitée (actualisée) indépendamment d'autres partitions. Les tâches de cette rubrique décrivent comment traiter les partitions dans une base de données model à l'aide de la boîte de dialogue **Traiter la ou les partitions** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
###  <a name="bkmk_create_new"></a> Pour traiter une partition  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur la table qui contient les partitions à traiter, puis sélectionnez **Partitions**.  
  
2.  Dans la boîte de dialogue **Partitions** , dans **Partitions**, cliquez sur le bouton Traiter.  
  
3.  Dans la boîte de dialogue **Traiter la ou les partitions** , dans la zone de liste **Mode** , sélectionnez l’un des modes de traitement suivants :  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Traiter par défaut**|Détecte l'état de traitement d'un objet de partition et effectue le traitement nécessaire pour faire passer les objets de partition non traités ou traités partiellement dans un état de traitement complet. Les données des partitions et des tables vides sont chargées ; les hiérarchies, les colonnes calculées et les relations sont créées ou reconstruites.|  
    |**Traiter entièrement**|Traite un objet de partition et tous les objets qu'il contient. Lorsque la commande Traiter entièrement est exécutée pour un objet qui a déjà été traité, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supprime toutes les données de l'objet, puis traite l'objet. Ce type de traitement est obligatoire lorsqu'une modification structurelle a été apportée à un objet.|  
    |**Traiter des données**|Chargez les données dans une partition ou une table sans reconstruire les hiérarchies ou les relations ni recalculer les colonnes calculées et les mesures.|  
    |**Traiter l'effacement**|Supprime toutes les données d'une partition.|  
    |**Traiter l'ajout**|Mise à jour incrémentielle de la partition avec de nouvelles données.|  
  
4.  Dans la colonne de case à cocher **Traiter** , sélectionnez les partitions à traiter avec le mode sélectionné, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions de modèles tabulaires &#40;SSAS tabulaire&#41;](partitions-ssas-tabular.md)   
 [Créer et gérer des Partitions de modèles tabulaires &#40;SSAS tabulaire&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
