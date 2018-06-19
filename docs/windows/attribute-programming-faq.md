---
title: 特性编程常见问题 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributed programming
- attributes [C++], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35b57c8813778cf0bbf8efbfcbee8466074b87f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862359"
---
# <a name="attribute-programming-faq"></a>特性编程常见问题
本主题回答下列常见问题：  
  
-   [HRESULT 是什么？](#vcconattributeprogrammmingfaqanchor1)  
  
-   [何时具有指定属性的参数名称](#vcconattributeprogrammmingfaqanchor2)  
  
-   [可以在特性块中使用注释？](#vcconattributeprogrammmingfaqanchor3)  
  
-   [属性如何与继承交互？](#vcconattributeprogrammmingfaqanchor4)  
  
-   [如何在非特性化 ATL 项目中使用属性？](#vcconattributeprogrammmingfaqanchor5)  
  
-   [如何使用特性化项目中的.idl 文件？](#vcconattributeprogrammmingfaqanchor6)  
  
-   [可以修改由属性插入的代码？](#vcconattributeprogrammmingfaqanchor7)  
  
-   [如何向前声明特性化的接口？](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)  
  
-   [可以从还使用属性的类派生的类上使用属性？](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)  
  
##  <a name="vcconattributeprogrammmingfaqanchor1"></a> HRESULT 是什么？  
 `HRESULT`是通常由作为返回值特性和 ATL 通常以简单数据类型。 下表介绍各种值。 标头文件 winerror.h 中包含多个值。  
  
|名称|描述|值|  
|----------|-----------------|-----------|  
|S_OK|操作成功|0x00000000|  
|E_UNEXPECTED|意外的失败|: 0x8000FFFF|  
|E_NOTIMPL|未实现|0x80004001|  
|E_OUTOFMEMORY|无法分配必要的内存|已用完 0x8007000E|  
|E_INVALIDARG|一个或多个参数是无效|0x80070057|  
|E_NOINTERFACE|不支持此接口|0x80004002|  
|E_POINTER|无效的指针|0x80004003|  
|E_HANDLE|无效句柄|0x80070006|  
|E_ABORT|操作中止|0x80004004|  
|E_FAIL|未指定的失败|0x80004005|  
|E_ACCESSDENIED|常规拒绝访问错误|0x80070005|  
  
##  <a name="vcconattributeprogrammmingfaqanchor2"></a> 何时具有指定属性的参数名称  
 在大多数情况下，如果属性具有单个参数，该参数的名称为。 如果在你的代码中插入该属性，则不需要此名称。 例如，下面的用法的[聚合](../windows/aggregatable.md)属性：  
  
```  
[coclass, aggregatable(value=allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 正是相同：  
  
```  
[coclass, aggregatable(allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 但是，以下属性具有单一的未命名参数：  
  
||||  
|-|-|-|  
|[call_as](../windows/call-as.md)|[case](../windows/case-cpp.md)|[cpp_quote](../windows/cpp-quote.md)|  
|[default](../windows/default-cpp.md)|[defaultvalue](../windows/defaultvalue.md)|[defaultvtable](../windows/defaultvtable.md)|  
|[emitidl](../windows/emitidl.md)|[entry](../windows/entry.md)|[first_is](../windows/first-is.md)|  
|[helpcontext](../windows/helpcontext.md)|[helpfile](../windows/helpfile.md)|[helpstring](../windows/helpstring.md)|  
|[helpstringcontext](../windows/helpstringcontext.md)|[helpstringdll](../windows/helpstringdll.md)|[id](../windows/id.md)|  
|[iid_is](../windows/iid-is.md)|[import](../windows/import.md)|[importlib](../windows/importlib.md)|  
|[include](../windows/include-cpp.md)|[includelib](../windows/includelib-cpp.md)|[last_is](../windows/last-is.md)|  
|[length_is](../windows/length-is.md)|[max_is](../windows/max-is.md)|[no_injected_text](../windows/no-injected-text.md)|  
|[pointer_default](../windows/pointer-default.md)|[pragma](../windows/pragma.md)|[restricted](../windows/restricted.md)|  
|[size_is](../windows/size-is.md)|[源](../windows/source-cpp.md)|[switch_is](../windows/switch-is.md)|  
|[switch_type](../windows/switch-type.md)|[transmit_as](../windows/transmit-as.md)|[wire_marshal](../windows/wire-marshal.md)|  
  
##  <a name="vcconattributeprogrammmingfaqanchor3"></a> 可以在特性块中使用注释？  
 你可以使用特性块中的单行和多行注释。 但是，不能使用两种样式中的属性中保存的参数的括号内的注释。  
  
 以下被允许:  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1"), /* Multiple-line  
                                       comment */  
   threading("both") // Single-line comment  
]  
```  
  
 不允许以下：  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1" /* Multiple-line comment */ ),  
   threading("both" // Single-line comment)  
]  
```  
  
##  <a name="vcconattributeprogrammmingfaqanchor4"></a> 属性如何与继承交互？  
 你可以从其他类，该类可能本身被归因或不继承特性化和非特性化类。 从特性化的类派生的结果是相同的属性提供程序已转换其代码后从该类派生。 属性不会传输到派生通过 c + + 继承的类。 属性提供程序仅转换邻近及其属性的代码。  
  
##  <a name="vcconattributeprogrammmingfaqanchor5"></a> 如何在非特性化 ATL 项目中使用属性？  
 你可能必须具有.idl 文件，一个非特性化的 ATL 项目，并且你可能想要开始添加特性化的对象。 在这种情况下，使用添加类向导提供的代码。  
  
##  <a name="vcconattributeprogrammmingfaqanchor6"></a> 如何使用特性化项目中的.idl 文件？  
 你可能具有你想要使用特性化 ATL 项目中的.idl 文件。 在这种情况下，将使用[importidl](../windows/importidl.md)特性，编译的.h 文件的.idl 文件 (请参阅[MIDL 属性页](../ide/midl-property-pages.md)项目的属性页对话框中)，然后将.h 文件包含在你的项目.  
  
##  <a name="vcconattributeprogrammmingfaqanchor7"></a> 可以修改由属性插入的代码？  
 某些特性将代码注入到你的项目。 你可以通过查看插入的代码[/Fx](../build/reference/fx-merge-injected-code.md)编译器选项。 还有可能从插入文件复制代码并将其粘贴到你的源代码。 这样，您可以修改该属性的行为。 但是，你可能需要修改你的代码以及其他部分。  
  
 下面的示例是将插入的代码复制到一个源代码文件的结果：  
  
```  
// attr_injected.cpp  
// compile with: comsupp.lib  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
  
[ module(name="MyLibrary") ];  
  
// ITestTest  
[   
   object,  
   uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"),  
   dual,  
   helpstring("ITestTest Interface"),  
   pointer_default(unique)  
]  
  
__interface ITestTest : IDispatch {  
   [id(1), helpstring("method DoTest")]   
   HRESULT DoTest([in] BSTR str);  
};  
  
// _ITestTestEvents  
[  
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"),  
   dispinterface,  
   helpstring("_ITestTestEvents Interface")  
]  
  
__interface _ITestTestEvents {  
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);  
};  
  
// CTestTest  
[  
   coclass,  
   threading(apartment),  
   vi_progid("TestATL1.TestTest"),  
   progid("TestATL1.TestTest.1"),  
   version(1.0),  
   uuid("D9632007-14FA-4679-9E1C-28C9A949E784"),  
   // this line would be commented out from original file  
   // event_source("com"),  
   // this line would be added to support injected code  
   source(_ITestTestEvents),  
   helpstring("TestTest Class")  
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
 如果想要使前向声明的属性化接口，必须将相同的属性应用到适用于实际接口声明前向声明。 你还必须应用[导出](../windows/export.md)属性设为前向声明。  
  
##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> 可以从还使用属性的类派生的类上使用属性？  
 否，不支持从还使用属性的类派生的类上使用属性。  
  
## <a name="see-also"></a>请参阅  
 [概念](../windows/attributed-programming-concepts.md)