---
title: Résoudre les problèmes de SQL Server sur Linux | Microsoft Docs
description: Fournit des conseils de dépannage pour l’utilisation de SQL Server sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.openlocfilehash: 5adbd3cb58791fc38d534a64d1a76ab2e329c1bc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610496"
---
# <a name="troubleshoot-sql-server-on-linux"></a>Résoudre les problèmes de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce document décrit comment résoudre les problèmes de Microsoft SQL Server s'exécutant sur Linux ou dans un conteneur Docker. Lors du dépannage de SQL Server sur Linux, n’oubliez pas de consulter les fonctionnalités prises en charge et les limitations connues dans les [notes de publication de SQL Server sur Linux](sql-server-linux-release-notes.md).

> [!TIP]
> Pour obtenir des réponses aux questions fréquemment posées, consultez le [SQL Server sur le Forum aux questions sur Linux](sql-server-linux-faq.md).

## <a id="connection"></a> Résoudre les échecs de connexion
Si vous rencontrez des difficultés pour vous connecter à votre serveur SQL Server sous Linux, il existe quelques éléments à vérifier. 

- Vérifiez que le nom du serveur ou l’adresse IP est accessible à partir de votre ordinateur client.

   > [!TIP]
   > Pour rechercher l’adresse IP de votre ordinateur Ubuntu, vous pouvez exécuter la commande ifconfig dans l’exemple suivant :
   >
   >   ```bash
   >   sudo ifconfig eth0 | grep 'inet addr'
   >   ```
   > Pour Red Hat, vous pouvez utiliser l’adresse ip, comme dans l’exemple suivant :
   >
   >   ```bash
   >   sudo ip addr show eth0 | grep "inet"
   >   ```
   > Une exception à cette technique concerne les machines virtuelles Azure. Pour les machines virtuelles Azure, [rechercher l’adresse IP publique de la machine virtuelle dans le portail Azure](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#connect).

- Le cas échéant, vérifiez que vous avez ouvert le port SQL Server (1433 par défaut) sur le pare-feu.

- Pour les machines virtuelles Azure, vérifiez que vous avez une [règle de groupe de sécurité réseau pour le port de SQL Server par défaut](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#remote).

- Vérifiez que le nom d’utilisateur et le mot de passe ne contiennent pas de fautes de frappe, ni d'espaces, ni une casse incorrecte.

- Essayez de définir explicitement le protocole et numéro de port avec le nom du serveur comme dans l’exemple suivant : **tcp:servername, 1433**.

- Des problèmes de connectivité réseau peuvent également entraîner des délais d’attente et des erreurs de connexion. Après avoir vérifié vos informations de connexion et la connectivité réseau, recommencez l’opération.

## <a name="manage-the-sql-server-service"></a>Gérer le service SQL Server

Les sections suivantes vous montrent comment démarrer, arrêter, redémarrer et vérifier l’état du service SQL Server. 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Gérer le service mssql-server sous Red Hat Enterprise Linux (RHEL) et Ubuntu 

Vérifiez l’état du service SQL Server à l’aide de cette commande :

   ```bash
   sudo systemctl status mssql-server
   ```

Vous pouvez arrêter, démarrer ou redémarrer le service SQL Server en fonction des besoins à l’aide des commandes suivantes :

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl start mssql-server
   sudo systemctl restart mssql-server
   ```

### <a name="manage-the-execution-of-the-mssql-docker-container"></a>Gestion de l’exécution du conteneur Docker mssql

Vous pouvez obtenir l’ID d’état et le conteneur du dernier conteneur Docker SQL Server créé en exécutant la commande suivante (l’ID est sous le **ID de conteneur** colonne) :

   ```bash
   sudo docker ps -l
   ```
   
Vous pouvez arrêter ou redémarrer le service SQL Server en fonction des besoins à l’aide des commandes suivantes :
   
   ```bash
   sudo docker stop <container ID>
   sudo docker restart <container ID>
   ```

> [!TIP]
> Pour obtenir des conseils de dépannage plus pour Docker, consultez [conteneurs de résolution des problèmes de SQL Server Docker](sql-server-linux-configure-docker.md#troubleshooting).

## <a name="access-the-log-files"></a>Accéder aux fichiers journaux
   
SQL Server stocke ses journaux dans le fichier /var/opt/mssql/log/errorlog dans les installations sous Linux et Docker.
 Vous devez être en mode de 'super utilisateur' pour parcourir ce répertoire.

Le programme d’installation enregistre ici : /var/opt/mssql/setup-< horodatage qui représente l'heure d’installation> Vous pouvez parcourir les fichiers journaux des erreurs avec n’importe quel outil compatible UTF-16 tel que « vim » ou « cat » comme suit : 

   ```bash
   sudo cat errorlog
   ```

Si vous préférez, vous pouvez également convertir les fichiers vers UTF-8 pour les lire avec « more » ou « less » avec la commande suivante :
   
   ```bash
   sudo iconv –f UTF-16LE –t UTF-8 <errorlog> -o <output errorlog file>
   ```
## <a name="extended-events"></a>Événements étendus

Les événements étendus peuvent être interrogées via une commande SQL.  Plus d’informations sur les événements étendus accessibles [ici](https://technet.microsoft.com/library/bb630282.aspx):

## <a name="crash-dumps"></a>Vidages sur incident 

Recherchez les vidages dans le répertoire de journaux dans Linux. Recherchez dans le répertoire /var/opt/mssql/log les vidages Linux Core (extension .tar.gz2) ou les mini-vidages SQL (extension .mdmp)

Pour les vidages principaux 
   ```bash
   sudo ls /var/opt/mssql/log | grep .tar.gz2 
   ```

Pour les vidages sur SQL 
   ```bash
   sudo ls /var/opt/mssql/log | grep .mdmp 
   ```
   
## <a name="start-sql-server-in-minimal-configuration-or-in-single-user-mode"></a>Démarrage de SQL Server dans une Configuration minimale ou en Mode mono-utilisateur

### <a name="start-sql-server-in-minimal-configuration-mode"></a>Démarrez SQL Server en Mode Configuration minimale
Cette option est utile lorsqu'une valeur de configuration définie (espace mémoire insuffisant, par exemple) a empêché le serveur de démarrer.
  
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -f
   ```

### <a name="start-sql-server-in-single-user-mode"></a>Démarrez SQL Server en Mode mono-utilisateur
Dans certaines circonstances, vous devrez peut-être démarrer une instance de SQL Server en mode mono-utilisateur à l’aide de l’option de démarrage -m. Vous pouvez par exemple vouloir modifier les options de configuration du serveur ou rétablir une base de données maître ou une autre base de données système endommagée. Par exemple, vous pouvez vouloir modifier les options de configuration du serveur ou récupérer une base de données maître endommagée ou une autre base de données système   

Démarrez SQL Server en Mode mono-utilisateur
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m
   ```

Démarrez SQL Server en Mode mono-utilisateur avec SQLCMD
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
   ```
  
> [!WARNING]  
>  Démarrez SQL Server sous Linux avec l’utilisateur « mssql » afin d’éviter les problèmes de démarrage à l'avenir. Exemple « sudo -u mssql /opt/mssql/bin/sqlservr [OPTIONS DE DÉMARRAGE] » 

Si vous avez démarré par inadvertance SQL Server avec un autre utilisateur, vous devez changer la propriété des fichiers de base de données SQL Server pour l'attribuer à l’utilisateur 'mssql' avant de démarrer SQL Server avec systemd. Par exemple, exécutez la commande suivante pour modifier la propriété de tous les fichiers de base de données sous /var/opt/mssql sur l’utilisateur « mssql »,

   ```bash
   chown -R mssql:mssql /var/opt/mssql/
   ```

## <a name="rebuild-system-databases"></a>Reconstruire les bases de données système
En dernier recours, vous pouvez choisir de régénérer le maître, puis bases de données model vers des versions par défaut.

> [!WARNING]
> Ces étapes seront **supprimer toutes les données de système de SQL Server** que vous avez configuré ! Cela inclut des informations sur vos bases de données utilisateur (mais pas les bases de données utilisateur eux-mêmes). Elle supprime également d’autres informations stockées dans les bases de données système, y compris les éléments suivants : informations de clé principale, les certificats chargés dans master, le mot de passe de connexion SA, des informations relatives aux travaux msdb, les informations de messagerie de base de données msdb, et que les options de sp_configure. Utiliser uniquement si vous comprenez les implications !

1. Arrêt de SQL Server.

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Exécutez **sqlservr** avec la **force-setup** paramètre. 

   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr --force-setup
   ```
   
   > [!WARNING]
   > Consultez l’avertissement précédent ! En outre, vous devez exécuter en tant que le **mssql** utilisateur comme indiqué ici.

1. Une fois que vous voyez le message « Récupération est terminée », appuyez sur CTRL + C. Ceci arrêtera de SQL Server

1. Reconfigurer le mot de passe SA.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-sa-password
   ```
   
1. Démarrage de SQL Server et reconfigurer le serveur. Cela inclut les restaurer ou attacher des bases de données utilisateur.

   ```bash
   sudo systemctl start mssql-server
   ```

## <a name="improve-performance"></a>Améliorer les performances

Il existe de nombreux facteurs affectent les performances, notamment la conception de base de données, le matériel et des charges de travail. Si vous cherchez à améliorer les performances, commencez par consulter les meilleures pratiques dans l’article, [performances meilleures pratiques et des instructions de configuration de SQL Server sur Linux](sql-server-linux-performance-best-practices.md). Ensuite, Explorer certains des outils disponibles pour résoudre les problèmes de performances.

- [Magasin de requêtes](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [Vues de gestion dynamique (DMV) de système](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
- [Tableau de bord de performances dans SQL Server Management Studio](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)

## <a name="common-issues"></a>Problèmes courants

1. Impossible de se connecter à votre instance de SQL Server à distance.

   Consultez la section Dépannage de l’article, [se connecter à SQL Server sur Linux](#connection).

2. Erreur : Le nom d’hôte doit compter 15 caractères maximum.

   Il s’agit d’un problème connu qui se produit chaque fois que le nom de l’ordinateur sur lequel on tente d’installer le package Debian SQL Server est supérieur à 15 caractères. Il n’existe actuellement aucune solution de contournement autre que la modification du nom de l’ordinateur. Une façon d’effectuer cette opération est de modifier le fichier de nom d’hôte et de redémarrer l’ordinateur. Le [guide du site Web](http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/) suivant explique cela en détail.

3. Réinitialiser le mot de passe système (SA) d’administration.

   Si vous avez oublié le mot de passe d’administrateur système ou que vous devez le réinitialiser pour une raison quelconque, procédez comme suit.

   > [!NOTE]
   > Les étapes suivantes arrêter temporairement le service SQL Server.

   Connectez vous au terminal de l’ordinateur hôte, exécutez les commandes suivantes, suivez les invites pour réinitialiser le mot de passe SA :

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. Utiliser des caractères spéciaux dans le mot de passe.

   Si vous utilisez certains caractères dans le mot de passe de connexion SQL Server, vous devrez peut-être caractère d’échappement avec une barre oblique inverse lorsque vous les utilisez dans une commande de Linux dans le terminal. Par exemple, vous devez échapper le symbole dollar ($) à chaque fois que vous l’utilisez dans un script d’interface de commande/Terminal Server :

   Ne fonctionne pas :

   ```bash
   sudo sqlcmd -S myserver -U sa -P Test$$
   ```

   Fonctionne :

   ```bash
   sqlcmd -S myserver -U sa -P Test\$\$
   ```

   Ressources : [caractères spéciaux](http://tldp.org/LDP/abs/html/special-chars.html)
   [Escaping](http://tldp.org/LDP/abs/html/escapingsection.html)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
