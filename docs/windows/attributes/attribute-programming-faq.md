---
title: 特性编程常见问题
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 6c1762994d2cb109e86397bb0a5db1258cf33be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376065"
---
# <a name="attribute-programming-faq"></a>特性编程常见问题

本主题回答以下常见问题：

- [什么是 HRESULT？](#vcconattributeprogrammmingfaqanchor1)

- [何时必须指定属性的参数名称？](#vcconattributeprogrammmingfaqanchor2)

- [我可以在属性块中使用注释吗？](#vcconattributeprogrammmingfaqanchor3)

- [属性如何与继承交互？](#vcconattributeprogrammmingfaqanchor4)

- [如何在非归因 ATL 项目中使用属性？](#vcconattributeprogrammmingfaqanchor5)

- [如何在属性化项目中使用 .idl 文件？](#vcconattributeprogrammmingfaqanchor6)

- [我可以修改由属性注入的代码吗？](#vcconattributeprogrammmingfaqanchor7)

- [如何转发声明属性化接口？](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [是否可以对派生自同样使用属性的类的属性使用属性？](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a>什么是 HRESULT？

HRESULT 是一种简单的数据类型，通常由属性和 ATL 用作返回值。 下表描述了各种值。 页眉文件 winerror.h 中包含更多值。

|名称|说明|“值”|
|----------|-----------------|-----------|
|S_OK|操作成功|0x00000000|
|E_UNEXPECTED|意外失败|0x8000FFFF|
|E_NOTIMPL|未实现|0x80004001|
|E_OUTOFMEMORY|分配所需内存失败|0x8007000E|
|E_INVALIDARG|一个或多个参数无效|0x80070057|
|E_NOINTERFACE|不支持此类接口|0x80004002|
|E_POINTER|无效指针|0x80004003|
|E_HANDLE|句柄无效|0x80070006|
|E_ABORT|操作已中止|0x80004004|
|E_FAIL|未指定失败|0x80004005|
|E_ACCESSDENIED|常规访问被拒绝错误|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a>何时必须指定属性的参数名称？

在大多数情况下，如果属性具有单个参数，则命名该参数。 在代码中插入该属性时，不需要此名称。 例如，[聚合属性](aggregatable.md)的以下用法：

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

与以下情况完全相同：

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

但是，以下属性具有单个未命名的参数：

||||
|-|-|-|
|[call_as](call-as.md)|[情况 下](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[默认值](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[进入](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[帮助文件](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[进口](import.md)|[importlib](importlib.md)|
|[包括](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[限制](restricted.md)|
|[size_is](size-is.md)|[源](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a>我可以在属性块中使用注释吗？

您可以在属性块中使用单行和多行注释。 但是，不能在括号内使用任一样式的注释，将参数保留到属性。

允许以下操作：

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

不允许使用以下内容：

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a>属性如何与继承交互？

可以从其他类继承属性类和未归因类，这些类本身可能归因与否。 从属性类派生的结果与属性提供程序转换其代码后从该类派生的结果相同。 属性不会通过C++继承传输到派生类。 属性提供程序仅在其属性附近转换代码。

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a>如何在非归因 ATL 项目中使用属性？

您可能有一个非归因 ATL 项目，该项目具有 .idl 文件，您可能需要开始添加属性化对象。 在这种情况下，请使用**添加类向导**提供代码。

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a>如何在属性化项目中使用 .idl 文件？

您可能有一个要在 ATL 属性化项目中使用的 .idl 文件。 在这种情况下，您将使用[importidl](importidl.md)属性，将 .idl 文件编译为 .h 文件（请参阅项目**属性页**对话框中的[MIDL 属性页](../../build/reference/midl-property-pages.md)），然后在项目中包括 .h 文件。

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a>我可以修改由属性注入的代码吗？

某些属性将代码注入到项目中。 您可以使用[/Fx](../../build/reference/fx-merge-injected-code.md)编译器选项查看注入的代码。 还可以从注入的文件复制代码并将其粘贴到源代码中。 这允许您修改属性的行为。 但是，您可能还必须修改代码的其他部分。

以下示例是将注入的代码复制到源代码文件中的结果：

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

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>如何转发声明属性化接口？

如果要对属性化接口进行正向声明，则必须对应用于实际接口声明的正向声明应用相同的属性。 还必须将[导出](export.md)属性应用于前进声明。

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>是否可以对派生自同样使用属性的类的属性使用属性？

否，不支持使用从同样使用属性的类派生的类的属性。

## <a name="see-also"></a>另请参阅

[C++ COM 和 .NET 的属性](cpp-attributes-com-net.md)
