---
title: "ptr::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::com::ptr::Attach"
  - "ptr::Attach"
  - "ptr.Attach"
  - "msclr.com.ptr.Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
ms.assetid: 81d930de-cb2a-4c30-9bd6-94d65942c47a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ptr::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将 COM 对象添加到 `com::ptr`。  
  
## 语法  
  
```  
void Attach(  
   _interface_type * _right  
);  
```  
  
#### 参数  
 `_right`  
 指向附加的 COM 接口指针。  
  
## 异常  
 如果 `com::ptr` 已经拥有对 COM 对象的一个引用，则 `Attach` 将抛出 <xref:System.InvalidOperationException>。  
  
## 备注  
 通过调用 `Attach` 对引用 COM 对象，但它的调用方不释放对的引用。  
  
 将 `NULL` 设置为 `Attach` 会导致未采取的操作。  
  
## 示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  在之前属于自己的对象中 `ReplaceDocument` 成员函数先调用 `Release` 并调用 `Attach` 附加一个新文档对象。  
  
```  
// comptr_attach.cpp  
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
 [ptr::operator\=](../dotnet/ptr-operator-assign.md)   
 [ptr::Release](../dotnet/ptr-release.md)