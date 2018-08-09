---
title: 组件类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.coclass
dev_langs:
- C++
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2043ca568f36d7fc0eaaffbf940cabb423de5620
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647835"
---
# <a name="coclass"></a>coclass
创建 COM 对象，可以实现 COM 接口。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[coclass]  
```  
  
## <a name="remarks"></a>备注  
 **组件类**c + + 属性置于生成的.idl 文件中组件类构造。  
  
 在定义组件类时，还可以指定[uuid](../windows/uuid-cpp-attributes.md)，[版本](../windows/version-cpp.md)，[线程](../windows/threading-cpp.md)， [vi_progid](../windows/vi-progid.md)，和[progid](../windows/progid.md)属性。 如果未指定其中的任意一个，它将生成。  
  
 如果两个标头文件包含具有类**组件类**属性，且不指定一个 GUID，则编译器将为这两个类，使用相同的 GUID，这样将导致 MIDL 错误。  因此，应使用`uuid`属性使用时**组件类**。  
  
 **ATL 项目**  
  
 当此属性在 ATL 项目中，优先于类或结构定义它：  
  
-   将插入代码或数据，以支持自动注册的对象。  
  
-   将插入代码或数据，以支持的对象的 COM 类工厂。  
  
-   注入代码或数据以实现`IUnknown`并使该对象可创建 COM 对象的对象。  
  
 具体而言，以下基类添加到目标对象：  
  
-   [CComCoClass 类](../atl/reference/ccomcoclass-class.md)为对象提供的默认类工厂和聚合模型。  
  
-   [CComObjectRootEx 类](../atl/reference/ccomobjectrootex-class.md)具有基于指定的线程处理模型类模板[线程](../windows/threading-cpp.md)属性。 如果`threading`属性未指定，默认线程模型是单元。  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md)如果添加[noncreatable](../windows/noncreatable.md)属性未指定目标对象。  
  
 最后，使用嵌入的 IDL 不定义任何双重接口将替换为相应[IDispatchImpl](../atl/reference/idispatchimpl-class.md)类。 如果嵌入的 IDL 中的双重接口定义，则不会修改基列表中的特定接口。  
  
 **组件类**属性还提供以下函数通过插入的代码，或在的用例`GetObjectCLSID`，作为基类中的静态方法`CComCoClass`:  
  
-   `UpdateRegistry` 注册目标类的类工厂。  
  
-   `GetObjectCLSID`这与注册，还可用来获取目标类的 CLSID。  
  
-   `GetObjectFriendlyName` 默认情况下返回的格式字符串"\<*目标类名*> `Object`"。 如果此函数已存在，未添加。 将此函数添加到目标类，以返回更友好的名称比自动生成。  
  
-   `GetProgID`这与注册，将返回与指定的字符串[progid](../windows/progid.md)属性。  
  
-   `GetVersionIndependentProgID` 具有相同的功能`GetProgID`，但它会返回与指定的字符串[vi_progid](../windows/vi-progid.md)。  
  
 对目标类进行以下更改，与 COM 映射：  
  
-   COM 映射添加了目标类派生的所有接口的条目和由指定的所有条目[COM 接口入口点](../mfc/com-interface-entry-points.md)属性或所需的那些[聚合](../windows/aggregates.md)属性。  
  
-   [OBJECT_ENTRY_AUTO](../atl/reference/object-map-macros.md#object_entry_auto)宏插入到 COM 映射。
  
 生成类的.idl 文件中组件类的名称将具有与类相同的名称。  例如，并且引用下面的示例，若要访问用于 coclass 的类 ID `CMyClass`，在通过 MIDL 生成的标头文件在客户端，使用`CLSID_CMyClass`。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用**组件类**属性：  
  
```cpp  
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
  
 下面的示例演示如何重写由注入代码中出现的函数的默认实现**组件类**属性。 有关查看插入的代码的详细信息，请参阅 [/Fx](../build/reference/fx-merge-injected-code.md) 。 任何基类或接口，使用的类将出现在注入的代码。 此外，如果您显式指定此类作为基在组件类的类包括在注入的代码默认情况下，特性提供程序将使用在代码中指定的窗体。  
  
```cpp  
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
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**，**结构**|  
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