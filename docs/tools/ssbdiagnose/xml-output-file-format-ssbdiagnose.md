---
title: Format de fichier de sortie XML (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35efa723a022ca4982b5d7113041841b508cf7d3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815113"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Format du fichier de sortie XML (ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La sortie de l’utilitaire **ssbdiagnose** est écrite dans un fichier XML lorsque vous l’exécutez avec le commutateur **-XML** . Le fichier de sortie XML répertorie les informations d'en-tête et les erreurs identifiées dans la configuration [!INCLUDE[ssSB](../../includes/sssb-md.md)] ou la conversation analysée. Vous pouvez écrire une application qui analyse ou effectue un rapport sur les erreurs répertoriées dans le fichier. Vous pouvez également consulter le fichier XML dans tout éditeur XML, comme le bloc-notes XML.  
  
 Un fichier de sortie de **ssbdiangose** contient un élément racine DiagnosticInformation avec deux types enfants :  
  
-   Un élément Banner contenant les informations d'en-tête.  
  
-   Un élément Issue pour chaque problème signalé par **ssbdiagnose**.  
  
## <a name="diagnosticinformation-root-element"></a>Élément racine DiagnosticInformation  
  
-   [Élément DiagnosticInformation &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Élément Banner  
  
-   [Élément Banner &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Élément Issue  
  
-   [Élément Issue &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Utilitaire ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
