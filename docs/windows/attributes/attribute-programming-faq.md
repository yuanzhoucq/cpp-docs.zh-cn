---
title: 特性编程常见问题
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: fd4c24e3933738d128dffd41018466c33b419de8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025093"
---
# <a name="attribute-programming-faq"></a>特性编程常见问题

本主题回答下列常见问题：

- [HRESULT 是什么？](#vcconattributeprogrammmingfaqanchor1)

- [何时已指定属性的参数名称](#vcconattributeprogrammmingfaqanchor2)

- [可以在特性块中使用注释？](#vcconattributeprogrammmingfaqanchor3)

- [属性与继承？](#vcconattributeprogrammmingfaqanchor4)

- [如何在非属性化 ATL 项目中使用特性？](#vcconattributeprogrammmingfaqanchor5)

- [如何使用特性化项目中的.idl 文件？](#vcconattributeprogrammmingfaqanchor6)

- [可以修改由属性插入的代码？](#vcconattributeprogrammmingfaqanchor7)

- [如何向前声明特性化的接口？](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [可以从还使用特性的类派生的类上使用属性？](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

##  <a name="vcconattributeprogrammmingfaqanchor1"></a> HRESULT 是什么？

HRESULT 为通常用作返回值属性和 ATL 的一般情况下的简单数据类型。 下表介绍各种值。 更多的值包含在标头文件 winerror.h 中。

|名称|描述|值|
|----------|-----------------|-----------|
|S_OK|操作成功|0x00000000|
|E_UNEXPECTED|意外的失败|0x8000FFFF|
|E_NOTIMPL|未实现|0x80004001|
|E_OUTOFMEMORY|无法分配必要的内存|0x8007000E|
|E_INVALIDARG|一个或多个参数均无效|0x80070057|
|E_NOINTERFACE|不支持此类接口|0x80004002|
|E_POINTER|无效的指针|0x80004003|
|E_HANDLE|无效的句柄|0x80070006|
|E_ABORT|操作已中止|0x80004004|
|E_FAIL|未知的故障|0x80004005|
|E_ACCESSDENIED|常规拒绝访问错误|0x80070005|

##  <a name="vcconattributeprogrammmingfaqanchor2"></a> 何时已指定属性的参数名称

在大多数情况下，如果属性具有一个参数，该参数是命名为。 在代码中插入属性时，不需要此名称。 例如，下面的用法[聚合](aggregatable.md)属性：

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

正是与相同：

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

但是，以下属性具有单一的未命名参数：

||||
|-|-|-|
|[call_as](call-as.md)|[case](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[entry](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[import](import.md)|[importlib](importlib.md)|
|[include](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[restricted](restricted.md)|
|[size_is](size-is.md)|[源](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

##  <a name="vcconattributeprogrammmingfaqanchor3"></a> 可以在特性块中使用注释？

您可以使用在属性块中的单行和多行注释。 但是，不能使用注释保存属性的参数的括号中的这两种样式。

以下被允许使用：

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

以下是不允许：

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

##  <a name="vcconattributeprogrammmingfaqanchor4"></a> 属性与继承？

特性化和非特性化类可以继承其他类，它们可能本身由于与否。 从特性化类派生的结果是相同的属性提供程序已转换其代码后从该类派生。 属性未传输到派生类通过 c + + 继承。 特性提供程序仅转换代码附近，其属性。

##  <a name="vcconattributeprogrammmingfaqanchor5"></a> 如何在非属性化 ATL 项目中使用特性？

您可能具有.idl 文件中，非属性化的 ATL 项目，你可能想要开始添加特性化的对象。 在这种情况下，使用**添加类向导**提供代码。

##  <a name="vcconattributeprogrammmingfaqanchor6"></a> 如何使用特性化项目中的.idl 文件？

您可能想要使用它在特性化 ATL 项目中的.idl 文件。 在这种情况下，将使用[importidl](importidl.md)属性中，编译到的.h 文件的.idl 文件 (请参阅[MIDL 属性页](../../build/reference/midl-property-pages.md)在项目的**属性页**对话框)，并然后在项目中包含的.h 文件。

##  <a name="vcconattributeprogrammmingfaqanchor7"></a> 可以修改由属性插入的代码？

某些属性将代码注入到你的项目。 可以使用查看插入的代码[/Fx](../../build/reference/fx-merge-injected-code.md)编译器选项。 还有可能要插入的文件中复制代码并将其粘贴到你的源代码。 这样，您可以修改该属性的行为。 但是，您可能需要修改代码的其他部分。

下面的示例是将插入的代码复制到源的代码文件的结果：

```cpp
// attr_injected.cpp
// compile with: comsupp.lib
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name="MyLibrary") ];

// ITestTest
[
   object, uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"), dual, helpstring("ITestTest Interface"), pointer_default(unique)
]

__interface ITestTest : IDispatch {
   [id(1), helpstring("method DoTest")]
   HRESULT DoTest([in] BSTR str);
};

// _ITestTestEvents
[
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"), dispinterface, helpstring("_ITestTestEvents Interface")
]

__interface _ITestTestEvents {
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);
};

// CTestTest
[
   coclass, threading(apartment), vi_progid("TestATL1.TestTest"), progid("TestATL1.TestTest.1"), version(1.0), uuid("D9632007-14FA-4679-9E1C-28C9A949E784"), // this line would be commented out from original file
   // event_source("com"), // this line would be added to support injected code
   source(_ITestTestEvents), helpstring("TestTest Class")
]

class ATL_NO_VTABLE CTestTest : public ITestTest,
// the following base classes support added injected code
public IConnectionPointContainerImpl<CTestTest>,
public IConnectionPointImpl<CTestTest, &__uuidof(::_ITestTestEvents), CComDynamicUnkArray>
{
public:
   CTestTest() {
   }
   // this line would be commented out from original file
   // __event __interface _ITestTestEvents;
   DECLARE_PROTECT_FINAL_CONSTRUCT()
   HRESULT FinalConstruct() {
      return S_OK;
   }

void FinalRelease() {}

public:
   CComBSTR m_value;
   STDMETHOD(DoTest)(BSTR str) {
      VARIANT_BOOL bCancel = FALSE;
      BeforeChange(str,&bCancel);
      if (bCancel) {
          return Error("Error : Someone don't want us to change the value");
      }

   m_value =str;
   return S_OK;
    }
// the following was copied in from the injected code.
HRESULT BeforeChange(::BSTR i1,::VARIANT_BOOL* i2) {
   HRESULT hr = S_OK;
   IConnectionPointImpl<CTestTest, &__uuidof(_ITestTestEvents), CComDynamicUnkArray>* p = this;
   VARIANT rgvars[2];
   Lock();
   IUnknown** pp = p->m_vec.begin();
   Unlock();
   while (pp < p->m_vec.end()) {
      if (*pp != NULL) {
         IDispatch* pDispatch = (IDispatch*) *pp;
         ::VariantInit(&rgvars[1]);
         rgvars[1].vt = VT_BSTR;
         V_BSTR(&rgvars[1])= (BSTR) i1;
         ::VariantInit(&rgvars[0]);
         rgvars[0].vt = (VT_BOOL | VT_BYREF);
         V_BOOLREF(&rgvars[0])= (VARIANT_BOOL*) i2;
         DISPPARAMS disp = { rgvars, NULL, 2, 0 };
         VARIANT ret_val;
         hr = __ComInvokeEventHandler(pDispatch, 1, 1, &disp, &ret_val);
         if (FAILED(hr))
            break;
      }
      pp++;
   }
   return hr;
}

BEGIN_CONNECTION_POINT_MAP(CTestTest)
CONNECTION_POINT_ENTRY(__uuidof(::_ITestTestEvents))
END_CONNECTION_POINT_MAP()
// end added code section

// _ITestCtrlEvents Methods
public:
};

int main() {}
```

##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> 如何向前声明特性化的接口？

如果要进行特性化接口的前向声明，则必须为前向声明适用于实际接口声明的应用相同的属性。 此外必须应用[导出](export.md)属性为前向声明。

##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> 可以从还使用特性的类派生的类上使用属性？

否，不支持从还使用特性的类派生的类上使用属性。

## <a name="see-also"></a>请参阅

[对于 COM 和.NET 的 c + + 特性](cpp-attributes-com-net.md)