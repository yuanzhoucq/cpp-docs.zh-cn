---
title: 模块 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.module
dev_langs:
- C++
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea891ce5ee5c3570577edf7c2122b2cd39b5c64d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378546"
---
# <a name="module-c"></a>module (C++)

定义.Idl 文件中的库块。

## <a name="syntax"></a>语法

```cpp
[ module (
   type=dll,
   name=string,
   version=1.0,
   uuid=uuid,
   lcid=integer,
   control=boolean,
   helpstring=string,
   helpstringdll=string,
   helpfile=string,
   helpcontext=integer,
   helpstringcontext=integer,
   hidden=boolean,
   restricted=boolean,
   custom=string,
   resource_name=string,
) ];
```

### <a name="parameters"></a>参数

*type*<br/>
（可选）可以是以下值之一：

- `dll` 添加函数和类，使产生的 DLL 发挥进程内 COM 服务器。 这是默认值。

- `exe` 添加函数和类，使生成可执行文件发挥进程外 COM 服务器。

- `service` 添加函数和类，使生成可执行文件发挥进程外 NT 服务。

- `unspecified` 禁用相关模块特性的 ATL 代码注入： 注入 ATL Module 类、 全局实例 _AtlModule 和入口点函数。 不要禁用该项目中的其他特性的 ATL 代码注入。

*name*<br/>
（可选）库块的名称。

*version*<br/>
（可选）你想要分配到的库块的版本号。 默认值为 1.0。

*uuid*<br/>
库的唯一 ID。 如果省略此参数，ID 将自动为库生成参数。 可能需要检索*uuid*库块，您可以通过使用标识符来执行此操作 **__uuidof (** *libraryname* **)**。

*lcid*<br/>
本地化参数。 请参阅[lcid](/windows/desktop/Midl/lcid)有关详细信息。

*control*<br/>
（可选）指定库中的所有组件的控件。

*helpstring*<br/>
指定类型库。

*helpstringdll*<br/>
（可选）设置要用于执行文档字符串查找的.dll 文件的名称。 请参阅[helpstringdll](/windows/desktop/Midl/helpstringdll)有关详细信息。

*helpfile*<br/>
（可选）名称**帮助**类型库文件。

*helpcontext*<br/>
（可选）**帮助 ID**该类型库。

*helpstringcontext*<br/>
（可选）请参阅[helpstringcontext](../windows/helpstringcontext.md)有关详细信息。

*hidden*<br/>
（可选）禁止显示整个媒体库。 这种用法与控件一起使用。 主机需要创建新的类型库，该库对控件进行包装，使其具有扩展特性。 请参阅[隐藏](/windows/desktop/Midl/hidden)MIDL 特性的详细信息。

*restricted*<br/>
（可选）不能随意调用库中的成员。 请参阅[受限](/windows/desktop/Midl/restricted)MIDL 特性的详细信息。

*custom*<br/>
（可选）一个或多个属性则它类似于[自定义](../windows/custom-cpp.md)属性。 第一个参数*自定义*是该特性的 GUID。 例如：

```
[module(custom={guid,1}, custom={guid1,2})]
```

*资源名称*<br/>
用 rgs 文件字符串资源 ID 来注册 DLL、可执行文件或服务应用程序的 APP ID。 模块是服务类型模块时，也使用此参数获取包含服务名称的字符串 ID。

> [!NOTE]
> rgs 文件和含服务名称的字符串应包含相同的数字值。

## <a name="remarks"></a>备注

除非指定，否则*受限*参数[emitidl](../windows/emitidl.md)，**模块**中使用 c + + 特性的任何程序所需。

将创建库块，如果除了 **模块** 特性，源代码还使用 [dispinterface](../windows/dispinterface.md)、 [dual](../windows/dual.md)、 [object](../windows/object-cpp.md)或蕴含 [coclass](../windows/coclass.md)的特性。

一个库块只允许一个.idl 文件。 使用正在实施的最新参数值，合并源代码中多个模块条目。

如果在使用 ATL 的项目中使用此属性，该属性的行为将会更改。 除了上述行为，该属性还将插入一个全局对象 (称为`_AtlModule`) 的正确类型和其他支持代码。 如果特性是独立的，它将插入从正确的模块类型中派生出来的类。 如果将该特性应用于类，它将添加正确的模块类型的基本类。 正确的类型确定的值*类型*参数：

- `type` = **dll**

   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) 用作基类，并使用需要 COM 服务器的标准 DLL 入口点。 这些入口点为[DllMain](/windows/desktop/Dlls/dllmain)， [DllRegisterServer](https://msdn.microsoft.com/library/windows/desktop/ms682162)， [DllUnRegisterServer](https://msdn.microsoft.com/library/windows/desktop/ms691457)， [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow)，和[DllGetClassObject](https://msdn.microsoft.com/library/windows/desktop/dd797891)。

- `type` = **exe**

   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md)用作基类和标准可执行文件的入口点[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)。

- `type` = **service**

   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md)用作基类和标准可执行文件的入口点[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)。

- `type` = **unspecified**

   禁用与模块特性相关的 ATL 代码注入。

## <a name="example"></a>示例

下面的代码演示如何在生成的.idl 文件中创建库块。

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

下面的代码将演示可以提供函数的实现，因为使用 **模型**，该函数将在注入代码中显示。 有关查看插入的代码的详细信息，请参阅 [/Fx](../build/reference/fx-merge-injected-code.md) 。 若要重写一项由 **模块** 特性插入的功能，使用包含实现函数的类，并让 **模块** 特性应用到该类。

```cpp
// cpp_attr_ref_module2.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// no semicolon after attribute block
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[类特性](../windows/class-attributes.md)<br/>
[独立特性](../windows/stand-alone-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](../windows/usesgetlasterror.md)<br/>
[库](/windows/desktop/Midl/library)<br/>
[helpcontext](../windows/helpcontext.md)<br/>
[helpstring](../windows/helpstring.md)<br/>
[helpfile](../windows/helpfile.md)<br/>
[version](../windows/version-cpp.md)  