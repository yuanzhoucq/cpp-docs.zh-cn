---
title: "ptr::~ptr | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr.com.ptr.~ptr"
  - "ptr.~ptr"
  - "msclr::com.ptr::~ptr"
  - "~ptr"
  - "ptr::~ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::~ptr"
ms.assetid: 5f644aa5-fe66-4992-a5f8-13ec1292c949
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::~ptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`com::ptr`析构。  
  
## 语法  
  
```  
~ptr();  
```  
  
## 备注  
 在销毁，它拥有对其 COM 对象的 `com::ptr` 释放所有引用。  假定，不再引用对 COM 对象，COM 对象将被删除，并将已释放其内存。  
  
## 示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。在 `main` 函数，那么，当结构超出 `try` 块的大小，从而调用的基础 `com::ptr` 析构函数，释放对 COM 对象的所有引用，拥有的两个 `XmlDocument` 对象的析构函数调用。  
  
```  
// comptr_dtor.cpp  
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
  
   // construct the internal com::ptr with a COM object  
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   IXMLDOMDocument* pDoc = NULL;  
  
   try {  
      // create an XML DOM document object  
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,   
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));  
      // construct the ref class with the COM object  
      XmlDocument doc1(pDoc);  
  
      // or create the class from a progid string  
      XmlDocument doc2("Msxml2.DOMDocument.3.0");  
   }  
   // doc1 and doc2 destructors are called when they go out of scope  
   // and the internal com::ptr releases its reference to the COM object  
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
 [ptr::ptr](../dotnet/ptr-ptr.md)   
 [ptr::CreateInstance](../dotnet/ptr-createinstance.md)