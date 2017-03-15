---
title: "coclass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.coclass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "coclass attribute"
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# coclass
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建 COM 对象，可以实现 COM 接口。  
  
## 语法  
  
```  
  
[coclass]  
  
```  
  
## 备注  
 **coclass** C\+\+ 特性在生成的 .idl 文件放置在 coclass 构造。  
  
 当定义 coclass 时，还可以指定 [uuid](../windows/uuid-cpp-attributes.md)、 [版本](../windows/version-cpp.md)、 [线程处理](../windows/threading-cpp.md)、 [vi\_progid](../windows/vi-progid.md)和 [progid](../windows/progid.md) 属性。  如果将其中的任何一个未指定，则将生成。  
  
 如果两个头文件包含与 **coclass** 属性的类，而不指定 GUID，编译器为两个类都将使用相同的 GUID，并且，这会导致的错误。  因此，那么，当您使用 **coclass**时，应使用 `uuid` 属性。  
  
 **ATL 项目**  
  
 当此特性前面在 ATL 项目的类或结构定义，则:  
  
-   插入代码或数据支持对象的自动注册。  
  
-   插入代码或数据支持对象的一个 COM 类工厂。  
  
-   插入代码或数据实现 **IUnknown** 并将对象 COMcreatable 对象。  
  
 具体而言，以下基类添加到目标对象:  
  
-   [CComCoClass 类](../atl/reference/ccomcoclass-class.md) 为对象提供默认类工厂和摘要模型。  
  
-   [CComObjectRootEx 类](../atl/reference/ccomobjectrootex-class.md) 具有基于线程模型类的一个模板以指定由 [线程处理](../windows/threading-cpp.md) 属性。  如果 **线程处理** 未指定属性，默认线程模型是单元。  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md) 添加 [不可创建](../windows/noncreatable.md) 属性是否没有为目标对象指定。  
  
 最后，未定义使用嵌入 IDL 的所有双重接口用相应的 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 类来替换。  如果双重接口在嵌入的 IDL 中定义，在基础的特定接口列表不会被修改。  
  
 **coclass** 属性还使以下功能可通过注入的代码，但如果 `GetObjectCLSID`，用作静态方法在基类 `CComCoClass`:  
  
-   该 目标的类工厂类的`UpdateRegistry` 注册。  
  
-   `GetObjectCLSID`，与注册相关，还可用于获取目标类的 CLSID。  
  
-   默认情况下**GetObjectFriendlyName** 返回该格式 “AMP\_LTtarget*类 nameAMP\_GT*`Object`”的字符串。  如果此功能已存在，不会添加。  比自动生成的控件将此功能添加到目标类返回一个更友好的名称。  
  
-   **GetProgID**，与注册相关，返回字符串指定与 [progid](../windows/progid.md) 属性。  
  
-   **GetVersionIndependentProgID** 具有与 **GetProgID**相同，但是，它返回字符串指定与 [vi\_progid](../windows/vi-progid.md)。  
  
 以下更改，与 COM 映射相关，对目标类:  
  
-   COM 映射添加与目标类派生自的任何接口的项，并且所有项。 [COM 接口的入口点](../mfc/com-interface-entry-points.md) 属性指定了或那些由 [聚合](../windows/aggregates.md) 属性要求。  
  
-   [OBJECT\_ENTRY\_AUTO](../Topic/OBJECT_ENTRY_AUTO.md) 宏插入到 COM 映射。  此宏类似于 [OBJECT\_ENTRY](http://msdn.microsoft.com/zh-cn/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) 基于功能，但不必是目标类的 COM 映射的一部分。  
  
 在类的 .idl 文件中生成的 coclass 的名称将与类相同。  例如，并参考以下示例，访问的类 ID 在客户端的 coclass CMyClass，通过使用 MIDL 生成的头文件，使用 CLSID\_CMyClass。  
  
## 示例  
 下面的代码演示如何使用 **coclass** 属性:  
  
```  
// cpp_attr_ref_coclass1.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[ object, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface I {  
   HRESULT func();  
};  
  
[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),   
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]  
class CMyClass : public I {};  
```  
  
 下面的示例演示如何重写出现在 **coclass** 属性插入的代码功能的默认实现。  请参见 [\/Fx](../build/reference/fx-merge-injected-code.md) 有关查看插入的代码的更多信息。  为类使用的所有基类或接口将会显示插入的代码。   此外，默认情况下，如果类在插入的代码包含，并且您显式指定该类为基础。 coclass，属性提供程序将在代码中使用指定的窗体。  
  
```  
// cpp_attr_ref_coclass2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface bb {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class CMyClass : public bb {  
public:  
   // by adding the definition of UpdateRegistry to your code,   
   // the function will not be included in the injected code  
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {  
      // you can add to the default implementation  
      CRegistryVirtualMachine rvm;  
      HRESULT hr;  
      if (FAILED(hr = rvm.AddStandardReplacements()))  
         return hr;  
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());  
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),  
         GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);  
   }  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject](../windows/appobject.md)