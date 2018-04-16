---
title: "组件类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.coclass
dev_langs:
- C++
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6bcae762c603f05ce11eae5d14eb2e182c666797
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="coclass"></a>coclass
创建 COM 对象，可以实现 COM 接口。  
  
## <a name="syntax"></a>语法  
  
```  
  
[coclass]  
  
```  
  
## <a name="remarks"></a>备注  
 **组件类**c + + 特性将组件类构造放置在生成的.idl 文件。  
  
 在定义组件类时，你还可以指定[uuid](../windows/uuid-cpp-attributes.md)，[版本](../windows/version-cpp.md)，[线程处理](../windows/threading-cpp.md)， [vi_progid](../windows/vi-progid.md)，和[progid](../windows/progid.md)属性。 如果未指定任何之一，它将生成。  
  
 如果两个标头文件包含具有类**组件类**特性并不指定的 GUID，编译器将为这两个类，使用相同的 GUID，这将导致 MIDL 错误。  因此，应使用`uuid`属性使用时**组件类**。  
  
 **ATL 项目**  
  
 当此属性之前在 ATL 项目中，一个类或结构定义时它：  
  
-   插入的代码或数据以支持自动注册的对象。  
  
-   插入代码或数据，从而为该对象支持的 COM 类工厂。  
  
-   插入的代码或数据以实现**IUnknown**并使该对象可创建的 COM 对象。  
  
 具体而言，以下基类添加到目标对象：  
  
-   [CComCoClass 类](../atl/reference/ccomcoclass-class.md)为对象提供默认类工厂和聚合模型。  
  
-   [CComObjectRootEx 类](../atl/reference/ccomobjectrootex-class.md)具有基于指定的线程处理模型类模板[线程处理](../windows/threading-cpp.md)属性。 如果**线程处理**属性未指定，则默认线程模型是单元。  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md)如果添加[noncreatable](../windows/noncreatable.md)属性未指定目标对象。  
  
 最后，使用嵌入的 IDL 不定义任何双重接口将替换为相应[IDispatchImpl](../atl/reference/idispatchimpl-class.md)类。 如果嵌入的 IDL 中定义了双重接口，则不会修改的基础列表中的特定接口。  
  
 **组件类**属性还提供以下函数通过插入的代码，或在的情况下`GetObjectCLSID`，作为基类中的静态方法`CComCoClass`:  
  
-   `UpdateRegistry`注册的目标类的类工厂。  
  
-   `GetObjectCLSID`这与注册，还可用来获取目标类的 CLSID。  
  
-   **GetObjectFriendlyName**默认情况下返回的格式字符串"\<*目标类名称*> `Object`"。 如果已存在此函数，则不添加。 将此函数添加到目标类，以返回比自动生成的一个更友好的名称。  
  
-   **GetProgID**，这与注册相关，返回与指定的字符串[progid](../windows/progid.md)属性。  
  
-   **GetVersionIndependentProgID**具有与相同的功能**GetProgID**，但它将返回与指定的字符串[vi_progid](../windows/vi-progid.md)。  
  
 对目标类进行到 COM 映射相关的以下更改：  
  
-   COM 映射添加与目标类派生自的所有接口的条目和指定的所有项[COM 接口入口点](../mfc/com-interface-entry-points.md)属性或所需要的那些[聚合](../windows/aggregates.md)属性。  
  
-   [OBJECT_ENTRY_AUTO](../atl/reference/object-map-macros.md#object_entry_auto)宏插入到 COM 映射。
  
 在类的.idl 文件中生成的组件类的名称将具有与类相同的名称。  例如，并且引用下面的示例，若要访问组件类的类 ID CMyClass，通过 MIDL 生成的标头文件中，客户端中使用 CLSID_CMyClass。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用**组件类**属性：  
  
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
  
 下面的示例演示如何重写的函数，通过将插入的代码中出现的默认实现**组件类**属性。 有关查看插入的代码的详细信息，请参阅 [/Fx](../build/reference/fx-merge-injected-code.md) 。 在注入的代码，将显示任何基类或接口的类使用。   此外，如果你显式指定该类作为基你组件类的类包括默认情况下，在注入的代码，属性提供程序将使用你的代码中指定窗体。  
  
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
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**， `struct`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [COM 特性](../windows/com-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject](../windows/appobject.md)