---
title: "com::ptr 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "com::ptr"
  - "msclr::com::ptr"
  - "msclr.com.ptr"
  - "com.ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr 类"
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# com::ptr 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可用作类的 CLR 成员的 COM 对象的包装。其析构函数调用时，也会自动包装 COM 对象生存期管理，在释放所有对象自己的引用。  类似于 [CComPtr Class](../atl/reference/ccomptr-class.md)。  
  
## 语法  
  
```  
template<class _interface_type>  
ref class ptr;  
```  
  
#### 参数  
 `_interface_type`  
 COM 接口  
  
## 备注  
 `com::ptr` 还用于本地变量，各功能简化 COM 和自动化任务生存期管理。  
  
 `com::ptr` 不能直接使用作为函数参数；使用 [% \(跟踪引用\)](../windows/tracking-reference-operator-cpp-component-extensions.md) 或 [对象句柄运算符 \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)。  
  
 `com::ptr` 无法从函数直接返回；使用的句柄。  
  
## 示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。调用类结果的公共方法调用中对包含的 `IXMLDOMDocument` 对象。示例创建了一个 XML 文档的实例，并使用一些简单的 XML，然后执行节点数简化的结构。分析的文档树的 XML 输出到控制台。  
  
```  
// comptr.cpp  
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
  
   void LoadXml(String^ xml) {  
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);  
      BSTR bstr = NULL;  
  
      try {  
         // load some XML into the document  
         bstr = ::SysAllocString(pinnedXml);  
         if (NULL == bstr) {  
            throw gcnew OutOfMemoryException;  
         }  
         VARIANT_BOOL bIsSuccessful = false;  
         // use operator -> to call IXMODOMDocument member function  
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));  
      }  
      finally {  
         ::SysFreeString(bstr);  
      }  
   }  
  
   // simplified function to write just the first xml node to the console  
   void WriteXml() {  
      IXMLDOMNode* pNode = NULL;  
  
      try {  
         // the first child of the document is the first real xml node  
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));  
         if (NULL != pNode) {  
            WriteNode(pNode);  
         }  
      }  
      finally {  
         if (NULL != pNode) {  
            pNode->Release();  
         }  
      }  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   // simplified function that only writes the node  
   void WriteNode(IXMLDOMNode* pNode) {  
      BSTR bstr = NULL;  
  
      try {  
         // write out the name and text properties  
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));  
         String^ strName = gcnew String(bstr);  
         Console::Write("<{0}>", strName);  
         ::SysFreeString(bstr);  
         bstr = NULL;  
  
         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));  
         Console::Write(gcnew String(bstr));  
         ::SysFreeString(bstr);  
         bstr = NULL;  
  
         Console::WriteLine("</{0}>", strName);  
      }  
      finally {  
         ::SysFreeString(bstr);  
      }  
   }  
  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   try {  
      // create the class from a progid string  
      XmlDocument doc("Msxml2.DOMDocument.3.0");  
  
      // stream some xml into the document  
      doc.LoadXml("<word>persnickety</word>");  
  
      // write the document to the console  
      doc.WriteXml();  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
}  
```  
  
  **\<Word wordpersnickety\>\<\/\>**   
## 要求  
 **Header file** \<msclr\\com\\ptr.h\>  
  
 **Namespace** msclr::com  
  
## 请参阅  
 [C\+\+ 支持库](../dotnet/cpp-support-library.md)   
 [ptr 成员](../dotnet/ptr-members.md)