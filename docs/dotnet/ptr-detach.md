---
title: "ptr::Detach | Microsoft Docs"
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
  - "ptr.Detach"
  - "msclr.com.ptr.Detach"
  - "ptr::Detach"
  - "msclr::com::ptr::Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::Detach"
ms.assetid: 23370c8a-8f79-4880-9fa1-46e110c1a92c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

丢弃 COM 对象的所有权，返回指向对象的指针。  
  
## 语法  
  
```  
_interface_type * Detach();  
```  
  
## 返回值  
 指向 COM 对象的指针。  
  
 如果不具有对象，则返回 null。  
  
## 异常  
 在内部，在自己的 COM 对象上调用 `QueryInterface` 并且所有错误 `HRESULT` 通过 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 转换为异常 。  
  
## 备注  
 `Detach` 首先以调用方的利益添加对 COM 对象的引用，然后释放所有通过 `com::ptr` 拥有的引用。调用方必须最终释放返回的对象来销毁它。  
  
## 示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。`DetachDocument` 成员函数调用 `Detach` 来放弃 COM 对象的拥有权并且返回一个指向调用方的指针。  
  
```  
// comptr_detach.cpp  
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
  
   // detach the COM object and return it  
   // this releases the internal reference to the object  
   IXMLDOMDocument* DetachDocument() {  
      return m_ptrDoc.Detach();  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// unmanaged function that loads XML into a raw XML DOM Document object  
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {  
   HRESULT hr = S_OK;  
   VARIANT_BOOL bSuccess;  
   hr = pDoc->loadXML(bstrXml, &bSuccess);  
   if (S_OK == hr && !bSuccess) {  
      hr = E_FAIL;  
   }  
   return hr;  
}  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   IXMLDOMDocument* pDoc = NULL;  
   BSTR bstrXml = NULL;  
  
   try {  
      // create the class from a progid string  
      XmlDocument doc("Msxml2.DOMDocument.3.0");  
  
      bstrXml = ::SysAllocString(L"<word>persnickety</word>");  
      if (NULL == bstrXml) {  
         throw gcnew OutOfMemoryException("bstrXml");  
      }  
      // detach the document object from the ref class  
      pDoc = doc.DetachDocument();  
      // use unmanaged function and raw object to load xml  
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));  
      // release document object as the ref class no longer owns it  
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
 [ptr::Release](../dotnet/ptr-release.md)   
 [ptr::Attach](../dotnet/ptr-attach.md)