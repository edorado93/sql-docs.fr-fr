---
title: Ajouter une carte personnalisée à un rapport mobile Reporting Services | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: fd259b95-bb58-4eb1-a436-6aa12fc6f5f2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b2f2d3b15021569fe53bfc886f744ed7e53c1444
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646957"
---
# <a name="add-a-custom-map-to-a-reporting-services-mobile-report"></a>Ajouter une carte personnalisée à un rapport mobile Reporting Services
Les cartes personnalisées requièrent deux fichiers :  
* Un fichier SHP pour les géométries de forme  
* Un fichier DBF pour les métadonnées  
  
En savoir plus sur les [cartes personnalisées dans les rapports pour mobiles Reporting Services](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md).  
  
Stockez ces deux fichiers dans le même dossier. Les noms de ces deux fichiers doivent correspondre (par exemple, canada.shp et canada.dbf). Les métadonnées (fichier DBF) doivent inclure le champ « NAME » avec la valeur du nom de la forme correspondante (key), pour être utilisées lors de l’ajout des données dans la carte.   
  
## <a name="load-a-custom-map"></a>Charger une carte personnalisée  
  
1. Dans l’onglet **Disposition** , sélectionnez le type **Carte à gradient**, **Carte à seuils**ou **Carte à bulles**, faites-la glisser sur l’aire de conception et dimensionnez-la.  
  
   ![SSMRP_MapsGallery](../../reporting-services/mobile-reports/media/ssmrp-mapsgallery.png)  
  
2. Dans la vue **Disposition** > panneau **Propriétés visuelles** > **Carte**, sélectionnez **Carte personnalisée d’un fichier**.   
  
   ![SSMRP_SelectCustomMap](../../reporting-services/mobile-reports/media/ssmrp-selectcustommap.png)  
  
3. Dans la boîte de dialogue **Ouvrir** , accédez à l’emplacement des fichiers SHP et DBF et sélectionnez les deux.   
  
   ![SSMRP_SelectDBFandSHP](../../reporting-services/mobile-reports/media/ssmrp-selectdbfandshp.png)  
  
## <a name="connect-data-to-a-custom-map"></a>Connecter des données à une carte personnalisée  
Lorsque vous ajoutez la carte personnalisée dans votre rapport, [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] la remplit avec des données géographiques simulées.  
  
![SSMRP_MapsData](../../reporting-services/mobile-reports/media/ssmrp-mapsdata.png)  
  
L’affichage des données réelles dans votre carte personnalisée est identique à celui des données dans les cartes intégrées. Suivez la procédure décrite dans [Cartes dans les rapports pour mobiles Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md) pour afficher vos données.  
  
### <a name="see-also"></a>Voir aussi  
- [Custom maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Cartes dans les rapports pour mobiles Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Créer et publier des rapports mobiles avec l’Éditeur de rapports mobiles SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
  
