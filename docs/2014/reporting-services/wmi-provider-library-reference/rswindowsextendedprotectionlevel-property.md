---
title: Propriété RSWindowsExtendedProtectionLevel (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 095d09011199aae209f4e659fdd1f9719a5a5ba8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172099"
---
# <a name="rswindowsextendedprotectionlevel-property-wmi-msreportserverconfigurationsetting"></a>Propriété RSWindowsExtendedProtectionLevel (WMI MSReportServer_ConfigurationSetting)
  Retourne une valeur de chaîne indiquant le niveau de protection configuré pour le serveur de rapports. Cette propriété est en lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a>Notes  
 Retourne une valeur de chaîne indiquant le niveau de protection configuré pour le serveur de rapports. Si le serveur de rapports auquel le fournisseur WMI est connecté ne prend pas en charge la protection étendue, “” (chaîne vide) est retourné. La liste suivante affiche les valeurs valides :  
  
 `“Off” | “Allow” | “Require”`  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété RSWindowsExtendedProtectionScenario &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [Méthode SetExtendedProtectionSettings &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md)   
 [Protection étendue de l’authentification avec Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [Fichier de configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
