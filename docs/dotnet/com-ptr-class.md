---
title: com::ptr 类
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::com::ptr::ptr
- msclr::com::ptr::Attach
- msclr::com::ptr::CreateInstance
- msclr::com::ptr::Detach
- msclr::com::ptr::GetInterface
- msclr::com::ptr::QueryInterface
- msclr::com::ptr::Release
- msclr::com::ptr::operator=
- msclr::com::ptr::operator->
- msclr::com::ptr::operator!
helpviewer_keywords:
- msclr::ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
ms.openlocfilehash: 8909f91e31279f1fc1395610aea4708b79731113
ms.sourcegitcommit: 9813e146a4eb30929d8352872859e8fcb7ff6d2f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805963"
---
# <a name="comptr-class"></a>com::ptr 类

可用作 CLR 类的成员的 COM 对象的包装器。  该包装器还可自动执行 COM 对象的生存期管理，并在调用对象的析构函数时释放对象上所有拥有的引用。 类似于[CComPtr 类](../atl/reference/ccomptr-class.md)。

## <a name="syntax"></a>语法

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>参数

*_interface_type*<br/>
COM 接口。

## <a name="remarks"></a>备注

`com::ptr` 还可用作局部函数变量，用来简化各种 COM 任务和自动执行生成期管理。

一个`com::ptr`不能直接用作函数参数; 使用[跟踪引用运算符](../windows/tracking-reference-operator-cpp-component-extensions.md)或[对象句柄运算符 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)相反。

一个`com::ptr`不能直接从函数返回; 请改用句柄。

## <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  调用类的公共方法将导致调用 `IXMLDOMDocument` 对象。  本示例创建一个 XML 文档实例，并使用一些简单 XML 填充它，然后在分析过的文档树中执行简化的节点浏览以将 XML 输出到控制台。

```cpp
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

```Output
<word>persnickety</word>
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|name|描述| 
|---------|-----------| 
|[ptr::ptr](#ptr)|构造`com::ptr`要包装的 COM 对象。| 
|[ptr::~ptr](#tilde-ptr)|因`com::ptr`。| 

### <a name="public-methods"></a>公共方法

|name|描述|
|---------|-----------| 
|[ptr::Attach](#attach)|将附加到的 COM 对象`com::ptr`。| 
|[ptr::CreateInstance](#createInstance)|创建中的 COM 对象的实例`com::ptr`。| 
|[ptr::Detach](#detach)|放弃 COM 对象，返回一个指向该对象的所有权。| 
|[ptr::GetInterface](#getInterface)|创建中的 COM 对象的实例`com::ptr`。| 
|[ptr::QueryInterface](#queryInterface)|查询接口拥有的 COM 对象，并将该结果附加到另一个`com::ptr`。| 
|[ptr::Release](#release)|释放 COM 对象上所有拥有的引用。|

### <a name="public-operators"></a>公共运算符

|name|描述|
|---------|-----------| 
|[ptr::operator-&gt;](#operator-arrow)|成员访问运算符，用于在拥有的 COM 对象上调用方法。| 
|[ptr::operator=](#operator-assign)|将附加到的 COM 对象`com::ptr`。| 
|[ptr::operator&nbsp;bool](#operator-bool)|使用运算符`com::ptr`条件表达式中。| 
|[ptr::operator!](#operator-logical-not)|若要确定是否拥有的 COM 对象无效的运算符。| 

## <a name="requirements"></a>要求

**标头文件** \<msclr\com\ptr.h >

**Namespace** msclr:: com

 

## <a name="ptr"></a>ptr::ptr

返回指向拥有的 COM 对象的指针。

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>参数

*P*<br/>
COM 接口指针。

### <a name="remarks"></a>备注

无参数构造函数分配`nullptr`对基础对象句柄。 以后调用`com::ptr`将验证内部对象，并以静默方式失败，直到创建或附加对象。

单参数构造函数中添加对 COM 对象的引用，但不会释放调用方的引用，以便调用方必须调用`Release`上要真正实现控件的 COM 对象。 当`com::ptr`的调用析构函数，它将自动释放 COM 对象上的引用。

传递`NULL`给此构造函数是与调用无参数版本相同。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 它演示了这两个版本的构造函数的使用情况。

```cpp
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

## <a name="tilde-ptr"></a>ptr::~ptr

因`com::ptr`。

```cpp
~ptr();
```

### <a name="remarks"></a>备注

析构，`com::ptr`释放它拥有其 COM 对象的所有引用。 假定没有其他一直保持到 COM 对象的引用，将删除的 COM 对象并释放其内存。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  在`main`函数，这两个`XmlDocument`它们超出范围时，将调用对象的析构函数`try`块中，从而导致基础`com::ptr`正在调用析构函数释放 COM 到所有拥有的引用对象。

```cpp
// comptr_dtor.cpp
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

## <a name="attach"></a>ptr::Attach

将附加到的 COM 对象`com::ptr`。

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>参数

*_right*<br/>
要附加的 COM 接口指针。

### <a name="exceptions"></a>Exceptions

如果`com::ptr`已拥有对 COM 对象的引用`Attach`引发<xref:System.InvalidOperationException>。

### <a name="remarks"></a>备注

调用`Attach`引用 COM 对象，但不会释放对它的调用方的引用。

传递`NULL`到`Attach`不导致正在采取任何操作。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 `ReplaceDocument`成员函数的第一个调用`Release`任何以前拥有对象，然后调用`Attach`要附加新的文档对象。

```cpp
// comptr_attach.cpp
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
      m_ptrDoc.Attach(pDoc);
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
      // store it in place of the one held by our ref class
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

## <a name="createInstance"></a>ptr::CreateInstance

创建中的 COM 对象的实例`com::ptr`。

```cpp
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   System::String ^ progid
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   const wchar_t * progid
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter
);
void CreateInstance(
   REFCLSID rclsid
);
```

### <a name="parameters"></a>参数

*progid*<br/>
`ProgID` 字符串。

*pouter*<br/>
指向聚合对象的 IUnknown 接口 (控制 IUnknown)。 如果`pouter`未指定，`NULL`使用。

*cls_context*<br/>
管理新创建的对象的代码将在其中运行的上下文。 值取自`CLSCTX`枚举。 如果`cls_context`未指定，使用 CLSCTX_ALL 的值。

*rclsid*<br/>
`CLSID` 关联的数据和将用于创建对象的代码。

### <a name="exceptions"></a>Exceptions

如果`com::ptr`已拥有对 COM 对象的引用`CreateInstance`引发<xref:System.InvalidOperationException>。

此函数将调用`CoCreateInstance`，并使用<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>要转换的任何错误`HRESULT`到相应的异常。

### <a name="remarks"></a>备注

`CreateInstance` 使用`CoCreateInstance`创建标识从 ProgID 或 CLSID 的指定对象的新实例。 `com::ptr`引用新创建的对象并将自动释放在析构时所有拥有的引用。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 类构造函数使用两种不同形式的`CreateInstance`可以根据 ProgID 或 CLSID 加上 CLSCTX 创建文档对象。

```cpp
// comptr_createinstance.cpp
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
   XmlDocument(REFCLSID clsid, DWORD clsctx) {
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc1("Msxml2.DOMDocument.3.0");

      // or from a clsid with specific CLSCTX
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

## <a name="detach"></a>ptr::Detach

放弃 COM 对象，返回一个指向该对象的所有权。

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>返回值

指向 COM 对象的指针。

如果没有对象为所拥有，则返回 NULL。

### <a name="exceptions"></a>Exceptions

在内部，`QueryInterface`拥有的 COM 对象和任何错误上调用`HRESULT`转换为通过异常<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>。

### <a name="remarks"></a>备注

`Detach` 首先添加对代表调用方的 COM 对象的引用，然后释放所拥有的所有引用`com::ptr`。  最终，调用方必须释放返回的对象，以将其销毁。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  `DetachDocument`成员函数调用`Detach`干脆放弃清理 COM 对象的所有权并返回一个指针，调用方。

```cpp
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

## <a name="getInterface"></a>ptr::GetInterface

返回指向拥有的 COM 对象的指针。

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>返回值

指向拥有的 COM 对象的指针。

### <a name="exceptions"></a>Exceptions

在内部，`QueryInterface`拥有的 COM 对象和任何错误上调用`HRESULT`转换为通过异常<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>。

### <a name="remarks"></a>备注

`com::ptr`代表调用方的添加对 COM 对象的引用，并同样将它自己的引用保持对 COM 对象。 最终，调用方必须释放对返回的对象的引用，或将永远不会被销毁。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 `GetDocument`成员函数使用`GetInterface`以返回指向 COM 对象的指针。

```cpp
// comptr_getinterface.cpp
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

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
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
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
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
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
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

```Output
<word>persnickety</word>
```

## <a name="queryInterface"></a>ptr::QueryInterface

查询接口拥有的 COM 对象，并将该结果附加到另一个`com::ptr`。

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>参数

*other*<br/>
`com::ptr` ，将获取接口。

### <a name="exceptions"></a>Exceptions

在内部，`QueryInterface`拥有的 COM 对象和任何错误上调用`HRESULT`转换为通过异常<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>。

### <a name="remarks"></a>备注

使用此方法创建归当前包装的 COM 对象的不同接口的 COM 包装器。 此方法调用`QueryInterface`通过拥有的 COM 对象，以请求指向特定的 COM 接口的对象，并将返回的接口指针附加到传入的`com::ptr`。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 `WriteTopLevelNode`成员函数使用`QueryInterface`以填充本地`com::ptr`与`IXMLDOMNode`，然后将传递`com::ptr`（通过跟踪引用） 的私有成员函数向控制台写入节点的名称和文本属性。

```cpp
// comptr_queryinterface.cpp
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
         // load some XML into our document
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

   // write the top level node to the console
   void WriteTopLevelNode() {
      com::ptr<IXMLDOMNode> ptrNode;

      // query for the top level node interface
      m_ptrDoc.QueryInterface(ptrNode);
      WriteNode(ptrNode);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(com::ptr<IXMLDOMNode> % node) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(node->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(node->get_text(&bstr));
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
      doc.WriteTopLevelNode();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<#document>persnickety</#document>
```

## <a name="release"></a>ptr::Release

释放 COM 对象上所有拥有的引用。

```cpp
void Release();
```

### <a name="remarks"></a>备注

调用此函数释放 COM 对象上所有拥有的引用和设置的内部句柄的 COM 对象`nullptr`。  如果不存在任何其他引用 COM 对象，它将被销毁。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  `ReplaceDocument`成员函数使用`Release`附加新文档之前释放任何以前的文档对象。

```cpp
// comptr_release.cpp
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
      m_ptrDoc.Attach(pDoc);
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
      // store it in place of the one held by our ref class
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

## <a name="operator-arrow"></a>ptr::operator-&gt;

成员访问运算符，用于在拥有的 COM 对象上调用方法。

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>返回值

一个`smart_com_ptr`对 COM 对象。

### <a name="exceptions"></a>Exceptions

在内部，`QueryInterface`拥有的 COM 对象和任何错误上调用`HRESULT`转换为通过异常<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>。

### <a name="remarks"></a>备注

此运算符，可调用拥有的 COM 对象的方法。 它将返回一个临时`smart_com_ptr`用于自动处理其自身`AddRef`和`Release`。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 `WriteDocument`函数使用`operator->`调用`get_firstChild`文档对象的成员。

```cpp
// comptr_op_member.cpp
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

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
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
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
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
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
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

```Output
<word>persnickety</word>
```

## <a name="operator-assign"></a>ptr::operator=

将附加到的 COM 对象`com::ptr`。

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>参数

*_right*<br/>
要附加的 COM 接口指针。

### <a name="return-value"></a>返回值

跟踪引用上的`com::ptr`。

### <a name="exceptions"></a>Exceptions

如果`com::ptr`已拥有对 COM 对象的引用`operator=`引发<xref:System.InvalidOperationException>。

### <a name="remarks"></a>备注

分配到的 COM 对象`com::ptr`引用 COM 对象，但不会释放对它的调用方的引用。

此运算符具有相同的效果`Attach`。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  `ReplaceDocument`成员函数的第一个调用`Release`任何以前拥有对象，然后使用`operator=`要附加新的文档对象。

```cpp
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

## <a name="operator-bool"></a> ptr::operator bool

使用运算符`com::ptr`条件表达式中。

```cpp
operator bool();
```

### <a name="return-value"></a>返回值

`true` 如果拥有的 COM 对象有效，则为`false`否则为。

### <a name="remarks"></a>备注

拥有的 COM 对象是如果它不是有效`nullptr`。

此运算符将转换为`_detail_class::_safe_bool`这是比更安全`bool`因为不能将它转换为整型类型。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 `CreateInstance`成员函数使用`operator bool`后创建新的文档对象，以确定它是否有效以及它是否将写入控制台。

```cpp
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

## <a name="operator-logical-not"></a>ptr::operator!

若要确定是否拥有的 COM 对象无效的运算符。

```cpp
bool operator!();
```

### <a name="return-value"></a>返回值

`true` 如果拥有的 COM 对象无效;`false`否则为。

### <a name="remarks"></a>备注

拥有的 COM 对象是如果它不是有效`nullptr`。

### <a name="example"></a>示例

本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。  `CreateInstance`成员函数使用`operator!`以确定文档对象已有所有者，以及无效的对象是否仅创建一个新实例。

```cpp
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
