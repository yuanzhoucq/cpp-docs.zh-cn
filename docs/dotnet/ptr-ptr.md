---
title: ptr::ptr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr::ptr
- ptr.ptr
- msclr.com.ptr.ptr
- msclr::com::ptr::ptr
dev_langs:
- C++
helpviewer_keywords:
- ptr::ptr
ms.assetid: 4f5883b4-7c0a-46c6-aa9f-4e49eed463eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 32b142a378fa18f8e14ef48cc75da8db415c2c4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446174"
---
# <a name="ptrptr"></a>ptr::ptr

构造`com::ptr`要包装的 COM 对象。

## <a name="syntax"></a>语法

```
ptr();
ptr(
   _interface_type * p
);
```

#### <a name="parameters"></a>参数

*P*<br/>
COM 接口指针。

## <a name="remarks"></a>备注

无参数构造函数分配`nullptr`对基础对象句柄。 对后续调用`com::ptr`将验证内部对象，并以静默方式失败，直到实际创建或附加对象。

一个参数的构造函数中添加对 COM 对象的引用，但不会释放调用方的引用，因此调用方必须调用`Release`上要真正实现控件的 COM 对象。 当`com::ptr`的调用析构函数，它将自动释放 COM 对象上的引用。

传递`NULL`给此构造函数是与调用无参数版本相同。

## <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 它演示了这两个版本的构造函数的使用情况。

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

## <a name="see-also"></a>请参阅

[ptr 成员](../dotnet/ptr-members.md)<br/>
[ptr::CreateInstance](../dotnet/ptr-createinstance.md)<br/>
[ptr::~ptr](../dotnet/ptr-tilde-ptr.md)