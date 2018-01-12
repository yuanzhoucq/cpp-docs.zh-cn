---
title: "ptr::operator = |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ptr.operator=
- msclr.com.ptr.operator=
- msclr::com::ptr::operator=
- ptr::operator=
dev_langs: C++
helpviewer_keywords: operator=
ms.assetid: 58619910-46c0-4db8-b183-c811b23b2df1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e58d177a8d12970ec5c4b9d1b8b86405f153bdc3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ptroperator"></a>ptr::operator=
将附加到 COM 对象`com::ptr`。  
  
## <a name="syntax"></a>语法  
  
```  
ptr<_interface_type> % operator=(  
   _interface_type * _right  
);  
```  
  
#### <a name="parameters"></a>参数  
 `_right`  
 要附加的 COM 接口指针。  
  
## <a name="return-value"></a>返回值  
 跟踪引用上的`com::ptr`。  
  
## <a name="exceptions"></a>异常  
 如果`com::ptr`已拥有对 COM 对象的引用`operator=`引发<xref:System.InvalidOperationException>。  
  
## <a name="remarks"></a>备注  
 分配到 COM 对象`com::ptr`引用的 COM 对象，但不会释放对它的调用方的引用。  
  
 此运算符的相同的效果`Attach`。  
  
## <a name="example"></a>示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  `ReplaceDocument`成员函数首先调用`Release`上任何以前拥有对象，然后使用`operator=`要附加新的文档对象。  
  
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
  
## <a name="requirements"></a>惠?  
 **标头文件** \<msclr\com\ptr.h >  
  
 **Namespace** msclr:: com  
  
## <a name="see-also"></a>请参阅  
 [ptr 成员](../dotnet/ptr-members.md)   
 [ptr::Attach](../dotnet/ptr-attach.md)   
 [ptr::Detach](../dotnet/ptr-detach.md)   
 [ptr::Release](../dotnet/ptr-release.md)