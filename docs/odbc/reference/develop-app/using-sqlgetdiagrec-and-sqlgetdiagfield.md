---
title: Utilisation de SQLGetDiagRec et SQLGetDiagField | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 4f486bb1-fad8-4064-ac9d-61f2de85b68b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37fb095579fd173fd24a5df933e3e1a65edbeada
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626037"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Utilisation de SQLGetDiagRec et de SQLGetDiagField
Applications appellent **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer les informations de diagnostic. Ces fonctions acceptent un handle d’environnement, connexion, instruction ou descripteur et renvoient des diagnostics à partir de la fonction de ce descripteur de la dernière utilisation. Les tests de diagnostic enregistrées sur un handle spécifique sont ignorés quand une nouvelle fonction est appelée à l’aide de ce descripteur. Si la fonction a retourné plusieurs enregistrements de diagnostic, l’application appelle ces fonctions plusieurs fois ; le nombre total d’enregistrements d’état est récupéré en appelant **SQLGetDiagField** pour l’enregistrement d’en-tête (enregistrement 0) avec l’option SQL_DIAG_NUMBER.  
  
 Applications extraire les champs de diagnostics individuels en appelant **SQLGetDiagField** et en spécifiant le champ à extraire. Certains champs de diagnostic n’ont pas de toute signification pour certains types de handles. Pour obtenir la liste des champs de diagnostic et leurs significations, consultez le [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) description de fonction.  
  
 Applications de récupérer le SQLSTATE, le code d’erreur natif et le message de diagnostic dans un seul appel en appelant **SQLGetDiagRec**; **SQLGetDiagRec** ne peut pas être utilisé pour récupérer des informations à partir de l’enregistrement d’en-tête.  
  
 Par exemple, le code suivant demande à l’utilisateur d’une instruction SQL et l’exécute. Si des informations de diagnostic a été retournées, elle appelle **SQLGetDiagField** pour obtenir le nombre d’enregistrements d’état et **SQLGetDiagRec** pour obtenir le SQLSTATE, le code d’erreur natif et le message de diagnostic à partir de celles enregistrements.  
  
```  
SQLCHAR       SqlState[6], SQLStmt[100], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLINTEGER    NativeError;  
SQLSMALLINT   i, MsgLen;  
SQLRETURN     rc1, rc2;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement.  
GetSQLStmt(SQLStmt);  
  
// Execute the SQL statement and return any errors or warnings.  
rc1 = SQLExecDirect(hstmt, SQLStmt, SQL_NTS);  
if ((rc1 == SQL_SUCCESS_WITH_INFO) || (rc1 == SQL_ERROR)) {
   SQLLEN numRecs = 0;
   SQLGetDiagField(SQL_HANDLE_STMT, hstmt, 0, SQL_DIAG_NUMBER, &numRecs, 0, 0);
   // Get the status records.
   i = 1;  
   while (i <= numRecs && (rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
            Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState,NativeError,Msg,MsgLen);  
      i++;  
   }  
}  
  
if ((rc1 == SQL_SUCCESS) || (rc1 == SQL_SUCCESS_WITH_INFO)) {  
   // Process statement results, if any.  
}  
```
