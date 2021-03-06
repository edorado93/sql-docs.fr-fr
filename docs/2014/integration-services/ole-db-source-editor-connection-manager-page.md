---
title: Éditeur de Source OLE DB (Page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.connection.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 53699902-8699-4547-b56b-a5b2079e98b6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c25e36d44b4b088bb2874039d4c292d76759da73
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172979"
---
# <a name="ole-db-source-editor-connection-manager-page"></a>Éditeur de source OLE DB (page Gestionnaire de connexions)
  La page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source OLE DB** vous permet de sélectionner le gestionnaire de connexions OLE DB pour la source. Cette page vous permet également de sélectionner une table ou une vue à partir de la base de données.  
  
> [!NOTE]  
>  Pour charger des données à partir d’une source de données qui utilise [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007, utilisez une source OLE DB. Vous ne pouvez pas utiliser une source Excel pour charger des données à partir d'une source de données Excel 2007. Pour plus d’informations, consultez [Configurer le gestionnaire de connexions OLE DB](configure-ole-db-connection-manager.md).  
>   
>  Pour charger des données à partir d'une source de données qui utilise [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 ou une version antérieure, utilisez une source Excel. Pour plus d’informations, consultez [Éditeur de source Excel &#40;page Gestionnaire de connexions&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md).  
  
> [!NOTE]  
>  Le `CommandTimeout` propriété de la source OLE DB n’est pas disponible dans le **éditeur de Source OLE DB**, mais peut être définie à l’aide de la **éditeur avancé**. Pour plus d’informations sur cette propriété, consultez la section sur la source Excel dans [Propriétés personnalisées OLE DB](data-flow/ole-db-custom-properties.md).  
  
 Pour en savoir plus sur la source OLE DB, consultez [Source OLE DB](data-flow/ole-db-source.md).  
  
## <a name="open-the-ole-db-source-editor-connection-manager-page"></a>Ouvrir l'Éditeur de source OLE (page Gestionnaire de connexions)  
  
1.  Ajoutez la source OLE DB au package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur le composant de la source, puis cliquez sur **Modifier**.  
  
3.  Cliquez sur **Gestionnaire de connexions**.  
  
## <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une nouvelle connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** .  
  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Option|Description|  
|------------|-----------------|  
|Table ou vue|Permet de récupérer les données d'une table ou d'une vue dans la source de données OLE DB.|  
|Variable de nom de table ou de vue|Spécifiez le nom de la table ou de la vue dans une variable.<br /><br /> **Informations connexes :** [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md)|  
|Commande SQL|Récupérez les données de la source de données OLE DB à l'aide d'une requête SQL.|  
|Commande SQL à partir d'une variable|Spécifiez le texte de la requête SQL dans une variable.|  
  
 **Aperçu**  
 Affichez un aperçu des résultats à partir de la boîte de dialogue **Vue de données** . Le mode**Aperçu** peut afficher jusqu’à 200 lignes.  
  
> [!NOTE]  
>  Lorsque vous affichez l'aperçu des données, les colonnes ayant un type CLR défini par l'utilisateur ne contiennent pas de données. Les valeurs \<valeur trop grande pour être affichée> ou System.Byte[] s’affichent à la place. La première s’affiche lorsque le fournisseur SQL OLE DB accède à la source de données, la seconde lorsque vous utilisez le fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="data-access-mode-dynamic-options"></a>Options dynamiques du mode d'accès aux données  
  
### <a name="data-access-mode--table-or-view"></a>Mode d'accès aux données = Table ou vue  
 **Nom de la table ou de la vue**  
 Sélectionnez le nom de la table ou de la vue dans la liste de celles qui sont disponibles dans la source de données.  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Mode d'accès aux données = Variable de nom de table ou de vue  
 **Nom de la variable**  
 Sélectionnez la variable qui contient le nom de la table ou de la vue.  
  
### <a name="data-access-mode--sql-command"></a>Mode d'accès aux données = Commande SQL  
 **Texte de la commande SQL**  
 Entrez le texte d’une requête SQL, générez la requête en cliquant sur **Générer une requête**ou recherchez le fichier qui contient le texte de la requête en cliquant sur **Parcourir**.  
  
 **Paramètres**  
 Si vous avez entré une requête paramétrable en spécifiant ? comme espace réservé de paramètre dans le texte de la requête, utilisez la boîte de dialogue **Définition des paramètres de la requête** pour mapper des paramètres d’entrée de la requête à des variables du package.  
  
 **Build query**  
 Utilisez la boîte de dialogue **Générateur de requêtes** pour construire la requête SQL visuellement.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir** , localisez le fichier qui contient le texte de la requête SQL.  
  
 **Analyser la requête**  
 Vérifiez la syntaxe du texte de la requête.  
  
### <a name="data-access-mode--sql-command-from-variable"></a>Mode d'accès aux données = Commande SQL à partir d'une variable  
 **Nom de la variable**  
 Sélectionnez la variable qui contient le texte de la requête SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de Source OLE DB &#40;Page colonnes&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md)   
 [Éditeur de Source OLE DB &#40;Page sortie d’erreur&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md)   
 [Extraire des données à l’aide de la Source OLE DB](data-flow/extract-data-by-using-the-ole-db-source.md)   
 [Gestionnaire de connexions OLE DB](connection-manager/ole-db-connection-manager.md)  
  
  
