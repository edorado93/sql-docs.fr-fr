---
title: Comparer et synchroniser des données d'une ou plusieurs tables avec des données d'une base de données de référence | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 96d743b0-b69a-45bb-ae0e-62103dca76e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 23b3057a23737eb43206f9615ce2f83bad6f5610
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745107"
---
# <a name="compare-and-synchronize-data-in-one-or-more-tables-with-data-in-a-reference-database"></a>Comparer et synchroniser des données d'une ou plusieurs tables avec des données d'une base de données de référence
Vous pouvez comparer les données d'une base de données *source* et d'une base de données *cible* et spécifier quelles tables doivent être comparées. Vous pouvez examiner les données et décider quels changements synchroniser. Vous pouvez ensuite soit mettre à jour la cible pour synchroniser les bases de données, soit exporter le script de mise à jour dans l'éditeur Transact\-SQL ou dans un fichier.  
  
Par exemple, vous pouvez synchroniser des bases de données pour mettre à jour un serveur de mise en lots avec une copie des données de production. Vous pouvez également synchroniser une ou plusieurs tables pour les remplir avec des données de référence d'une autre base de données. En outre, vous pouvez comparer les données avant et après l'exécution de tests comme une sorte de contrôle supplémentaire.  
  
Vous pouvez comparer les données dans deux bases de données, mais vous ne pouvez pas spécifier un fichier de projet de base de données ou un fichier .dacpac pour la comparaison car il ne contient pas de données.  
  
Cette section contient les rubriques suivantes :  
  
-   [Procédure : comparer et synchroniser les données de deux bases de données](../ssdt/how-to-compare-and-synchronize-the-data-of-two-databases.md)  
  
-   [Procédure : afficher les différences entre les données](../ssdt/how-to-view-data-differences.md)  
  
## <a name="requirements"></a>Spécifications  
Lorsque vous comparez des données dans une table ou une vue, la table ou la vue dans la base de données source doit partager plusieurs attributs avec une table ou une vue dans la base de données cible. Les tables et les vues qui ne répondent pas aux critères suivants ne sont pas comparées et n'apparaissent pas dans la deuxième page de l'Assistant **Nouvelle comparaison de données** :  
  
-   Les tables doivent avoir des noms de colonnes correspondants qui contiennent des types de données compatibles.  
  
    Les noms des tables, vues et propriétaires respectent la casse.  
  
-   Les tables doivent avoir les mêmes clé primaire, index unique ou contrainte unique.  
  
-   Les vues doivent posséder le même index cluster unique.  
  
-   Vous pouvez comparer une table avec une vue uniquement si elles ont le même nom.  
  
Chaque objet a une clé ou un index qui détermine les objets auxquels elle correspond. Toutefois, chaque table ou vue peut avoir plusieurs clés primaires, index uniques ou contraintes uniques. Par conséquent, vous pouvez spécifier l'index, la clé ou la contrainte à utiliser.  
  
## <a name="common-tasks"></a>Tâches courantes  
Dans cette section, vous pouvez trouver des descriptions des tâches courantes qui prennent en charge ce scénario.  
  
**Définir les options de contrôle de la façon dont les données sont comparées :** lorsque vous comparez des données, vous pouvez ignorer en toute sécurité des colonnes d'identité, désactiver des déclencheurs, puis désactiver des clés étrangères. Vous pouvez également supprimer des clés primaires, des index et des contraintes uniques du script de mise à jour.  
  
**Comparer les données dans les tables et éventuellement mettre à jour la cible pour qu'elle corresponde à la source :** après avoir spécifié une base de données source et une base de données cible à comparer et après avoir effectué la comparaison, vous pouvez afficher les résultats dans la fenêtre de **Comparaison de données**. Vous pouvez afficher non seulement les détails des différences mais également le script de mise à jour que vous pouvez utiliser pour synchroniser les données. Après avoir identifié les différences entre les deux bases de données, vous pouvez spécifier une action pour chaque différence. Vous pouvez ensuite mettre à jour la cible ou exporter le script de mise à jour dans l'éditeur Transact\-SQL ou dans un fichier. Vous pouvez exporter le script afin que vous ou quelqu'un d'autre puisse l'examiner avant d'appliquer les modifications.  
  
## <a name="UnderstandingDataCompareResults"></a>Comprendre les résultats de la comparaison  
Le tableau suivant décrit les cinq colonnes de la fenêtre de **Comparaison de données**.  
  
|colonne|Remarques|  
|----------|---------|  
|Object|Affiche le nom de la table ou de la vue et une case à cocher qui indique si la cible doit être synchronisée lorsque vous entrez des mises à jour ou exportez le script de mise à jour. La case à cocher n'est pas disponible pour les tables ou les vues qui ne contiennent pas de données.|  
|Enregistrements différents|Affiche le nombre d'enregistrements dans la cible qui ont la même clé mais pas les mêmes données que dans la source. Le nombre d'enregistrements marqués pour être mis à jour s'affiche entre parenthèses lorsque vous entrez des mises à jour ou exportez le script de mise à jour.|  
|Uniquement dans la source|Affiche le nombre d'enregistrements dans la source qui n'apparaissent pas dans la cible. Le nombre d'enregistrements marqués pour être ajouté s'affiche entre parenthèses lorsque vous entrez des mises à jour ou exportez le script de mise à jour.|  
|Uniquement dans la cible|Affiche le nombre d'enregistrements dans la cible qui n'apparaissent pas dans la source. Le nombre d'enregistrements marqués pour être supprimés s'affiche entre parenthèses lorsque vous entrez des mises à jour ou exportez le script de mise à jour.|  
|Enregistrements en double|Affiche le nombre d'enregistrements dans la cible qui ont la même clé et les mêmes données que dans la source. Ces enregistrements ne sont pas mis à jour lorsque vous entrez des mises à jour ou exportez le script de mise à jour.|  
  
### <a name="table-and-view-details"></a>Détails des tables et vues  
Lorsque vous cliquez sur une table ou une vue dans la fenêtre de **Comparaison de données**, le volet d'informations affiche toutes les lignes que la table ou la vue contient. Chaque onglet dans le volet d'informations affiche une autre catégorie (Enregistrements différents, Uniquement dans la source, Uniquement dans la cible, Enregistrements en double). Pour chaque ligne, vous pouvez activer ou désactiver la case à cocher correspondante pour indiquer si vous voulez inclure cette modification du script de mise à jour.  
  
## <a name="see-also"></a> Voir aussi  
[Outils de données SQL Server](../ssdt/sql-server-data-tools.md)  
[Guide pratique : Utiliser Comparer les schémas pour comparer différentes définitions de base de données](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
