---
title: "ptr::operator= | Microsoft Docs"
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
  - "ptr.operator="
  - "msclr.com.ptr.operator="
  - "msclr::com::ptr::operator="
  - "ptr::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator="
ms.assetid: 58619910-46c0-4db8-b183-c811b23b2df1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::operator=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将 COM 对象添加到 `com::ptr`。  
  
## 语法  
  
```  
ptr<_interface_type> % operator=(  
   _interface_type * _right  
);  
```  
  
#### 参数  
 `_right`  
 指向附加的 COM 接口指针。  
  
## 返回值  
 在 `com::ptr` 上的跟踪引用。  
  
## 异常  
 如果 `com::ptr` 已经拥有对 COM 对象的一个引用，则 `operator=` 将抛出 <xref:System.InvalidOperationException>。  
  
## 备注  
 分配一个 COM 对象给 一个 `com::ptr` 引用 COM 对象，但不释放调用者的引用。  
  
 此运算符与 `Attach` 作用相同。  
  
## 示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。在之前属于自己的对象中 `ReplaceDocument` 成员函数先调用 `Release` 并使用 `operator=` 附加一个新文档对象。  
  
```  
// comptr_op_assign.cpp  
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
      m_ptrDoc = pDoc;  
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
      // store it in place of the one held by the ref class  
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
 [ptr::Attach](../dotnet/ptr-attach.md)   
 [ptr::Detach](../dotnet/ptr-detach.md)   
 [ptr::Release](../dotnet/ptr-release.md)