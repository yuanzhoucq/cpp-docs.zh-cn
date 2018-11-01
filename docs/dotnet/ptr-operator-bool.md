---
title: ptr::operator bool
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr::operator bool
- ptr.operator bool
- operator bool
- msclr::com::ptr::operator bool
- msclr.com.ptr.operator bool
helpviewer_keywords:
- ptr::operator bool
ms.assetid: 31123377-6ecd-4cef-9b75-3db3996fbcd1
ms.openlocfilehash: 185db15a62cc676c771f60a54c583e19e28e95be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509664"
---
# <a name="ptroperator-bool"></a>ptr::operator bool

使用运算符`com::ptr`条件表达式中。

## <a name="syntax"></a>语法

```
operator bool();
```

## <a name="return-value"></a>返回值

**true**拥有的 COM 对象是否有效，则为**false**否则为。

## <a name="remarks"></a>备注

拥有的 COM 对象是如果它不是有效`nullptr`。

此运算符实际将转换为`_detail_class::_safe_bool`这是比更安全`bool`因为不能将它转换为整型类型。

## <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 `CreateInstance`成员函数使用`operator bool`后创建新的文档对象，以确定它是否有效以及它是否将写入控制台。

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

```Output
DOM Document created.
```

## <a name="requirements"></a>要求

**标头文件** \<msclr\com\ptr.h >

**Namespace** msclr:: com

## <a name="see-also"></a>请参阅

[ptr 成员](../dotnet/ptr-members.md)<br/>
[ptr::operator!](../dotnet/ptr-operator-logical-not.md)