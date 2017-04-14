---
title: "Planifier un package &#224; l&#39;aide de SQL Server Agent | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d389cce-05af-4e1d-b684-7bbff413c806
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# Planifier un package &#224; l&#39;aide de SQL Server Agent
  La procédure suivante fournit les étapes pour automatiser l'exécution d'un package en utilisant une étape de travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour exécuter le package.  
  
### Pour automatiser l'exécution des packages à l'aide de l'Agent SQL Server  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur laquelle vous voulez créer un travail, ou l'instance contenant le travail auquel vous voulez ajouter une étape.  
  
2.  Développez le nœud de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans l'Explorateur d'objets et effectuez l'une des tâches suivantes :  
  
    -   Pour créer un travail, cliquez avec le bouton droit sur **Travaux**, puis cliquez sur **Nouveau travail**.  
  
    -   Pour ajouter une étape à un travail existant, développez **Travaux**, cliquez avec le bouton droit sur le travail, puis cliquez sur **Propriétés**.  
  
3.  Sur la page **Général** , si vous créez un nouveau travail, fournissez un nom de travail, sélectionnez un propriétaire et une catégorie de travail, et fournissez, si vous le souhaitez, une description du travail.  
  
4.  Pour rendre le travail disponible pour la planification, sélectionnez **Activé**.  
  
5.  Pour créer une étape de travail d'un package que vous souhaitez à planifier, cliquez sur **Étapes**, puis cliquez sur **Nouveau**.  
  
6.  Pour le type d'étape de travail, sélectionnez **Package Integration Services** .  
  
7.  Dans la liste **Exécuter en tant que** , sélectionnez **Compte de service SQL Server Agent** ou sélectionnez un compte proxy ayant les informations d'identification qui seront utilisées par le travail. Pour plus d'informations sur la création d'un compte proxy, consultez [Create a SQL Server Agent Proxy](../../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
     En utilisant un compte proxy au lieu du **Compte de service SQL Server Agent** , vous pouvez résoudre les problèmes courants qui peuvent se produire lors de l'exécution d'un package à l'aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Pour plus d’informations sur ces problèmes, consultez l’article de la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] intitulé [Un package SSIS n’est pas exécuté lorsque vous appelez le package SSIS à partir d’une étape de travail de SQL Server Agent](http://support.microsoft.com/kb/918760).  
  
    > **REMARQUE :** Si le mot de passe est différent de celui des informations d’identification que le compte proxy utilise, vous devez mettre à jour le mot de passe des informations d’identification. Autrement, l'étape de travail échouera.  
  
     Pour plus d’informations sur la configuration du compte de service de l’Agent SQL Server, consultez [Définir le compte de démarrage du service pour l’Agent SQL Server &#40;Gestionnaire de configuration SQL Server&#41;](../Topic/Set%20the%20Service%20Startup%20Account%20for%20SQL%20Server%20Agent%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
8.  Dans la zone de liste **Source du package** , cliquez sur la source du package et définissez les options de l'étape de travail.  
  
     **Le tableau suivant décrit les sources de package possibles.**  
  
    |Source du package|Description|  
    |--------------------|-----------------|  
    |**Catalogue SSIS**|Packages stockés dans la base de données SSISDB. Les packages sont contenus dans les projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] déployés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
    |**SQL Server**|Packages stockés dans la base de données MSDB. Vous utilisez le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour gérer les packages.|  
    |**Magasin de packages SSIS**|Packages stockés dans le dossier par défaut sur votre ordinateur. Le dossier par défaut est *\<lecteur>*:\Program files\Microsoft SQL Server\110\DTS\Packages. Vous utilisez le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour gérer les packages.<br /><br /> Remarque : vous pouvez spécifier un dossier différent ou spécifier des dossiers supplémentaires dans le système de fichiers géré par le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , en modifiant le fichier de configuration pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Pour plus d’informations, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).|  
    |**Système de fichiers**|Packages stockés dans un dossier sur votre ordinateur local.|  
  
     **Les tableaux suivants décrivent les options de configuration disponibles pour l'étape de travail en fonction de la source du package que vous sélectionnez.**  
  
    > **IMPORTANT :** Si le package est protégé par un mot de passe, quand vous cliquez sur l’un des onglets de la page **Général** de la boîte de dialogue **Nouvelle étape de travail**, à l’exception de l’onglet **Package**, vous devez entrer le mot de passe dans la boîte de dialogue **Mot de passe du package** qui s’affiche. Sinon, le travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent n'exécute pas le package.  
  
     **Source du package**: Catalogue SSIS  
  
    |Onglet|Options|  
    |---------|-------------|  
    |**Package**|**Server**<br /><br /> Tapez ou sélectionnez le nom de l'instance de serveur de base de données qui héberge le catalogue SSIS.<br /><br /> Lorsque **Catalogue SSIS** est la source du package, vous pouvez vous connecter au serveur à l'aide d'un compte d'utilisateur Microsoft Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas disponible.|  
    ||**Package**<br /><br /> Cliquez sur le bouton de sélection (...) et sélectionnez un package.<br /><br /> Vous sélectionnez un package dans un dossier sous le nœud **Catalogues Integration Services** dans l' **Explorateur d'objets**.|  
    |**Paramètres**<br /><br /> Situés sur l'onglet **Configuration** .|L' **Assistant Conversion de projet Integration Services** vous permet de remplacer les configurations du package avec des paramètres.<br /><br /> L'onglet **Paramètres** affiche les paramètres que vous avez ajoutés lors de la conception du package, par exemple à l'aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. L'onglet affiche également les paramètres qui ont été ajoutés au package lors de la conversion du projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] du modèle de déploiement de package au modèle de déploiement de projet. Entrez les nouvelles valeurs des paramètres contenus dans le package. Vous pouvez entrer une valeur littérale ou utiliser la valeur contenue dans une variable d'environnement serveur que vous avez déjà mappée au paramètre.<br /><br /> Pour entrer la valeur littérale, cliquez sur le bouton de sélection en regard d'un paramètre. La boîte de dialogue **Modifier la valeur littérale pour l'exécution** s'affiche.<br /><br /> Pour utiliser une variable d'environnement, cliquez sur **Environnement** puis sélectionner l'environnement qui contient la variable que vous souhaitez utiliser.<br /><br /> **\*\* Important \*\*** Si vous avez mappé plusieurs paramètres et/ou propriétés du gestionnaire de connexions à des variables contenues dans plusieurs environnements, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent affiche un message d’erreur. Pour une exécution données, un package peut s'exécuter uniquement avec les valeurs contenues dans un seul environnement.<br /><br /> Pour plus d’informations sur la façon de créer un environnement serveur et de mapper une variable à un paramètre, consultez [Créer et mapper un environnement serveur](../../integration-services/packages/create-and-map-a-server-environment.md).|  
    |**Gestionnaires de connexions**<br /><br /> Situés sur l'onglet **Configuration** .|Modifiez les valeurs des propriétés du gestionnaire de connexions. Par exemple, vous pouvez modifier le nom du serveur. Les paramètres sont automatiquement générés sur le serveur SSIS pour les propriétés du gestionnaire de connexions. Pour modifier une valeur de propriété, vous pouvez entrer une valeur littérale ou utiliser la valeur contenue dans une variable d'environnement serveur que vous avez déjà mappée à la propriété du gestionnaire de connexions.<br /><br /> Pour entrer la valeur littérale, cliquez sur le bouton de sélection en regard d'un paramètre. La boîte de dialogue **Modifier la valeur littérale pour l'exécution** s'affiche.<br /><br /> Pour utiliser une variable d'environnement, cliquez sur **Environnement** puis sélectionner l'environnement qui contient la variable que vous souhaitez utiliser.<br /><br /> **\*\* Important \*\*** Si vous avez mappé plusieurs paramètres et/ou propriétés du gestionnaire de connexions à des variables contenues dans plusieurs environnements, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent affiche un message d’erreur. Pour une exécution données, un package peut s'exécuter uniquement avec les valeurs contenues dans un seul environnement.<br /><br /> Pour plus d’informations sur la façon de créer un environnement serveur et de mapper une variable à une propriété du gestionnaire de connexions, consultez [Créer et mapper un environnement serveur](../../integration-services/packages/create-and-map-a-server-environment.md).|  
    |**Avancé**<br /><br /> Situés sur l'onglet **Configuration** .|Configurez les paramètres supplémentaires suivants pour l’exécution du package :|  
    ||**Substitutions de propriété**:<br /><br /> Cliquez sur **Ajouter** pour entrer une nouvelle valeur de propriété de package, spécifiez le chemin d'accès de la propriété, et indiquez si la valeur de la propriété est sensible. Le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] chiffre les données sensibles. Pour modifier ou supprimer des paramètres de propriété, cliquez sur une ligne dans la zone de priorités **Propriété** puis cliquez sur **Modifier** ou sur **Supprimer**. Vous pouvez trouver le chemin de la propriété en procédant de l’une des façons suivantes :<br /><br /> - Copiez le chemin de la propriété à partir du fichier de configuration XML (\*.dtsconfig). Le chemin d'accès est répertorié dans la section Configuration du fichier, comme valeur de l'attribut Path. Voici un exemple de chemin d’accès de la propriété MaximumErrorCount : \Package.Properties[MaximumErrorCount]<br /><br /> - Exécutez **l’Assistant Configuration de package** et copiez les chemins des propriétés à partir de la dernière page **Fin de l’Assistant**. Vous pouvez ensuite quitter l'Assistant.<br /><br /> <br /><br /> Remarque : l’option **Substitutions de propriété** concerne des packages contenant des configurations que vous avez mises à niveau depuis une version précédente de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les packages que vous créez à l'aide de [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] et que vous déployez sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent des paramètres à la place des configurations.|  
    ||**Niveau de journalisation**<br /><br /> Sélectionnez l'un des niveaux de journalisation suivants pour l'exécution du package. Notez que le niveau de journalisation **Performances** ou **Commentaires** sélectionné peut affecter les performances de l’exécution du package.<br /><br /> **Aucun**:<br />                          La journalisation est désactivée. Seul l'état d'exécution du package est enregistré.<br /><br /> **De base**:<br />                          Tous les événements sont enregistrés, sauf les événements personnalisés et de diagnostic. Il s'agit de la valeur par défaut du niveau de journalisation.<br /><br /> **Performancess**:<br />                          Seules les statistiques de performances, et les événements OnError et OnWarning, sont enregistrés.<br /><br /> **Commentaires**:<br />                          Tous les événements sont enregistrés, y compris les événements personnalisés et de diagnostic.<br /><br /> Le niveau de journalisation que vous sélectionnez détermine quelles informations sont affichées dans les vues SSISDB et dans les rapports pour le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour plus d’informations, consultez [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/enable-logging-for-package-execution-on-the-ssis-server.md).|  
    ||**Vider en cas d'erreurs**<br /><br /> Déterminez si des fichiers de vidage du débogage sont générés lorsqu'une erreur se produit pendant l'exécution du package. Les fichiers contiennent des informations sur l'exécution du package qui peuvent vous aider à résoudre les problèmes d'exécution. Quand vous sélectionnez cette option et qu’une erreur se produit pendant l’exécution, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un fichier .mdmp (fichier binaire) et un fichier .tmp (fichier texte). Par défaut, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stocke ces fichiers dans le dossier *\<lecteur>:*\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps.|  
    ||**Runtime 32 bits**<br /><br /> Indiquez si le package est exécuté à l’aide de la version 32 bits de l’utilitaire dtexec sur un ordinateur 64 bits contenant une version 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.<br /><br /> Il peut être nécessaire d'exécuter le package à l'aide de la version 32 bits de dtexec si, par exemple, le package utilise un fournisseur OLE DB natif qui n'est pas disponible en version 64 bits. Pour plus d'informations, consultez [Considérations 64 bits pour Integration Services](http://msdn.microsoft.com/library/ms141766\(SQL.105\).aspx).<br /><br /> Par défaut, lorsque vous sélectionnez le type d'étape de travail **Package SQL Server Integration Services** , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent exécute le package à l'aide de la version de l'utilitaire dtexec qui est appelée automatiquement par le système. Le système appelle la version 32 bits ou 64 bits de l'utilitaire selon le processeur de l'ordinateur, et de la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent qui s'exécute sur l'ordinateur.|  
  
     **Source du package**: SQL Server, Magasin de packages SSIS ou Système de fichiers  
  
     Plusieurs options que vous pouvez définir pour les packages stockées dans SQL Server, le magasin de packages SSIS ou le système de fichiers correspondent aux options de ligne de commande de l’utilitaire d’invite de commandes **dtexec**. Pour plus d’informations sur l’utilitaire et les options de la ligne de commande, consultez [Utilitaire dtexec](../../integration-services/packages/dtexec-utility.md).  
  
    |Onglet|Options|  
    |---------|-------------|  
    |**Package**<br /><br /> Voici les options de l'onglet pour les packages stockés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou dans le magasin de packages d' [!INCLUDE[ssIS](../../includes/ssis-md.md)] .|**Server**<br /><br /> Tapez ou sélectionnez le nom de l'instance de serveur de base de données pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou pour le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
    ||**Utiliser l'authentification Windows**<br /><br /> Sélectionnez cette option pour la connexion au serveur à l'aide d'un compte d'utilisateur Microsoft Windows.|  
    ||**Authentification SQL Server**<br /><br /> Quand un utilisateur se connecte avec un nom d’accès et un mot de passe spécifiés à partir d’une connexion non autorisée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réalise l’authentification en vérifiant si un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été défini et si le mot de passe spécifié correspond à celui enregistré précédemment. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas trouver le compte de connexion, l'authentification échoue et l'utilisateur reçoit un message d'erreur.|  
    ||**Nom d'utilisateur**|  
    ||**Mot de passe**|  
    ||**Package**<br /><br /> Cliquez sur le bouton de sélection et sélectionnez le package.<br /><br /> Vous sélectionnez un package dans un dossier sous le nœud **Packages stockés** dans l' **Explorateur d'objets**.|  
    |**Package**<br /><br /> Voici les options de l'onglet pour les packages stockés dans le système de fichiers.|**Package**<br /><br /> Tapez le chemin d'accès complet du fichier de package, ou cliquez sur le bouton pour sélectionner le package.|  
    |**Configurations**|Ajoutez un fichier de configuration XML pour exécuter le package avec une configuration spécifique. Utilisez une configuration de package pour mettre à jour les valeurs des propriétés du package au moment de l'exécution.<br /><br /> Cette option correspond à l’option **/ConfigFile** de **dtexec**.<br /><br /> Pour comprendre le fonctionnement de l'application des configurations de package, consultez [Package Configurations](../../integration-services/packages/package-configurations.md). Pour plus d'informations sur la création d'un configuration de package, consultez [Create Package Configurations](../../integration-services/packages/create-package-configurations.md).|  
    |**Fichiers de commandes**|Spécifiez les autres options que vous souhaitez exécuter avec **dtexec**, dans un fichier distinct.<br /><br /> Par exemple, vous pouvez inclure un fichier qui contient l’option /Dump *errorcode* pour générer des fichiers de vidage du débogage quand un ou plusieurs événements spécifiques se produisent pendant l’exécution du package.<br /><br /> Vous pouvez exécuter un package avec des ensembles d'options différents en créant plusieurs fichiers et en spécifiant le fichier approprié à l'aide de l'option **Fichiers de commandes** .<br /><br /> L’option **Fichiers de commandes** correspond à l’option **/CommandFile** de **dtexec**.|  
    |**Sources de données**|Affichez les gestionnaires de connexions contenus dans le package. Pour modifier une chaîne de connexion, cliquez sur le gestionnaire de connexions et cliquez sur la chaîne de connexion.<br /><br /> Cette option correspond à l’option **/Connection** de **dtexec**.|  
    |**Options d'exécution**|**Mettre le package en échec en cas d'avertissements de validation**<br /> Indique si un avertissement est considéré une erreur. Si vous sélectionnez cette option et un avertissement se produit pendant la validation, le package échoue pendant la validation. Cette option correspond à l’option **/WarnAsError** de **dtexec**.<br /><br /> **Valider le package sans l'exécuter**<br /> Indique si l'exécution du package s'arrête après la phase de validation, sans exécuter effectivement le package. Cette option correspond à l’option **/Validate** de **dtexec**.<br /><br /> **Remplacer la propriété MacConcurrentExecutables**<br /> Spécifie le nombre d'exécutables que le package peut exécuter simultanément. La valeur -1 signifie que le package peut exécuter simultanément un nombre maximal de fichiers exécutables égal au nombre total de processeurs sur l'ordinateur exécutant le package, plus deux. Cette option correspond à l’option **/MaxConcurrent** de **dtexec**.<br /><br /> **Activer les points de contrôle de package**<br /> Indique si le package utilise des points de contrôle pendant l'exécution du package. Pour plus d'informations, consultez [Restart Packages by Using Checkpoints](../../integration-services/packages/restart-packages-by-using-checkpoints.md).<br /><br /> Cette option correspond à l’option **/CheckPointing** de **dtexec**.<br /><br /> **Substituer les options de redémarrage**<br /> Indique si une nouvelle valeur est définie pour la propriété **CheckpointUsage** du package. Sélectionnez une valeur dans la zone de liste **Option de redémarrage** .<br /><br /> Cette option correspond à l’option **/Restart** de **dtexec**.<br /><br /> **Utiliser le runtime 32 bits**<br /> Indiquez si le package est exécuté à l’aide de la version 32 bits de l’utilitaire dtexec sur un ordinateur 64 bits contenant une version 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.<br /><br /> Il peut être nécessaire d'exécuter le package à l'aide de la version 32 bits de dtexec si, par exemple, le package utilise un fournisseur OLE DB natif qui n'est pas disponible en version 64 bits. Pour plus d'informations, consultez [Considérations 64 bits pour Integration Services](http://msdn.microsoft.com/library/ms141766\(SQL.105\).aspx).<br /><br /> Par défaut, lorsque vous sélectionnez le type d'étape de travail **Package SQL Server Integration Services** , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent exécute le package à l'aide de la version de l'utilitaire dtexec qui est appelée automatiquement par le système. Le système appelle la version 32 bits ou 64 bits de l'utilitaire selon le processeur de l'ordinateur, et de la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent qui s'exécute sur l'ordinateur.|  
    |**Journalisation**|Associez un fournisseur d'informations à l'exécution du package.<br /><br /> **Module fournisseur d'informations SSIS pour les fichiers texte**<br /> Écrit les entrées du journal dans des fichiers texte ASCII<br /><br /> **Module fournisseur d'informations SSIS pour SQL Server**<br /> Écrit les entrées du journal dans la table sysssislog de la base de données MSDB.<br /><br /> **Module fournisseur d'informations SSIS pour SQL Server Profiler**<br /> Écrit des traces que vous pouvez afficher à l'aide de SQL Server Profiler.<br /><br /> **Module fournisseur d'informations SSIS pour le journal d'événements Windows**<br /> Écrit des entrées dans le journal Application du journal des événements Windows.<br /><br /> **Module fournisseur d'informations SSIS pour les fichiers XML**<br /> Écrit des fichiers journaux dans un fichier XML.<br /><br /> Pour le fichier texte, le fichier XML et les fournisseurs d'informations de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler, sélectionnez les gestionnaires de connexions des fichiers contenus dans le package. Pour le fournisseur d'informations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sélectionnez un gestionnaire de connexions OLE DB contenu dans le package.<br /><br /> Cette option correspond à l’option **/Logger** de **dtexec**.|  
    |**Valeurs définies**|Substituez un paramètre de propriété du package. Dans la zone **Propriétés** , entrez des valeurs dans les colonnes **Chemin d'accès de la propriété** et **Valeur** . Après avoir entré les valeurs d'une propriété, une ligne vide apparaît dans la zone **Propriétés** et vous permet d'entrer des valeurs pour une autre propriété.<br /><br /> Pour supprimer une propriété de la zone Propriétés, cliquez sur la ligne puis cliquez sur **Supprimer**.<br /><br /> Vous pouvez trouver le chemin de la propriété en procédant de l’une des façons suivantes :<br /><br /> - Copiez le chemin de la propriété à partir du fichier de configuration XML (\*.dtsconfig). Le chemin d'accès est répertorié dans la section Configuration du fichier, comme valeur de l'attribut Path. Voici un exemple de chemin d’accès de la propriété MaximumErrorCount : \Package.Properties[MaximumErrorCount]<br /><br /> - Exécutez **l’Assistant Configuration de package** et copiez les chemins des propriétés à partir de la dernière page **Fin de l’Assistant**. Vous pouvez ensuite quitter l'Assistant.|  
    |**Vérification**|**Exécuter uniquement les packages signés**<br /> Indique si la signature du package est vérifiée. Si le package n'est pas signé ou si la signature n'est pas valide, le package échoue. Cette option correspond à l’option **/VerifySigned** de **dtexec**.<br /><br /> **Vérifier la version du package**<br /> Indique si le numéro de build du package est vérifié par rapport au numéro de build entré dans la zone **Build** en regard de cette option. En cas de non-concordance, le package ne s'exécute pas. Cette option correspond à l’option **/VerifyBuild** de **dtexec**.<br /><br /> **Vérifier l'ID de package**<br /> Indique si le GUID du package est valide, en le comparant à l'ID de package entré dans la zone **ID du package** en regard de cette option. Cette option correspond à l’option **/VerifyPackageID** de **dtexec**.<br /><br /> **Vérifier l'ID de version**<br /> Indique si le GUID de la version est valide, en le comparant à l'ID de version entré dans la zone **ID de version** en regard de cette option. Cette option correspond à l’option **/VerifyVersionID** de **dtexec**.|  
    |**Ligne de commande**|Modifiez les options de ligne de commande de l'utilitaire dtexec. Pour plus d'informations sur les options, consultez [dtexec Utility](../../integration-services/packages/dtexec-utility.md).<br /><br /> **Restaurer les options d'origine**<br /> Utilisez les options de ligne de commande que vous avez définies sous les onglets **Package**, **Configurations**, **Fichiers de commandes**, **Sources de données**, **Options d’exécution**, **Journalisation**, **Valeurs définies** et **Vérification** de la boîte de dialogue **Propriétés de travail**.<br /><br /> **Modifier la commande manuellement**<br /> Entrez les options de ligne de commande supplémentaires dans la zone **Ligne de commande**.<br /><br /> Avant de cliquer sur **OK** pour enregistrer les modifications apportées à l'étape du travail, vous pouvez supprimer toutes les autres options que vous avez tapées dans la zone **Ligne de commande** en cliquant sur **Restaurer les options d'origine**.<br /><br /> **\*\* Conseil \*\*** Copiez la ligne de commande dans une fenêtre d’invite de commandes, ajoutez `dtexec`, puis exécutez le package à partir de la ligne de commande. Il s’agit d’un moyen simple de générer le texte dans la ligne de commande.|  
  
9. Cliquez sur **OK** pour enregistrer les paramètres et fermer la boîte de dialogue **Nouvelle étape de travail** .  
  
    > **REMARQUE :** Pour les packages enregistrés dans le **Catalogue SSIS**, le bouton **OK** est désactivé lorsqu’il existe un paramètre de propriété du gestionnaire de connexions, ou un autre paramètre, non résolu. Un paramètre est considéré comme non résolu lorsque vous utilisez une valeur contenue dans une variable d’environnement serveur pour définir le paramètre ou la propriété, et lorsque l’une des conditions suivantes est remplie :  
    >   
    >  La case à cocher **Environnement** sous l'onglet **Configuration** n'est pas sélectionnée.  
    >   
    >  L'environnement serveur qui contient la variable n'est pas sélectionné dans la zone de liste de l'onglet **Configuration** .  
  
10. Pour créer une planification pour une étape de travail, cliquez sur **Planifications** dans le volet **Sélectionner une page** . Pour plus d'informations sur la manière de configurer une planification, consultez [Schedule a Job](../../ssms/agent/schedule-a-job.md).  
  
    > [!TIP]  
    >  Lorsque vous nommez la planification, utilisez un nom unique et un descriptif, pour différencier plus facilement la planification des autres planifications de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## Voir aussi  
 [Exécution de projets et de packages](https://msdn.microsoft.com/library/hh213290.aspx)  
  
  