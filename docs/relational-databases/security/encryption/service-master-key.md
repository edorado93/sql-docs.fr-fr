---
title: Clé principale du service | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server]
- service master key [SQL Server], about service master key
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: fdf2165b76c7c3d9526995b00a608b0017a0c065
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837137"
---
# <a name="service-master-key"></a>clé principale de service
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La clé principale du service représente la racine de la hiérarchie de chiffrement de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Elle est générée automatiquement la première fois qu'il est nécessaire de chiffrer une autre clé. Par défaut, la clé principale du service est chiffrée à l'aide de l'API de protection des données (DPAPI) Windows et de la clé de la machine locale. La clé principale du service ne peut être ouverte que par le compte de service Windows sous lequel elle a été créée ou par un principal ayant accès au nom du compte de service et à son mot de passe.  
  
 La régénération ou la restauration de la clé principale du service implique le déchiffrement puis le chiffrement de la hiérarchie complète de chiffrement. À moins que l'intégrité de la clé n'ait été compromise, cette opération nécessitant de nombreuses ressources doit être planifiée pendant une période où la demande est faible.  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] utilise l’algorithme de chiffrement AES pour protéger la clé principale du service (SMK) et la clé principale de base de données (DMK). AES est un algorithme de chiffrement plus récent que 3DES, qui était utilisé dans les versions antérieures. Au terme de la mise à niveau d'une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)] vers [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les clés SMK et DMK doivent être régénérées pour mettre à niveau les clés principales vers AES. Pour plus d’informations sur la régénération de la clé SMK, consultez [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-service-master-key-transact-sql.md) et [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-master-key-transact-sql.md).  
  
## <a name="best-practice"></a>Bonne pratique  
 Sauvegardez la clé principale du service et stockez la copie sauvegardée en un lieu sûr, hors site.  
  
## <a name="related-tasks"></a>Tâches associées  
 [BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-service-master-key-transact-sql.md)  
  
 [RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/restore-service-master-key-transact-sql.md)  
  
 [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-service-master-key-transact-sql.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Hiérarchie de chiffrement](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
