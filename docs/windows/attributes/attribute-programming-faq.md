---
title: 特性编程常见问题
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 4191704da2fdac849ac1ce97692c2421ba7cda41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168378"
---
# <a name="attribute-programming-faq"></a>特性编程常见问题

本主题回答以下常见问题：

- [什么是 HRESULT？](#vcconattributeprogrammmingfaqanchor1)

- [何时需要指定属性的参数名称？](#vcconattributeprogrammmingfaqanchor2)

- [能否在属性块中使用注释？](#vcconattributeprogrammmingfaqanchor3)

- [特性如何与继承进行交互？](#vcconattributeprogrammmingfaqanchor4)

- [如何使用非特性化 ATL 项目中的属性？](#vcconattributeprogrammmingfaqanchor5)

- [如何在特性化项目中使用 .idl 文件？](#vcconattributeprogrammmingfaqanchor6)

- [能否修改由属性注入的代码？](#vcconattributeprogrammmingfaqanchor7)

- [如何转发声明属性化接口？](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [能否对从也使用特性的类派生的类使用特性？](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

##  <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a>什么是 HRESULT？

HRESULT 是一种简单的数据类型，通常由特性和 ATL 通常用作返回值。 下表描述了各种值。 标头文件 winerror.h 中包含的值越多。

|名称|描述|值|
|----------|-----------------|-----------|
|S_OK|操作成功|0x00000000|
|E_UNEXPECTED|意外故障|0x8000FFFF|
|E_NOTIMPL|未实现|0x80004001|
|E_OUTOFMEMORY|未能分配所需的内存|0x8007000E|
|E_INVALIDARG|一个或多个参数无效|0x80070057|
|E_NOINTERFACE|不支持此类接口|0x80004002|
|E_POINTER|无效指针|0x80004003|
|E_HANDLE|句柄无效|0x80070006|
|E_ABORT|操作中止|0x80004004|
|E_FAIL|未指定的失败|0x80004005|
|E_ACCESSDENIED|常规拒绝访问错误|0x80070005|

##  <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a>何时需要指定属性的参数名称？

在大多数情况下，如果特性只有一个参数，则该参数名为。 在代码中插入属性时不需要此名称。 例如，以下可[聚合](aggregatable.md)属性的用法：

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

完全相同：

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

但是，以下属性有一个未命名的参数：

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
|[size_is](size-is.md)|[source](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

##  <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a>能否在属性块中使用注释？

您可以在特性块中同时使用单行注释和多行注释。 但是，不能在保存属性参数的括号内使用任意样式的注释。

允许以下操作：

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

不允许以下操作：

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

##  <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a>特性如何与继承进行交互？

可以从其他类继承特性化和无归属类，这些类本身可能是特性化的。 从特性化类派生的结果与属性提供程序转换其代码后从该类派生的结果相同。 属性不通过C++继承传输到派生类。 特性提供程序仅在其特性的邻近范围内转换代码。

##  <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a>如何使用非特性化 ATL 项目中的属性？

您可能有一个包含 .idl 文件的非特性化 ATL 项目，您可能希望开始添加特性化对象。 在这种情况下，请使用 "**添加类向导**" 提供代码。

##  <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a>如何在特性化项目中使用 .idl 文件？

您可能有一个要在 ATL 特性化项目中使用的 .idl 文件。 在这种情况下，您将使用[importidl](importidl.md)属性，将 .idl 文件编译为 .h 文件（在项目的 "**属性页**" 对话框中，请参阅[MIDL 属性页](../../build/reference/midl-property-pages.md)），然后在您的项目中包含 .h 文件。

##  <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a>能否修改由属性注入的代码？

某些属性将代码注入到你的项目中。 您可以使用[/fx](../../build/reference/fx-merge-injected-code.md)编译器选项查看注入的代码。 还可以从插入的文件复制代码并将其粘贴到源代码中。 这允许您修改属性的行为。 但是，您可能还需要修改代码的其他部分。

下面的示例是将注入的代码复制到源代码文件中的结果：

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

##  <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>如何转发声明属性化接口？

如果要对属性化接口进行前向声明，则必须将相同的属性应用于应用于实际接口声明的前向声明。 还必须将[导出](export.md)特性应用到前向声明。

##  <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>能否对从也使用特性的类派生的类使用特性？

不可以。不支持对从也使用特性的类派生的类使用特性。

## <a name="see-also"></a>请参阅

[COM 和 .NET 的 C++ 属性](cpp-attributes-com-net.md)
