---
title: StayInSync, propriété-Exemple (VC ++) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StayInSync property [ADO], VC++ example
ms.assetid: 3a5db5f0-094b-46e1-939b-d9fa9417a406
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce7a4a2a9cbfefd9ff2c61fcf8ff4fdfeed233c8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729487"
---
# <a name="stayinsync-property-example-vc"></a>StayInSync, exemple de propriété (VC++)
Cet exemple montre comment la [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) propriété facilite l’accès aux lignes dans une liste hiérarchique [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 La boucle externe affiche le nom et prénom de chaque auteur, l’état et identification. Ajouté **Recordset** pour chaque ligne est récupérée à partir de la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection et attribué automatiquement aux **affectation** par le **StayInSync**  propriété chaque fois que le parent **Recordset** se déplace vers une nouvelle ligne. La boucle interne affiche quatre champs de chaque ligne dans l’objet recordset ajouté.  
  
```  
// BeginStayInSyncCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void StayInSyncX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1 ;  
  
   StayInSyncX();  
   ::CoUninitialize();  
}  
  
void StayInSyncX() {  
   HRESULT  hr = S_OK;  
  
   // Define string variables.  
   _bstr_t strCnn("Provider='MSDataShape'; Data Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _ConnectionPtr pConnection = NULL;  
   _RecordsetPtr pRst = NULL;  
   _RecordsetPtr pRstTitleAuthor = NULL;  
  
   try {  
      TESTHR(pRstTitleAuthor.CreateInstance(__uuidof(Recordset)));  
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
      TESTHR(pRst.CreateInstance(__uuidof(Recordset)));  
  
      // Open connection.  
      pConnection->Open (strCnn, "", "", adConnectUnspecified);  
      pRst->PutStayInSync(true);  
  
      // Open recordset with names from Author & titleauthor table.  
      pRst->Open("SHAPE  {select * from authors} "   
         "APPEND ({select * from titleauthor}"  
         "RELATE au_id TO au_id) AS chapTitleAuthor",  
         _variant_t((IDispatch*)pConnection, true), adOpenStatic, adLockReadOnly, adCmdText);  
  
      pRstTitleAuthor = pRst->GetFields()->GetItem("chapTitleAuthor")->Value;  
      while (!(pRst->EndOfFile)) {      
         printf("\n%s  %s  %s    %s\n", (LPCSTR)(_bstr_t)pRst->  
            Fields->GetItem("au_fname")->Value,  
            (LPCSTR)(_bstr_t)pRst->Fields->GetItem("au_lname")->Value,  
            (LPCSTR)(_bstr_t)pRst->Fields->GetItem("state")->Value,   
            (LPCSTR)(_bstr_t)pRst->Fields->GetItem("au_id")->Value);  
  
         _variant_t vIndex;  
         while ( !(pRstTitleAuthor->EndOfFile) ) {  
            vIndex = (short) 0;  
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
            vIndex = (short) 1;  
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
            vIndex = (short) 2;  
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
            vIndex = (short) 3;  
            printf("%s\n",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
  
            pRstTitleAuthor->MoveNext();  
         }  
         pRst->MoveNext();  
      }  
   }  
   catch(_com_error &e) {  
      // Notify user of errors, if any.  Pass connection pointer accessed from the Recordset.  
      PrintProviderError(pConnection);  
      PrintComError(e);     
   }  
  
   // Clean up objects before exit.  
   if (pRst)  
      if (pRst->State == adStateOpen)  
         pRst->Close();  
   if (pConnection)  
      if (pConnection->State == adStateOpen)  
         pConnection->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print Com errors.    
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Collection de champs (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [StayInSync, propriété](../../../ado/reference/ado-api/stayinsync-property.md)
