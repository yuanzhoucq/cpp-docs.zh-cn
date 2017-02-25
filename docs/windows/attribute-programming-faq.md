---
title: "Attribute Programming FAQ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributed programming"
  - "attributes [C++], frequently asked questions"
  - "FAQs (frequently asked questions), attributed programming [C++]"
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Attribute Programming FAQ
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题回答以下常见问题:  
  
-   [什么是 HRESULT?](#vcconattributeprogrammmingfaqanchor1)  
  
-   [我当必须为特性指定参数名称?](#vcconattributeprogrammmingfaqanchor2)  
  
-   [我是否能将注释在特性块?](#vcconattributeprogrammmingfaqanchor3)  
  
-   [属性与继承交互?](#vcconattributeprogrammmingfaqanchor4)  
  
-   [如何使用属性在一个非 ATL 项目?](#vcconattributeprogrammmingfaqanchor5)  
  
-   [如何使用 .idl 文件在一个特性化项目中?](#vcconattributeprogrammmingfaqanchor6)  
  
-   [我是否能修改属性插入的代码?](#vcconattributeprogrammmingfaqanchor7)  
  
-   [如何前向声明特性化的界面?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)  
  
-   [我是否能将在从还可以使用属性的类派生的类的属性?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)  
  
##  <a name="vcconattributeprogrammmingfaqanchor1"></a> 什么是 HRESULT?  
 `HRESULT` 由属性和 ATL 通常一个简单的数据类型，因为返回值通常。  下表描述了各种值。  多个值在头文件包含 winerror.h。  
  
|名称|说明|值|  
|--------|--------|-------|  
|S\_OK|成功的操作|0x00000000|  
|E\_UNEXPECTED|意外的失败|0x8000FFFF|  
|E\_NOTIMPL|未实现|0x80004001|  
|E\_OUTOFMEMORY|未能分配必要的内存|0x8007000E|  
|E\_INVALIDARG|一个或多个无效的参数|0x80070057|  
|E\_NOINTERFACE|不支持这样的接口|0x80004002|  
|E\_POINTER|无效的指针|0x80004003|  
|E\_HANDLE|无效处理|0x80070006|  
|E\_ABORT|中止的操作|0x80004004|  
|E\_FAIL|未指定的失败|0x80004005|  
|E\_ACCESSDENIED|泛型拒绝访问错误|0x80070005|  
  
##  <a name="vcconattributeprogrammmingfaqanchor2"></a> 我当必须为特性指定参数名称?  
 在大多数情况下，因此，如果属性具有一个参数，该参数名为。  此名称，在插入属性。代码时，不需要。  例如， [可聚集的](../windows/aggregatable.md) 属性的使用:  
  
```  
[coclass, aggregatable(value=allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 是同一如下所示:  
  
```  
[coclass, aggregatable(allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 但是，下面的特性具有唯一，未命名参数:  
  
||||  
|-|-|-|  
|[call\_as](../windows/call-as.md)|[case](../windows/case-cpp.md)|[cpp\_quote](../windows/cpp-quote.md)|  
|[default](../windows/default-cpp.md)|[defaultvalue](../windows/defaultvalue.md)|[defaultvtable](../windows/defaultvtable.md)|  
|[emitidl](../windows/emitidl.md)|[项](../windows/entry.md)|[first\_is](../windows/first-is.md)|  
|[helpcontext](../windows/helpcontext.md)|[helpfile](../windows/helpfile.md)|[helpstring](../windows/helpstring.md)|  
|[helpstringcontext](../windows/helpstringcontext.md)|[helpstringdll](../windows/helpstringdll.md)|[id](../windows/id.md)|  
|[iid\_is](../windows/iid-is.md)|[import](../windows/import.md)|[importlib](../windows/importlib.md)|  
|[包含](../windows/include-cpp.md)|[includelib](../windows/includelib-cpp.md)|[last\_is](../windows/last-is.md)|  
|[length\_is](../windows/length-is.md)|[max\_is](../windows/max-is.md)|[no\_injected\_text](../windows/no-injected-text.md)|  
|[pointer\_default](../windows/pointer-default.md)|[说明](../windows/pragma.md)|[restricted](../windows/restricted.md)|  
|[size\_is](../windows/size-is.md)|[source](../windows/source-cpp.md)|[switch\_is](../windows/switch-is.md)|  
|[switch\_type](../windows/switch-type.md)|[transmit\_as](../windows/transmit-as.md)|[wire\_marshal](../windows/wire-marshal.md)|  
  
##  <a name="vcconattributeprogrammmingfaqanchor3"></a> 我是否能将注释在特性块?  
 可以使用单行，并在属性中的多行注释块。  但是，不能使用注释任何一个样式位于备用参数的括号内于属性。  
  
 下面这样:  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1"), /* Multiple-line  
                                       comment */  
   threading("both") // Single-line comment  
]  
```  
  
 以下要求:  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1" /* Multiple-line comment */ ),  
   threading("both" // Single-line comment)  
]  
```  
  
##  <a name="vcconattributeprogrammmingfaqanchor4"></a> 属性与继承交互?  
 可继承从其他类的特性化和非特性化类，它们可能已特性化。  ，在属性提供转换其代码后，派生的结果从特性化的类与从派生该类。  属性不传递给派生类通过 C\+\+ 继承。  属性提供程序只转换代码在其特性两旁。  
  
##  <a name="vcconattributeprogrammmingfaqanchor5"></a> 如何使用属性在一个非 ATL 项目?  
 您可能有一个非 ATL 项目，具有 .idl 文件，因此，您可以首先添加特性化的对象。  在这种情况下，使用添加类向导的代码。  
  
##  <a name="vcconattributeprogrammmingfaqanchor6"></a> 如何使用 .idl 文件在一个特性化项目中?  
 您可能会在该 ATL 特性化的项目中使用的 .idl 文件。  在这种情况下，您在项目中使用 [importidl](../windows/importidl.md) 属性，生成 .idl 文件添加到 .h 文件 \(请参见在项目的 " 属性页 " 对话框的 [MIDL 属性页](../ide/midl-property-pages.md) \)，然后包括 .h 文件。  
  
##  <a name="vcconattributeprogrammmingfaqanchor7"></a> 我是否能修改属性插入的代码?  
 某些特性插入代码添加到项目中。  使用 [\/Fx](../build/reference/fx-merge-injected-code.md) 编译器选项，您可以查看插入的代码。  复制代码从注入的文件并将其粘贴到源代码也是可能的。  这使您得以修改属性的行为。  但是，您可能必须修改代码的其他部分。  
  
 下面的示例是复制插入的代码的结果到源代码文件:  
  
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
  
##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> 如何前向声明特性化的界面?  
 如果您使用前向声明特性化的接口，必须将同一特性应用于接口实际声明的前向声明。  您还必须将 [export](../windows/export.md) 特性应用于该前向声明。  
  
##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> 我是否能将在从还可以使用属性的类派生的类的属性?  
 不，在从还可以使用属性的类派生的类的属性不受支持。  
  
## 请参阅  
 [Concepts](../windows/attributed-programming-concepts.md)