---
title: Rechercher des problèmes de nouvelle tentative de lecture dans le sous-système d’entrées/sorties disque | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 32bc29554838858cd6e4bb0f3693628ab45b2a62
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751862"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>Rechercher des problèmes de nouvelle tentative de lecture dans le sous-système d’entrées/sorties
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle recherche le message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 825 dans le journal des événements. Ce message indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas pu lire les données du disque à la première tentative. Ce message signale un problème majeur avec le sous-système d'E/S. Il n’indique pas un problème avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutefois, le problème de disque peut entraîner la perte de données ou l'altération des bases de données s'il n'est pas résolu.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Les actions suivantes peuvent vous aider à identifier et à résoudre le problème matériel sous-jacent :  
  
-   Consultez le journal des erreurs et le texte spécifique de ce message pour trouver des indications expliquant pourquoi le problème s'est produit.  
  
-   Vérifiez le système de disques. Le problème peut être lié aux disques, aux contrôleurs de disques, aux cartes de disques ou aux pilotes de disques.  
  
-   Contactez le fabricant de vos disques pour vous procurer les utilitaires les plus récents permettant de vérifier l'état de votre système de disques.  
  
-   Contactez le fabricant de vos disques pour obtenir les dernières mises à jour des pilotes.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [MSSQLSERVER_825](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 [SQL Server I/O Basics, Chapter 2 (en anglais)](http://go.microsoft.com/fwlink/?linkid=69370)  
  
  
