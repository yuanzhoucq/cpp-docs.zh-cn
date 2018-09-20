---
title: ptr::operator! | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr::operator!
- msclr::com::ptr::operator!
- ptr.operator!
- msclr.com.ptr.operator!
dev_langs:
- C++
helpviewer_keywords:
- ptr::operator!
ms.assetid: 7f4101dc-2045-42e7-abb1-6a30e17147f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 186fe4bbeb86780cde586500380a7e2c500da38e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443498"
---
# <a name="ptroperator"></a>ptr::operator!

若要确定是否拥有的 COM 对象无效的运算符。

## <a name="syntax"></a>语法

```
bool operator!();
```

## <a name="return-value"></a>返回值

`true` 如果拥有的 COM 对象无效;`false`否则为。

## <a name="remarks"></a>备注

拥有的 COM 对象是如果它不是有效`nullptr`。

## <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  `CreateInstance`成员函数使用`operator!`以确定文档对象已有所有者，以及无效的对象是否仅创建一个新实例。

```
// comptr_op_not.cpp
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
         if (m_ptrDoc) {
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

```Output
DOM Document created.
```

## <a name="requirements"></a>要求

**标头文件** \<msclr\com\ptr.h >

**Namespace** msclr:: com

## <a name="see-also"></a>请参阅

[ptr 成员](../dotnet/ptr-members.md)<br/>
[ptr::operator bool](../dotnet/ptr-operator-bool.md)