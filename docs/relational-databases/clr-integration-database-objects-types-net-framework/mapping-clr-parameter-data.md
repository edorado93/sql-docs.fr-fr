---
title: Mappage des données de paramètre CLR | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8c9cfd87578b2ffaaefb8b46b340f76f74b373ed
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794561"
---
# <a name="mapping-clr-parameter-data"></a>Mappage des données de paramètres CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le tableau suivant répertorie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données, leurs équivalents dans le common language runtime (CLR) pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le **System.Data.SqlTypes** espace de noms et leurs équivalents de CLR natifs dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET framework.  
  
||||  
|-|-|-|  
|**Type de données SQL Server**|Type (dans System.Data.SqlTypes ou Microsoft.SqlServer.Types)|**Type de données CLR (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, Nullable\<Int64 >**|  
|**binaire**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**bit**|**SqlBoolean**|**Booléen, Nullable\<booléenne >**|  
|**char**|None|None|  
|**cursor**|None|None|  
|**date**|**SqlDateTime**|**Date/heure, Nullable\<DateTime >**|  
|**datetime**|**SqlDateTime**|**Date/heure, Nullable\<DateTime >**|  
|**datetime2**|None|**Date/heure, Nullable\<DateTime >**|  
|**DATETIMEOFFSET**|**Aucun**|**DateTimeOffset, Nullable\<DateTimeOffset >**|  
|**decimal**|**SqlDecimal**|**Decimal, Nullable\<décimal >**|  
|**float**|**SqlDouble**|**Double, Nullable\<Double >**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography** est défini dans Microsoft.SqlServer.Types.dll, qui est installée avec SQL Server et peut être téléchargé à partir de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [du feature pack](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry** est défini dans Microsoft.SqlServer.Types.dll, qui est installée avec SQL Server et peut être téléchargé à partir de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [du feature pack](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** est défini dans Microsoft.SqlServer.Types.dll, qui est installée avec SQL Server et peut être téléchargé à partir de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [du feature pack](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**image**|None|None|  
|**Int**|**SqlInt32**|**Int32, Nullable\<Int32 >**|  
|**money**|**SqlMoney**|**Decimal, Nullable\<décimal >**|  
|**nchar**|**SqlChars, SqlString**|**Chaîne, Char]**|  
|**ntext**|None|None|  
|**numeric**|**SqlDecimal**|**Decimal, Nullable\<décimal >**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SQLChars** est une meilleure correspondance pour le transfert de données et des accès, et **SQLString** est une meilleure correspondance pour effectuer des opérations de chaîne.|**Chaîne, Char]**|  
|**nvarchar (1), nchar (1)**|**SqlChars, SqlString**|**Char, String, Char [], Nullable\<char >**|  
|**real**|**SqlSingle** (la plage de **SqlSingle**, cependant, est supérieure à **réel**)|**Unique, Nullable\<unique >**|  
|**rowversion**|None|**Byte[]**|  
|**smallint**|**SqlInt16**|**Int16, Nullable\<Int16 >**|  
|**smallmoney**|**SqlMoney**|**Decimal, Nullable\<décimal >**|  
|**sql_variant**|None|**Objet**|  
|**table**|None|None|  
|**texte**|None|None|  
|**time**|None|**TimeSpan, Nullable\<TimeSpan >**|  
|**timestamp**|None|None|  
|**tinyint**|**SqlByte**|**Byte, Nullable\<Byte>**|  
|**uniqueidentifier**|**SqlGuid**|**GUID, Nullable\<Guid >**|  
|**Type(UDT) défini par l’utilisateur**|None|La même classe liée au type défini par l'utilisateur dans le même assembly ou un assembly dépendant.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**varbinary(1), binary(1)**|**SqlBytes, SqlBinary**|**byte, Byte[], Nullable\<byte>**|  
|**varchar**|None|None|  
|**xml**|**SqlXml**|None|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Conversion automatique de types de données avec les paramètres de sortie  
 Une méthode CLR peut retourner des informations pour le code ou le programme appelant en marquant un paramètre d’entrée avec la **out** modificateur (Microsoft Visual c#) ou  **\<Out() > ByRef** (Microsoft Visual Basic) Si le paramètre d’entrée est un type de données CLR dans le **System.Data.SqlTypes** espace de noms et le programme appelant spécifie son équivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de type de données en tant que le paramètre d’entrée, une conversion de type se produit automatiquement Lorsque la méthode CLR retourne le type de données.  
  
 Par exemple, la procédure stockée CLR suivante a un paramètre d’entrée du **SqlInt32** type de données CLR qui est marquée avec **out** (c#) ou  **\<Out() > ByRef** () Visual Basic) :  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ … }  
```  
  
```vb  
\<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( \<Out()> ByRef value As SqlInt32)  
…  
End Sub  
```  
  
 Une fois que l’assembly est généré et créé dans la base de données, la procédure stockée est créée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec Transact-SQL suivante, qui spécifie un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données de **int** comme paramètre de sortie :  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Lorsque le CLR stockées procédure est appelée, le **SqlInt32** type de données est automatiquement convertie en un **int** type de données et retourné au programme appelant.  
  
 Cependant, certains types de données CLR ne peuvent pas être convertis automatiquement en leurs types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] équivalents via un paramètre de sortie. Le tableau suivant répertorie ces exceptions.  
  
|||  
|-|-|  
|**Type de données CLR (SQL Server)**|**Type de données SQL Server**|  
|**Décimal**|SMALLMONEY|  
|**SqlMoney**|SMALLMONEY|  
|**Décimal**|money|  
|**DateTime**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|Ajouté **SqlGeography**, **SqlGeometry**, et **SqlHierarchyId** types à la table de mappage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
