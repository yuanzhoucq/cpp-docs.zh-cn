---
title: "ptr::Release | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ptr.Release"
  - "ptr::Release"
  - "msclr.com.ptr.Release"
  - "msclr::com::ptr::Release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Release 方法"
ms.assetid: 7855781e-e4f6-4ad5-86a5-a81e2c3d90db
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ptr::Release
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

释放 COM 对象上拥有的所有引用。  
  
## 语法  
  
```  
void Release();  
```  
  
## 备注  
 调用此函数释放 COM 对象上拥有的任何引用并将句柄内部 COM 对象为 `nullptr`。如果 COM 对象上的其他引用不存在，将其销毁。  
  
## 示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。`ReplaceDocument` 成员函数使用 `Release` 释放所有的文档对象在附加新文档。  
  
```  
// comptr_release.cpp  
// compile with: /clr /link msxml2.lib  
#include <msxml2.h>  
#include <msclr\com\ptr.h>  
  
#import <msxml3.dll> raw_interfaces_only  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
using namespace msclr;  
  
// a ref class that uses a com::ptr to contain an   
// IXMLDOMDocument object  
ref class XmlDocument {  
public:  
   // construct the internal com::ptr with a null interface  
   // and use CreateInstance to fill it  
   XmlDocument(String^ progid) {  
      m_ptrDoc.CreateInstance(progid);     
   }  
  
   // replace currently held COM object with another one  
   void ReplaceDocument(IXMLDOMDocument* pDoc) {  
      // release current document object  
      m_ptrDoc.Release();  
      // attach the new document object  
      m_ptrDoc.Attach(pDoc);  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// unmanaged function that creates a raw XML DOM Document object  
IXMLDOMDocument* CreateDocument() {  
   IXMLDOMDocument* pDoc = NULL;  
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,  
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));  
   return pDoc;  
}  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   IXMLDOMDocument* pDoc = NULL;  
  
   try {  
      // create the class from a progid string  
      XmlDocument doc("Msxml2.DOMDocument.3.0");  
  
      // get another document object from unmanaged function and  
      // store it in place of the one held by our ref class  
      pDoc = CreateDocument();  
      doc.ReplaceDocument(pDoc);  
      // no further need for raw object reference  
      pDoc->Release();  
      pDoc = NULL;  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
   finally {  
      if (NULL != pDoc) {  
         pDoc->Release();  
      }  
   }  
}  
```  
  
## 要求  
 **Header file** \<msclr\\com\\ptr.h\>  
  
 **Namespace** msclr::com  
  
## 请参阅  
 [ptr 成员](../dotnet/ptr-members.md)   
 [ptr::Detach](../dotnet/ptr-detach.md)