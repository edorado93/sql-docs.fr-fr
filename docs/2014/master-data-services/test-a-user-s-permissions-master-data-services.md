---
title: Tester les autorisations d’un utilisateur (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 6c506123c772e1063713fc81f32fdbbaa0d5c8f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051079"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>Tester les autorisations d’un utilisateur (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez créer un utilisateur de test et vous connecter à l'application Web pour tester les autorisations. Lorsqu'un utilisateur tente d'accéder à l'URL [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , les informations d'identification de l'utilisateur sont authentifiées. Dans Internet Explorer, les paramètres de sécurité déterminent si cette opération se produit automatiquement ou si l'utilisateur doit entrer un nom d'utilisateur et un mot de passe. Pour modifier ces paramètres, procédez comme suit :  
  
### <a name="to-test-a-users-security"></a>Pour tester la sécurité d'un utilisateur  
  
1.  Dans Internet Explorer 7 et version ultérieure, cliquez sur **Outils**, sur **Options Internet**, puis sur l'onglet **Sécurité** .  
  
2.  Cliquez sur **Intranet local** , puis sur le bouton **Personnaliser le niveau** .  
  
3.  Dans la section **Authentification utilisateur** , choisissez **Demander le nom d'utilisateur et le mot de passe**.  
  
4.  La prochaine fois que vous ouvrez la fenêtre de navigateur, vous serez invité à fournir un nom d'utilisateur et un mot de passe.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité &#40;Master Data Services&#41;](security-master-data-services.md)  
  
  
