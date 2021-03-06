---
title: Restauration à partir de sauvegardes stockées dans Windows Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6ae358b2-6f6f-46e0-a7c8-f9ac6ce79a0e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5b00513b2522d83605f1d8ee29c9dcf68a86f625
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48154809"
---
# <a name="restoring-from-backups-stored-in-windows-azure"></a>Restauration à partir des sauvegardes stockées dans Windows Azure
  Cette rubrique présente les éléments à prendre en considération lorsque vous restaurez une base de données à l'aide d'une sauvegarde stockée dans le service de stockage d'objets Blob Windows Azure. Ceci s'applique aux sauvegardes créées à l'aide de la sauvegarde SQL Server vers l'URL ou par la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 Nous vous recommandons de consulter cette rubrique si vous avez des sauvegardes stockées dans le service de stockage d'objets blob Windows Azure et vous planifiez de les restaurer. Lisez ensuite la rubrique qui explique comment restaurer une base de données dont les sauvegardes sont locales ou sur le cloud, les deux méthodes étant identiques.  
  
## <a name="overview"></a>Vue d'ensemble  
 Les outils et les méthodes utilisés pour restaurer une base de données à partir d'une sauvegarde local s'appliquent également à la restauration d'une base de données depuis une sauvegarde sur le cloud.  Les sections suivantes présentent ces considérations et les différences que vous devez connaître lorsque vous utilisez des sauvegardes stockées dans le service de stockage Blob Windows Azure.  
  
### <a name="using-transact-sql"></a>Utilisation de Transact-SQL  
  
-   Étant donné que SQL Server doit se connecter à une source externe pour récupérer les fichiers de sauvegarde, les informations d'identification SQL sont utilisées pour authentifier le compte de stockage. Par conséquent, l'instruction RESTORE nécessite l'option WITH CREDENTIAL. Pour plus d'informations, voir [SQL Server Backup and Restore with Windows Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
-   Si vous utilisez une [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour gérer vos sauvegardes dans le cloud, vous pouvez passer en revue toutes les sauvegardes disponibles dans le stockage, en utilisant la fonction système **smart_admin.fn_available_backups** . Cette fonction système retourne toutes les sauvegardes disponibles pour une base de données dans une table. Comme les résultats sont retournés dans une table, vous pouvez les filtres ou les trier. Pour plus d’informations, consultez [smart_admin.fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql).  
  
### <a name="using-sql-server-management-studio"></a>Utilisation de SQL Server Management Studio  
  
-   La tâche de restauration est utilisée pour restaurer une base de données à l'aide de SQL Server Management Studio. La page de support de sauvegarde comprend maintenant l’option **URL** pour afficher les fichiers de sauvegarde stockés dans le service de stockage d’objets blob Microsoft Azure. Vous devez également fournir les informations d'identification SQL utilisées par vous authentifier sur le compte de stockage. La grille **Jeux de sauvegarde à restaurer** est ensuite remplie avec les sauvegardes disponibles dans le stockage d’objets blob Microsoft Azure. Pour plus d’informations, consultez [Restauration à partir du stockage Microsoft Azure à l’aide de SQL Server Management Studio](sql-server-backup-to-url.md#RestoreSSMS).  
  
### <a name="optimizing-restores"></a>Optimisation des restaurations  
 Pour réduire le temps d’écriture des restaurations, ajoutez le droit d’utilisateur **Effectuer les tâches de maintenance de volume** au compte d’utilisateur SQL Server. Pour plus d’informations, consultez [Initialisation des fichiers de base de données](http://go.microsoft.com/fwlink/?LinkId=271622). Si la restauration est toujours lente avec l'initialisation instantanée des fichiers activée, examinez la taille du fichier journal sur l'instance où la base de données a été sauvegardée. Si le fichier journal est de très grande taille (plusieurs Go), il faut s'attendre à ce que la restauration soit lente. Pendant la restauration, le fichier journal doit être remis à zéro, ce qui prend beaucoup de temps.  
  
 Pour réduire les durées de restauration, il est recommandé d'utiliser des sauvegardes compressées.  Pour des tailles de sauvegarde de plus de 25 Go, utilisez l’ [utilitaire AzCopy](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx) pour un téléchargement sur le disque local, puis effectuez la restauration. Pour connaître les bonnes pratiques et obtenir des recommandations, consultez [Meilleures pratiques et dépannage de sauvegarde SQL Server vers une URL](sql-server-backup-to-url-best-practices-and-troubleshooting.md).  
  
 Vous pouvez également activer l'indicateur de trace 3051 lors de la restauration afin de générer un journal détaillé. Ce fichier journal se trouve dans le répertoire du journal et son nom est au format suivant : BackupToUrl-\<nom_instance>-\<nom_base_de_données>-action-\<PID.log>. Le fichier journal contient des informations sur chaque aller-retour dans le stockage Windows Azure, y compris le délai d'attente qui peut être utile lors du diagnostic de problèmes.  
  
### <a name="topics-on-performing-restore-operations"></a>Rubriques relatives aux procédures des opérations de restauration  
  
-   [Restaurations complètes de bases de données &#40;mode de récupération simple&#41;](complete-database-restores-simple-recovery-model.md)  
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
-   [Restaurations complètes de bases de données &#40;mode de récupération complète&#41;](complete-database-restores-full-recovery-model.md)  
  
-   [Restaurations de fichiers &#40;mode de récupération simple&#41;](file-restores-simple-recovery-model.md)  
  
-   [Restaurations de fichiers &#40;mode de récupération complète&#41;](file-restores-full-recovery-model.md)  
  
-   [Restaurations fragmentaires &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
