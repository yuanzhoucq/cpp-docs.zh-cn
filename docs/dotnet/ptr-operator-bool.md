---
title: "ptr::operator bool | Microsoft Docs"
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
  - "ptr::operator bool"
  - "ptr.operator bool"
  - "operator bool"
  - "msclr::com::ptr::operator bool"
  - "msclr.com.ptr.operator bool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::operator bool"
ms.assetid: 31123377-6ecd-4cef-9b75-3db3996fbcd1
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在条件表达式中，使用运算符 `com::ptr` 。  
  
## 语法  
  
```  
operator bool();  
```  
  
## 返回值  
 如果指定的对象有效，则为 `true`；否则为 `false`。  
  
## 备注  
 如果其不是`nullptr`，那么所持有的COM 对象是有效的。  
  
 比 `bool` 安全的此运算符实际上转换为 `_detail_class::_safe_bool`，因为它无法转换为整型。  
  
## 示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  在创建新文档对象后， 成员函数`CreateInstance` 使用 `operator bool`来判定其是否有效，然后将其写到控制台 。  
  
```  
// comptr_op_bool.cpp  
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
   void CreateInstance(String^ progid) {  
      if (!m_ptrDoc) {  
         m_ptrDoc.CreateInstance(progid);     
         if (m_ptrDoc) { // uses operator bool  
            Console::WriteLine("DOM Document created.");  
         }  
      }  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   try {  
      XmlDocument doc;  
      // create the instance from a progid string  
      doc.CreateInstance("Msxml2.DOMDocument.3.0");  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
}  
```  
  
  **创建DOM 文档。**   
## 要求  
 **Header file** \<msclr\\com\\ptr.h\>  
  
 **Namespace** msclr::com  
  
## 请参阅  
 [ptr 成员](../dotnet/ptr-members.md)   
 [ptr::operator\!](../dotnet/ptr-operator-logical-not.md)