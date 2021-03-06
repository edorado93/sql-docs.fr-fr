---
title: Vue d’ensemble de SQL Server sur Linux | Microsoft Docs
description: Cet article décrit comment SQL Server s’exécute sur Linux et fournit des informations sur comment en savoir plus.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.openlocfilehash: 8b8ee30d255382981a65a661ed0a080e39e4577a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617107"
---
# <a name="sql-server-on-linux"></a>SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: moniker range="= sql-server-2017 || = sqlallproducts-allversions"
À partir de SQL Server 2017, SQL Server s’exécute sur Linux. C'est le même moteur de base de données que MSSQL Server, avec de nombreuses fonctionnalités et des services équivalents, quel que soit votre système d’exploitation.
::: moniker-end

::: moniker range=">= sql-server-ver15 || >= sql-server-linux-ver15"
SQL Server 2019 CTP 2.0 s’exécute sur Linux. C'est le même moteur de base de données que MSSQL Server, avec de nombreuses fonctionnalités et des services équivalents, quel que soit votre système d’exploitation. Pour en savoir plus sur cette version, consultez [quelles sont les nouveautés dans SQL Server 2019 CTP 2.0 pour Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sqllinux).
::: moniker-end

::: moniker range="= sql-server-2017"
> [!TIP]
> [SQL Server 2019 CTP 2.0](sql-server-linux-overview.md?view=sql-server-ver15) a été publié ! Pour découvrir les nouveautés dans la dernière version de Linux, consultez [quelles sont les nouveautés dans SQL Server 2019 CTP 2.0 pour Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sqllinux).
::: moniker-end

::: moniker range="= sql-server-linux-2017"
> [!TIP]
> [SQL Server 2019 CTP 2.0](sql-server-linux-overview.md?view=sql-server-linux-ver15) a été publié ! Pour découvrir les nouveautés dans la dernière version de Linux, consultez [quelles sont les nouveautés dans SQL Server 2019 CTP 2.0 pour Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-linux-ver15#sqllinux).
::: moniker-end

::: moniker range="= sqlallproducts-allversions"
> [!TIP]
> SQL Server 2019 CTP 2.0 a été publié ! Pour découvrir les nouveautés dans la dernière version de Linux, consultez [quelles sont les nouveautés dans SQL Server 2019 CTP 2.0 pour Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sqllinux).
::: moniker-end

## <a name="install"></a>Installation

Pour démarrer, installez SQL Server sur Linux en suivant l'une des sections de démarrage rapide suivantes :

- [Installation sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécuter sur Docker](quickstart-install-connect-docker.md)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker lui-même s’exécute sur plusieurs plateformes, ce qui signifie que vous pouvez exécuter l’image Docker sur Windows, Mac ou Linux.

## <a name="connect"></a>Connection

Après l’installation, connectez-vous à l’instance de SQL Server installée sur un ordinateur Linux. Vous pouvez vous connecter localement ou à distance via un large éventail d’outils et de pilotes. Les didacticiels de démarrage rapide montrent comment utiliser l'outil en ligne de commande [sqlcmd](sql-server-linux-setup-tools.md). Les autres outils possibles sont les suivants :

| Tool | Didacticiel |
|-----|-----|
| Visual Studio Code (VS Code) | [Utiliser VS Code avec SQL Server sur Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Utiliser SSMS sur Windows pour se connecter à SQL Server sur Linux](sql-server-linux-manage-ssms.md) |
| Outils de données SQL Server (SSDT) | [Utiliser SSDT avec SQL Server sur Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Explorer

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

SQL Server 2017 a le même moteur de base de données sous-jacent sur toutes les plateformes prises en charge, y compris Linux. Par conséquent, nombreuses fonctionnalités et les fonctionnalités existantes fonctionnent de la même façon sur Linux. Cette partie de la documentation expose certaines de ces fonctionnalités du point de vue Linux. Elle indique également les parties qui ont des exigences spécifiques à Linux.

Si vous êtes déjà familiarisé avec SQL Server, passez en revue les [notes de publication](sql-server-linux-release-notes.md) pour des recommandations générales et les problèmes connus pour cette version. Observez [quelles sont les nouveautés de SQL Server sur Linux](sql-server-linux-whats-new.md) ainsi que les [Nouveautés globales à SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15"

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] a le même moteur de base de données sous-jacent sur toutes les plateformes prises en charge, y compris Linux. Par conséquent, nombreuses fonctionnalités et les fonctionnalités existantes fonctionnent de la même façon sur Linux. Cette partie de la documentation expose certaines de ces fonctionnalités du point de vue Linux. Elle indique également les parties qui ont des exigences spécifiques à Linux.

Si vous êtes déjà familiarisé avec SQL Server sur Linux, passez en revue la [notes de publication](sql-server-linux-release-notes-2019.md) pour des instructions générales et les problèmes connus pour cette version. Examinez ensuite [quelles sont les nouveautés de la version préliminaire de SQL Server 2019 sur Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15).

::: moniker-end

<!--SQL Server All Versions-->
::: moniker range="=sqlallproducts-allversions"

SQL Server 2017 et [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] ont le même moteur de base de données sous-jacent sur toutes les plateformes prises en charge, y compris Linux. Par conséquent, nombreuses fonctionnalités et les fonctionnalités existantes fonctionnent de la même façon sur Linux. Cette partie de la documentation expose certaines de ces fonctionnalités du point de vue Linux. Elle indique également les parties qui ont des exigences spécifiques à Linux.

Si vous êtes déjà familiarisé avec SQL Server sur Linux, passez en revue les notes de publication :

- [Notes de publication de SQL Server 2017](sql-server-linux-release-notes.md)
- [Notes de publication de version préliminaire de SQL Server 2019](sql-server-linux-release-notes-2019.md)

Examinez ensuite quelles sont les nouveautés :

- [Quelles sont les nouveautés de SQL Server 2017](sql-server-linux-whats-new.md)
- [Nouveautés de la version préliminaire de SQL Server 2019 sur Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sqllinux)

::: moniker-end

> [!TIP]
> Pour obtenir des réponses aux questions fréquemment posées, consultez le [SQL Server sur le Forum aux questions sur Linux](sql-server-linux-faq.md).

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
