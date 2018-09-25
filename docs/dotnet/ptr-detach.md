---
title: ptr::Detach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr.Detach
- msclr.com.ptr.Detach
- ptr::Detach
- msclr::com::ptr::Detach
dev_langs:
- C++
helpviewer_keywords:
- ptr::Detach
ms.assetid: 23370c8a-8f79-4880-9fa1-46e110c1a92c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0f8d5a45cc3805a2e7feb943d5fe2d615c0f4daa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448026"
---
# <a name="ptrdetach"></a>ptr::Detach

放弃 COM 对象，返回一个指向该对象的所有权。

## <a name="syntax"></a>语法

```
_interface_type * Detach();
```

## <a name="return-value"></a>返回值

指向 COM 对象的指针。

如果没有对象为所拥有，则返回 NULL。

## <a name="exceptions"></a>异常

在内部，`QueryInterface`拥有的 COM 对象和任何错误上调用`HRESULT`转换为通过异常<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>。

## <a name="remarks"></a>备注

`Detach` 首先添加对代表调用方的 COM 对象的引用，然后释放所拥有的所有引用`com::ptr`。  最终，调用方必须释放返回的对象，以将其销毁。

## <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  `DetachDocument`成员函数调用`Detach`干脆放弃清理 COM 对象的所有权并返回一个指针，调用方。

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

## <a name="requirements"></a>要求

**标头文件** \<msclr\com\ptr.h >

**Namespace** msclr:: com

## <a name="see-also"></a>请参阅

[ptr 成员](../dotnet/ptr-members.md)<br/>
[ptr::Release](../dotnet/ptr-release.md)<br/>
[ptr::Attach](../dotnet/ptr-attach.md)