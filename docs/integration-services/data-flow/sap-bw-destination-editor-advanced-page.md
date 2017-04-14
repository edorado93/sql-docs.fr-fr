---
title: "&#201;diteur de destination SAP&#160;BW (page Avanc&#233;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sapbwdestination.advanced.f1"
ms.assetid: 862957db-bbc6-4dda-bc0e-591457f1baa7
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# &#201;diteur de destination SAP&#160;BW (page Avanc&#233;)
  Utilisez la page **Avancé** de **l’Éditeur de destination SAP BW** pour définir les paramètres avancés tels que la taille du package et les informations de temps d’attente.  
  
 Pour en savoir plus sur la destination SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [Destination SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la page Avancé**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la destination SAP BW.  
  
2.  Sous l’onglet **Flux de données**, double-cliquez sur la destination SAP BW.  
  
3.  Dans **l’Éditeur de destination SAP BW**, cliquez sur **Avancé** pour ouvrir la page **Avancé** de l’éditeur.  
  
## Options  
  
> [!NOTE]  
>  Si vous ne connaissez pas toutes les valeurs requises pour configurer la destination, adressez-vous à votre administrateur SAP.  
  
 **Taille du package**  
 Spécifiez combien de lignes de données seront transférées à la fois. La valeur optimale de ce paramètre dépend du système SAP Netweaver BW et du traitement supplémentaire des données qui peut avoir lieu. En général, des valeurs comprises entre 2 000 et 20 000 offrent les meilleures performances.  
  
 **Déclencher la chaîne de processus**  
 (Facultatif) Spécifiez le nom d'une chaîne de processus à déclencher une fois le chargement des données terminé.  
  
 **Délai d'attente d'InfoPackage**  
 Spécifiez le nombre maximal de secondes pendant lesquelles la destination doit attendre la fin de l'InfoPackage.  
  
 **Attendre la fin du transfert de données**  
 Spécifiez si la destination doit attendre que le système SAP Netweaver BW ait terminé de charger les données.  
  
 **Ne pas démarrer InfoPackage (attendre uniquement)**  
 Spécifiez que la destination ne doit pas déclencher d'InfoPackage, mais attendre uniquement la notification informant que le système SAP Netweaver BW a démarré le chargement des données.  
  
## Voir aussi  
 [Éditeur de destination SAP BW &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Éditeur de destination SAP BW &#40;page Mappages&#41;](../../integration-services/data-flow/sap-bw-destination-editor-mappings-page.md)   
 [Éditeur de destination SAP BW &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/sap-bw-destination-editor-error-output-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  