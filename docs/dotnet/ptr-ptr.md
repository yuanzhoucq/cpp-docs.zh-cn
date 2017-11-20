---
title: "ptr::ptr |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ptr::ptr
- ptr.ptr
- msclr.com.ptr.ptr
- msclr::com::ptr::ptr
dev_langs: C++
helpviewer_keywords: ptr::ptr
ms.assetid: 4f5883b4-7c0a-46c6-aa9f-4e49eed463eb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99016a9006bb13be70fe38fd222ad25a08792b20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ptrptr"></a>ptr::ptr
构造`com::ptr`包装的 COM 对象。  
  
## <a name="syntax"></a>语法  
  
```  
ptr();  
ptr(  
   _interface_type * p  
);  
```  
  
#### <a name="parameters"></a>参数  
 `P`  
 COM 接口指针。  
  
## <a name="remarks"></a>备注  
 无参数构造函数将分配`nullptr`对基础对象句柄。 后续调用`com::ptr`将验证的内部对象，并且以静默方式失败，直到实际创建或附加对象。  
  
 单参数构造函数添加对 COM 对象的引用，但不会释放调用方的引用，以便调用方必须调用`Release`上要真正放弃控件的 COM 对象。 当`com::ptr`的调用析构函数，它将自动释放 COM 对象上的引用。  
  
 传递`NULL`向此构造函数是与调用的无参数的版本相同。  
  
## <a name="example"></a>示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 它演示如何使用这两个版本的构造函数。  
  
```  
// comptr_ptr.cpp  
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
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\com\ptr.h >  
  
 **Namespace** msclr:: com  
  
## <a name="see-also"></a>另请参阅  
 [ptr 成员](../dotnet/ptr-members.md)   
 [ptr::CreateInstance](../dotnet/ptr-createinstance.md)   
 [ptr::~ptr](../dotnet/ptr-tilde-ptr.md)