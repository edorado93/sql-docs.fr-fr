---
title: Historique d’ADO | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, what's new
ms.assetid: 667673f2-3151-432b-894a-3fc60b704ea4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e00a1ff652e3f1463d37e2cd5457965968b4ba4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709557"
---
# <a name="ado-features-for-each-release"></a>Fonctionnalités d’ADO pour chaque version
Cette rubrique répertorie les nouvelles fonctionnalités introduites par chaque version de ADO, ADO MD et ADOX.

## <a name="ado-60"></a>ADO 6.0
 ADO 6.0 est inclus dans Windows Vista dans le cadre de Windows Data Access Components (Windows DAC) 6.0. ADO 6.0 est fonctionnellement équivalent à ADO 2.8.

## <a name="ado-28"></a>ADO 2.8
 ADO 2.8 a été inclus dans Windows XP et Windows Server 2003, dans le cadre de la Microsoft Data Access composants (MDAC) 2.8. Une version redistribuable de MDAC 2.8 est également disponible ; Notez que cette version redistribuable doit uniquement être installée sur Windows 2000. ADO 2.8 résout plusieurs problèmes liés à la sécurité :

 *Accès de disque dur n’est pas autorisé en dehors d’une zone de confiance.*
Dans les sites non approuvés qui implique de script entre domaines, les opérations suivantes sont désactivées : **Stream.SaveToFile**, **Stream.LoadFromFile**, **Recordset.Save**, et **Recordset.Open**, utilisé conjointement avec le **adCmdFile** indicateur ou avec le fournisseur Microsoft OLE DB persistance (MSPersist).

 **Recordset.Open** *,***Recordset.Save** *,***Stream.SaveToFile** *, et* **Stream.LoadFromFile***fonctionnent sur les fichiers physiques uniquement.* 
Ces méthodes maintenant vérifier que les descripteurs de fichiers pointent vers les fichiers physiques uniquement.

 **Recordset.ActiveCommand***retourne une erreur lorsqu’elle est appelée à partir d’une page HTML/ASP.* 
Cela empêche le **commande** objet à partir de l’utilisation abusive.

 *Le nombre de***Recordsets***retourné par imbriquée***forme***commande a une limite supérieure.* 
Une commande imbriquée shape renvoie désormais un maximum de 512 **Recordsets**. Cela signifie qu’un **forme** n’est plus possible d’imbriquer des commandes à n’importe quelle profondeur. Au lieu de cela, la profondeur maximale de niveau est 512, si chaque commande génère un seul (enfant) **Recordset**. If, n’importe quel niveau, un **forme** commande retourne plusieurs **Recordsets**, le niveau maximal de profondeur sera inférieure à 512.

## <a name="ado-27"></a>ADO 2.7
 *prise en charge de la plateforme 64 bits* ADO 2.7 introduit la prise en charge des processeurs 64 bits.

## <a name="ado-26"></a>ADO 2.6
 **CubDef.GetSchemaObject***méthode* à partir de ADO 2.6, les objets ADO MD peuvent être récupérées à l’aide des noms uniques, comme spécifié par le [UniqueName, propriété (ADO MD)](../../ado/reference/ado-md-api/uniquename-property-ado-md.md).   Les noms des objets parents n’êtes pas obligé d’être connu, et les collections de parent n’êtes pas obligé d’être renseignée pour récupérer un objet de schéma. Consultez [getschemaobject, méthode (ADO MD)](../../ado/reference/ado-md-api/getschemaobject-method-ado-md.md).

 *Commande flux* le **commande** objet prend en charge des commandes dans le format de flux comme alternative à l’utilisation de la **CommandText** propriété. Le [CommandStream, propriété (ADO)](../../ado/reference/ado-api/commandstream-property-ado.md) peut être utilisé pour spécifier les modèles XML ou codes en tant que le **commande** d’entrée avec le fournisseur Microsoft OLE DB pour SQL Server.

 **Dialecte***propriété* [dialecte](../../ado/reference/ado-api/dialect-property.md) est une nouvelle propriété qui définit la syntaxe et les règles générales que le fournisseur utilise pour analyser la chaîne ou le flux.  

 **Command.Execute***méthode* le [exécuter la méthode](../../ado/reference/ado-api/execute-method-ado-command.md) de ADO **commande** objet a été amélioré pour utiliser des flux pour l’entrée et de sortie.  

 *Champ statusvalues* si l’utilisateur rencontre une erreur DB_E_ERRORSOCCURRED lorsque vous modifiez un **champ** d’un **Recordset**, ADO remplira maintenant le **Field.Status**propriété avec les informations d’état approprié afin que l’utilisateur aura plus d’informations sur la cause du problème. Consultez [Status, propriété (objet Field ADO)](../../ado/reference/ado-api/status-property-ado-field.md).

 **NamedParameters***propriété* [NamedParameters](../../ado/reference/ado-api/namedparameters-property-ado.md) est une nouvelle propriété de la **commande** nommé de l’objet qui indique que le fournisseur doit utiliser. paramètres.  

 *Jeux de résultats dans des flux* ADO peut retourner des jeux de résultats à partir d’une source de données dans un **Stream**, au lieu d’un **Recordset** objet. À l’aide de la dernière version du fournisseur Microsoft OLE DB pour SQL Server, vous pouvez obtenir des résultats XML à partir du fournisseur en exécutant une requête « Pour le XML ». Un **Stream** qui reçoit le jeu de résultats peut être ouvert avec une commande « Pour XML » comme source. Consultez [récupération des jeux de résultats en flux](../../ado/guide/data/retrieving-resultsets-into-streams.md).

 *Jeu de résultats de ligne unique* ADO le **enregistrement** objet peut maintenant être ouverts sur une chaîne de commande ou **commande** objet qui retourne une ligne de données à partir du fournisseur. Cela entraîne une amélioration des performances avec les fournisseurs MDAC 2.6. Consultez [Open, méthode (objet Record ADO)](../../ado/reference/ado-api/open-method-ado-record.md).

## <a name="ado-25"></a>ADO 2.5
 **Enregistrement** *objet* ADO 2.5 présente le **enregistrement** objet pour représenter et gérer une ligne à partir d’un **Recordset** ou un fournisseur de données ou un objet qui encapsule un des données semi-structurées, comme un fichier ou répertoire.

 **Stream** *objet* ADO 2.5 introduit également la **Stream** objet pour représenter un flux de données binaire ou texte.

 *Liaison d’URL* ADO 2.5 présente l’utilisation d’une URL, comme alternative à un texte de chaîne et la commande de connexion, pour nommer des objets de magasin de données. Une URL peut être utilisée avec le **connexion** et **Recordset** des objets, comme avec la nouvelle **enregistrement** et **Stream** objets.

 *Les fournisseurs de données prenant en charge la liaison d’URL* ADO 2.5 prend en charge les fournisseurs OLE DB qui reconnaissent les schémas d’URL. Cela inclut le fournisseur OLE DB pour la publication Internet qui accède au système de fichiers Windows 2000 et identifie le schéma HTTP existant.
