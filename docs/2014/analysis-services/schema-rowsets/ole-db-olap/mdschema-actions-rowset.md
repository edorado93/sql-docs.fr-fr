---
title: Ensemble de lignes MDSCHEMA_ACTIONS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_ACTIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_ACTIONS rowset
ms.assetid: f73081f8-ac51-4286-b46e-2b34e792c3e0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 317ddc9a284df779a44866c0c037310b29f76d02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140725"
---
# <a name="mdschemaactions-rowset"></a>Ensemble de lignes MDSCHEMA_ACTIONS
  Décrit les actions qui peuvent être disponibles pour les applications clientes.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_ACTIONS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom de la base de données.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non pris en charge. Contient toujours `VT_NULL`.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube auquel appartient cette action.|  
|`ACTION_NAME`|`DBTYPE_WSTR`||Nom de cette action.|  
|`ACTION_TYPE`|`DBTYPE_I4`||Bitmap utilisé pour spécifier la méthode de déclenchement de l'action. Le fichier Msmd.h définit les constantes de valeur binaire suivantes pour cette image bitmap :<br /><br /> -   `MDACTION_TYPE_URL` (`0x01`)<br />-   `MDACTION_TYPE_HTML` (`0x02`)<br />-   `MDACTION_TYPE_STATEMENT` (`0x04`)<br />-   `MDACTION_TYPE_DATASET` (`0x08`)<br />-   `MDACTION_TYPE_ROWSET` (`0x10`)<br />-   `MDACTION_TYPE_COMMANDLINE` (`0x20`)<br />-   `MDACTION_TYPE_PROPRIETARY` (`0x40`)<br />-   `MDACTION_TYPE_REPORT` (`0x80`)<br />-   `MDACTION_TYPE_DRILLTHROUGH` (`0x100`)|  
|`COORDINATE`|`DBTYPE_WSTR`||Expression MDX (Multidimensional Expressions) qui spécifie un objet ou une coordonnée dans l'espace multidimensionnel dans lequel l'action est effectuée. L'application cliente est chargée de fournir la veleur de cette colonne de restriction.<br /><br /> Le `CORDINATE` doit résoudre l'objet spécifié dans `COORDINATE_TYPE`.|  
|`COORDINATE_TYPE`|`DBTYPE_I4`||Bitmap qui spécifie la manière dont la colonne de restriction `COORDINATE` est interprétée. Le fichier Msmd.h définit les constantes de valeur binaire suivantes pour cette image bitmap :<br /><br /> -   `MDACTION_COORDINATE_CUBE` (`1`)<br />-   `MDACTION_COORDINATE_DIMENSION` (`2`)<br />     fait référence aux hiérarchies de dimensions.<br />-   `MDACTION_COORDINATE_LEVEL` (`3`)<br />-   `MDACTION_COORDINATE_MEMBER` (`4`)<br />-   `MDACTION_COORDINATE_SET` (`5`)<br />-   `MDACTION_COORDINATE_CELL` (`6`)|  
|`ACTION_CAPTION`|`DBTYPE_WSTR`||Nom de l'action si aucune légende n'a été spécifiée et si aucune traduction n'a été spécifiée dans le DDL.<br /><br /> Si une légende ou des traductions ont été spécifiées, et que `CaptionIsMDX` est faux, l'une des chaînes suivantes :<br /><br /> -La traduction pour la langue appropriée.<br />-Légende spécifiée si aucune traduction n’a été trouvée pour la langue spécifiée.<br />-Le nom de l’action si aucune traduction n’a été trouvée et la légende n’a pas été spécifiée dans le DDL.<br /><br /> Si une légende ou des traductions ont été spécifiées, et que `CaptionIsMDX` soit vrai, chaîne qui résulte de la détection de la traduction appropriée pour la langue spécifiée ou de la traduction spécifiée dans la légende DDL, et du calcul de la formule pour créer la chaîne.<br /><br /> Si l'action a été spécifiée dans un script MDX, il n'y a pas de traductions et la légende est toujours traitée comme une expression MDX.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description conviviale de l'action.|  
|`CONTENT`|`DBTYPE_WSTR`||Expression ou contenu de l'action qui sera exécutée.|  
|`APPLICATION`|`DBTYPE_WSTR`||Nom de l'application qui sera utilisée pour exécuter l'action.|  
|`INVOCATION`|`DBTYPE_I4`||Informations sur la manière dont l'action doit être appelée :<br /><br /> -   `MDACTION_INVOCATION_INTERACTIVE` (`1`) indique une action régulière utilisée pendant les opérations normales. Il s'agit de la valeur par défaut pour cette colonne.<br />-   `MDACTION_INVOCATION_ON_OPEN` (`2`) indique que l’action doit être effectuée lorsque le cube est tout d’abord ouvert.<br />-   `MDACTION_INVOCATION_BATCH` (`4`) indique que l’action est effectuée dans le cadre d’une opération de traitement par lots ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tâche.<br /><br /> Les valeurs de l'énumération sont définies dans le fichier, Msmd.h.|  
  
 L'ensemble de lignes est trié sur `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `ACTION_NAME`.  
  
> [!NOTE]  
>  Les actions de type `MDACTION_TYPE_PROPRIETARY` doivent fournir une valeur pour la colonne `APPLICATION`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_ACTIONS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Obligatoire|  
|`ACTION_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`ACTION_TYPE`|`DBTYPE_I4`|Ce paramètre est facultatif|  
|`COORDINATE`|`DBTYPE_WSTR`|Obligatoire|  
|`COORDINATE_TYPE`|`DBTYPE_I4`|Obligatoire|  
|`INVOCATION`|`DBTYPE_I4`|(Facultative) La colonne de restriction `INVOCATION` a comme valeur par défaut la valeur de `MDACTION_INVOCATION_INTERACTIVE`. Pour récupérer toutes les actions, utilisez la valeur `MDACTION_INVOCATION_ALL` dans la colonne de restriction `INVOCATION`.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -CUBE 1<br />-DIMENSION DE 2<br /><br /> La restriction par défaut est la valeur 1.|  
  
> [!IMPORTANT]  
>  La colonne de restriction `INVOCATION` a une valeur par défaut de `MDACTION_INVOCATION_INTERACTIVE`. Tout ensemble de lignes de schéma qui ne spécifie pas explicitement une valeur pour cette colonne contient uniquement des lignes avec cette valeur. Si vous souhaitez que l'ensemble de lignes contienne l'ensemble d'actions entier, utilisez la constante `MDACTION_INVOCATION_ALL` dans la colonne de restriction `INVOCATION`.  
  
 Les applications clientes peuvent définir plusieurs `ACTION_TYPE` en utilisant l'opérateur OR.  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant répertorie les combinaisons `COORDINATE` et `COORDINATE_TYPE` valides.  
  
|Type d'objet COORDINATE|COORDINATE_TYPE|  
|----------------------------|----------------------|  
|`Cube`|`MDACTION_COORDINATE_CUBE`|  
|`Dimension`|`MDACTION_COORDINATE_DIMENSION`<br /><br /> `MDACTION_COORDINATE_LEVEL`<br /><br /> `MDACTION_COORDINATE_MEMBER`<br /><br /> `MDACTION_COORDINATE_SET`<br /><br /> `MDACTION_COORDINATE_CELL`|  
|`Hierarchy`|`MDACTION_COORDINATE_DIMENSION`|  
|`Level`|`MDACTION_COORDINATE_LEVEL`|  
|`Member`|`MDACTION_COORDINATE_MEMBER`|  
|`Set`|`MDACTION_COORDINATE_SET`|  
|`cell`|`MDACTION_COORDINATE_CELL`|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
