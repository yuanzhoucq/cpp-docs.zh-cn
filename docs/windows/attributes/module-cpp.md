---
title: 模块（C++ COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: 9d4f9e23aaf182e28930ba3a4462b07533ba9015
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754375"
---
# <a name="module-c"></a>module (C++)

定义.Idl 文件中的库块。

## <a name="syntax"></a>语法

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>参数

type <br/>
（可选）可以是以下项之一：

- `dll`添加允许生成的 DLL 充当进程内 COM 服务器的函数和类。 这是默认值。

- `exe`添加允许生成的可执行文件的函数和类作为进程外 COM 服务器运行。

- `service`添加允许生成的可执行文件的函数和类作为 NT 服务运行。

- `unspecified`禁用与模块属性相关的 ATL 代码的注入：ATL 模块类的注入、全局实例_AtlModule和入口点函数。 不要禁用该项目中的其他特性的 ATL 代码注入。

name <br/>
（可选）库块的名称。

*version*<br/>
（可选）要分配给库块的版本号。 默认值为 1.0。

*uuid*<br/>
库的唯一 ID。 如果省略此参数，ID 将自动为库生成参数。 可能需要检索库块中的 *uuid* ，可以通过使用标识符 **__uuidof (** *libraryname* **)** 来执行此操作。

*lcid*<br/>
本地化参数。 有关详细信息，请参阅 [lcid](/windows/win32/Midl/lcid) 。

*控制*<br/>
（可选）指定库中的所有子类都是控件。

*helpstring*<br/>
指定类型库。

*helpstringdll*<br/>
（可选）设置 .dll 文件的名称，以便用于执行文档字符串查找。 有关详细信息，请参阅 [helpstringdll](/windows/win32/Midl/helpstringdll) 。

*帮助文件*<br/>
（可选）类型**库的帮助文件**的名称。

*helpcontext*<br/>
（可选）此类型库**的帮助 ID。**

*helpstringcontext*<br/>
（可选）有关详细信息，请参阅[帮助字符串上下文](helpstringcontext.md)。

*隐藏*<br/>
（可选）防止显示整个库。 这种用法与控件一起使用。 主机需要创建新的类型库，该库对控件进行包装，使其具有扩展特性。 更多详细信息，请参阅 [隐藏](/windows/win32/Midl/hidden) MIDL 特性。

*限制*<br/>
（可选）不能任意调用库的成员。 更多详细信息，请参阅 [受限](/windows/win32/Midl/restricted) MIDL 特性。

*自 定义*<br/>
（可选）一个或多个属性;这与[自定义](custom-cpp.md)属性类似。 *要自定义*的第一个参数是属性的 GUID。 例如：

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
用 rgs 文件字符串资源 ID 来注册 DLL、可执行文件或服务应用程序的 APP ID。 模块是服务类型模块时，也使用此参数获取包含服务名称的字符串 ID。

> [!NOTE]
> rgs 文件和含服务名称的字符串应包含相同的数字值。

## <a name="remarks"></a>备注

除非指定 *受限* 参数为 [emitidl](emitidl.md)，在使用 c + + 特性的任何程序时， **模块** 是必须的。

将创建库块，如果除了 **模块** 特性，源代码还使用 [dispinterface](dispinterface.md)、 [dual](dual.md)、 [object](object-cpp.md)或蕴含 [coclass](coclass.md)的特性。

一个库块只允许一个.idl 文件。 使用正在实施的最新参数值，合并源代码中多个模块条目。

如果在使用 ATL 的项目中使用此属性，该属性的行为将会更改。 除了上述行为外，该属性还插入正确类型的全局对象 （称为`_AtlModule`） 和其他支持代码。 如果特性是独立的，它将插入从正确的模块类型中派生出来的类。 如果将该特性应用于类，它将添加正确的模块类型的基本类。 正确的类型由*类型*参数的值确定：

- `type` = **Dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) 用作基类，并使用需要 COM 服务器的标准 DLL 入口点。 这些入口点为 [DllMain](/windows/win32/Dlls/dllmain)、 [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver)、 [DllUnRegisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver)/ [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)和 [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject)。

- `type` = **Exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) 用作基类和标准可执行文件的入口点 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)。

- `type` = **服务**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) 用作基类和标准可执行文件的入口点 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)。

- `type` = **未指定**

   禁用与模块特性相关的 ATL 代码注入。

## <a name="example"></a>示例

下面的代码演示如何在生成的.idl 文件中创建库块。

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

下面的代码将演示可以提供函数的实现，因为使用 **模型**，该函数将在注入代码中显示。 有关查看插入的代码的详细信息，请参阅 [/Fx](../../build/reference/fx-merge-injected-code.md) 。 若要重写一项由 **模块** 特性插入的功能，使用包含实现函数的类，并让 **模块** 特性应用到该类。

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
|**重复**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[图书馆](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[帮助文件](helpfile.md)<br/>
[version](version-cpp.md)
