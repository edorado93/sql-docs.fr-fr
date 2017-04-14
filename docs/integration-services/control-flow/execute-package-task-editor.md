---
title: "&#201;diteur de t&#226;che d&#39;ex&#233;cution de package | Microsoft Docs"
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
  - "sql13.dts.designer.executepackagetask.package.f1"
  - "sql13.dts.designer.executepackagetask.parameter.F1"
  - "sql13.dts.designer.executepackagetask.general.f1"
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# &#201;diteur de t&#226;che d&#39;ex&#233;cution de package
  Utilisez l'Éditeur de tâche d'exécution de package pour configurer la tâche d'exécution de package. La tâche d'exécution de package étend les fonctionnalités d'entreprise de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en permettant à des packages d'exécuter d'autres packages au sein d'un flux de travail.  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir l'Éditeur de tâche d'exécution de package](#open)  
  
-   [Définir les options sur la page Général](#general)  
  
-   [Définir les options sur la page Package](#package)  
  
-   [Définir les options sur la page Liaisons de paramètre](#parameter)  
  
##  <a name="open"></a> Ouvrir l'Éditeur de tâche d'exécution de package  
  
1.  Ouvrez un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] qui contient une tâche d'exécution de package.  
  
2.  Cliquez avec le bouton droit sur la tâche dans le Concepteur SSIS, puis cliquez sur **Modifier**.  
  
##  <a name="general"></a> Définir les options sur la page Général  
 **Nom**  
 Fournissez un nom unique pour la tâche d'exécution de package. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Entrez une description de la tâche d'exécution de package.  
  
##  <a name="package"></a> Définir les options sur la page Package  
 **ReferenceType**  
 Sélectionnez **Référence du projet** pour les packages enfants qui sont dans le projet. Sélectionnez **Référence externe** pour les packages enfants situés en dehors du package.  
  
> [!NOTE]  
>  L’option **ReferenceType** est en lecture seule et est définie sur **Référence externe** si le projet qui contient le package n’a pas été converti en modèle de déploiement de projet. Pour plus d’informations sur la conversion, consultez [Déployer des projets sur le serveur Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
 **Mot de passe**  
 Si le package enfant s'avère protégé par un mot de passe, indiquez ce dernier ou cliquez sur le bouton représentant des points de suspension (…) afin de définir un nouveau mot de passe.  
  
 **ExecuteOutOfProcess**  
 Spécifiez si le package enfant s'exécute dans le processus du package parent ou dans un processus distinct. Par défaut, la propriété ExecuteOutOfProcess de la tâche d’exécution du package a la valeur **False**, et le package enfant s’exécute dans le même processus que le package parent. Si vous affectez la valeur **true**à cette propriété, le package enfant s'exécute dans un processus indépendant. Cela peut ralentir le lancement du package enfant. En outre, si vous avez défini la propriété sur **true**, vous ne pouvez pas déboguer le package dans une installation d’outils uniquement : vous devez installer le produit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Pour plus d’informations, consultez [Installer Integration Services](../../integration-services/install-windows/install-integration-services.md).  
  
### Options dynamiques de ReferenceType  
  
#### ReferenceType = Référence externe  
 **Emplacement**  
 Sélectionnez l'emplacement du package enfant. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**SQL Server**|Définissez l'emplacement d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Système de fichiers**|Permet de définir l'emplacement du système de fichiers.|  
  
 **Connexion**  
 Sélectionnez le type d’emplacement de stockage du package enfant.  
  
 **PackageNameReadOnly**  
 Permet d'afficher le nom du package.  
  
#### ReferenceType = Référence du projet  
 **PackageNameFromProjectReference**  
 Sélectionnez un package contenu dans le projet, qui sera le package enfant.  
  
### Options dynamiques pour la définition de l'emplacement  
  
#### Emplacement = SQL Server  
 **Connexion**  
 Sélectionnez un gestionnaire de connexions OLE DB dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes : **[Gestionnaire de connexions OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md), [Configurer le gestionnaire de connexions OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)  
  
 **PackageName**  
 Permet de saisir le nom du package enfant ou de cliquer sur le bouton représenté par des points de suspension (…) pour atteindre le package.  
  
#### Emplacement = Système de fichiers  
 **Connexion**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 **PackageNameReadOnly**  
 Permet d'afficher le nom du package.  
  
##  <a name="parameter"></a> Définir les options sur la page Liaisons de paramètre  
 Vous pouvez passer des valeurs du package parent ou du projet au package enfant. Le projet doit utiliser le modèle de déploiement de projet et le package enfant doit être contenu dans le même projet qui contient le package parent.  
  
 Pour plus d’informations sur la conversion de projets en modèle de déploiement de projet, consultez [Déployer des projets sur le serveur Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
 **Paramètre de package enfant**  
 Entrez ou sélectionnez un nom pour le paramètre de package enfant.  
  
 **Variable ou paramètre de liaison**  
 Sélectionnez le paramètre ou la variable contenant la valeur que vous souhaitez transmettre au package enfant.  
  
 **Ajouter**  
 Cliquez pour mapper un paramètre ou une variable à un paramètre de package enfant.  
  
 **Supprimer**  
 Cliquez pour supprimer un mappage entre un paramètre ou une variable et un paramètre de package enfant.  
  
  