---
title: coclass （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: 0a47f4f503541f9dee67dd8c6cf10297de724a19
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232789"
---
# <a name="coclass"></a>coclass

创建可实现 COM 接口的 COM 对象。

## <a name="syntax"></a>语法

```cpp
[coclass]
```

## <a name="remarks"></a>备注

**Coclass** c + + 特性在生成的 .idl 文件中放置组件类构造。

定义 coclass 时，还可以指定 " [uuid](uuid-cpp-attributes.md)"、"[版本](version-cpp.md)"、"[线程](threading-cpp.md)"、" [vi_progid](vi-progid.md)" 和 " [progid](progid.md) " 属性。 如果未指定任何一个，则将生成该文件。

如果两个标头文件包含具有**coclass**特性的类，但未指定 guid，则编译器将对这两个类使用相同的 guid，这将导致 MIDL 错误。  因此， `uuid` 使用**coclass**时应使用特性。

**ATL 项目**

当此属性在 ATL 项目中的类或结构定义之前时，它：

- 注入用于支持对象自动注册的代码或数据。

- 注入用于支持对象的 COM 类工厂的代码或数据。

- 注入要实现的代码或数据 `IUnknown` ，并使该对象成为可通过 COM 创建的对象。

具体而言，以下基类将添加到目标对象：

- [CComCoClass 类](../../atl/reference/ccomcoclass-class.md)提供对象的默认类工厂和聚合模型。

- [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)具有一个[基于线程化属性指定](threading-cpp.md)的线程模型类的模板。 如果 `threading` 未指定属性，则默认线程模型为单元。

- 如果没有为目标对象指定[noncreatable](noncreatable.md)属性，则会添加[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) 。

最后，使用嵌入的 IDL 未定义的任何双重接口都将替换为相应的[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)类。 如果双重接口在嵌入的 IDL 中定义，则不会修改基列表中的特定接口。

**Coclass**特性还使以下函数可通过插入的代码提供或 `GetObjectCLSID` 作为基类中的静态方法提供 `CComCoClass` ：

- `UpdateRegistry`注册目标类的类工厂。

- `GetObjectCLSID`与注册相关的，还可用于获取目标类的 CLSID。

- `GetObjectFriendlyName`默认情况下，返回 "" 格式的字符串 \<*target class name*> `Object` 。 如果此函数已存在，则不会添加它。 将此函数添加到目标类，以返回比自动生成的名称更友好的名称。

- `GetProgID`与注册相关的，返回用[progid](progid.md)特性指定的字符串。

- `GetVersionIndependentProgID`具有与相同的功能 `GetProgID` ，但它返回[vi_progid](vi-progid.md)指定的字符串。

以下与 COM 映射相关的更改将与目标类建立关联：

- 将添加一个 COM 映射，其中包含目标类派生自的所有接口的条目，以及由[COM 接口入口点](../../mfc/com-interface-entry-points.md)属性指定的所有条目，以及 "[聚合](aggregates.md)" 属性所需的所有条目。

- 将[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)宏插入 COM 映射。

类的 .idl 文件中生成的 coclass 名称将与类具有相同的名称。  例如，若要 `CMyClass` 通过 MIDL 生成的标头文件在客户端中访问组件类的类 ID，并参考以下示例，请使用 `CLSID_CMyClass` 。

## <a name="example"></a>示例

下面的代码演示如何使用**coclass**特性：

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

下面的示例演示如何重写**组件类**特性注入的代码中显示的函数的默认实现。 有关查看插入的代码的详细信息，请参阅 [/Fx](../../build/reference/fx-merge-injected-code.md) 。 用于类的任何基类或接口都将出现在注入的代码中。 此外，如果默认情况下在注入的代码中包含一个类，并将该类显式指定为组件类的基项，则属性提供程序将使用你在代码中指定的窗体。

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
   // by adding the definition of UpdateRegistry to your code, // the function will not be included in the injected code
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {
      // you can add to the default implementation
      CRegistryVirtualMachine rvm;
      HRESULT hr;
      if (FAILED(hr = rvm.AddStandardReplacements()))
         return hr;
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),       GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);
   }
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**`class`**, **`struct`**|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[COM 特性](com-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)
