---
title: 模块 （c + +） |Microsoft 文档
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
ms.openlocfilehash: ce7925fd15a7a332dbfb18e2a22dc104783300b7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882506"
---
# <a name="module-c"></a>module (C++)
定义.Idl 文件中的库块。  
  
## <a name="syntax"></a>语法  
  
```  
  
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
  
#### <a name="parameters"></a>参数  
 ***类型***  （可选）  
 可以是以下各项之一：  
  
-   **dll** 添加函数和类，使产生的 DLL 发挥进程内 COM 服务器的功能。 这是默认值。  
  
-   **exe** 添加函数和类，使生成的可执行文件发挥进程外 COM 服务器的功能。  
  
-   **service** 添加函数和类，使生成的可执行文件发挥进程外 NT 服务的功能。  
  
-   **unspecified** 禁用相关模块特性的 ATL 代码注入：注入 ATL Module 类、全局实例_AtlModule 和入口点函数。  不要禁用该项目中的其他特性的 ATL 代码注入。  
  
 ***名称***  （可选）  
 库块的名称。  
  
 ***版本***  （可选）  
 想要分配到库块的版本号。 默认值为 1.0。  
  
 `uuid`  
 库的唯一 ID。 如果省略此参数，ID 将自动为库生成参数。 你可能需要检索*uuid*你的库块，则你可以使用的标识符 **__uuidof (***libraryname***)**。  
  
 **lcid**  
 本地化参数。 有关详细信息，请参阅 [lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) 。  
  
 **控件** （可选）  
 指定库中的所有组件为控件。  
  
 **helpstring**  
 指定类型库。  
  
 ***helpstringdll***  （可选）  
 设置要用于执行文档字符串查找的.dll 文件名称。 有关详细信息，请参阅 [helpstringdll](http://msdn.microsoft.com/library/windows/desktop/aa366860) 。  
  
 **帮助文件** （可选）  
 类型库的帮助文件名称。  
  
 **helpcontext** （可选）  
 该类型库的帮助 ID。  
  
 **helpstringcontext** （可选）  
 有关详细信息，请参阅 [helpstringcontext](../windows/helpstringcontext.md) 。  
  
 **隐藏** （可选）  
 禁止显示整个媒体库。 这种用法与控件一起使用。 主机需要创建新的类型库，该库对控件进行包装，使其具有扩展特性。 更多详细信息，请参阅 [隐藏](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL 特性。  
  
 **受限** （可选）  
 不能随意调用库中的成员。 更多详细信息，请参阅 [受限](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL 特性。  
  
 ***自定义***  （可选）  
 一个或多个特性；这类似于 [自定义](../windows/custom-cpp.md) 特性。 到 `custom` 的第一个参数是该特性的 GUID。 例如：  
  
```  
[module(custom={guid,1}, custom={guid1,2})]  
```  
  
 **resource_name**  
 用 rgs 文件字符串资源 ID 来注册 DLL、可执行文件或服务应用程序的 APP ID。 模块是服务类型模块时，也使用此参数获取包含服务名称的字符串 ID。  
  
> [!NOTE]
>  rgs 文件和含服务名称的字符串应包含相同的数字值。  
  
## <a name="remarks"></a>备注  
 除非指定 **受限** 参数为 [emitidl](../windows/emitidl.md)，在使用 c + + 特性的任何程序时， **模块** 是必须的。  
  
 将创建库块，如果除了 **模块** 特性，源代码还使用 [dispinterface](../windows/dispinterface.md)、 [dual](../windows/dual.md)、 [object](../windows/object-cpp.md)或蕴含 [coclass](../windows/coclass.md)的特性。  
  
 一个库块只允许一个.idl 文件。 使用正在实施的最新参数值，合并源代码中多个模块条目。  
  
 如果在使用 ATL 的项目中使用此属性，该属性的行为将会更改。 除了上述行为，该特性还将插入正确类型和其他支持代码的全局对象（称为 **_AtlModule**）。 如果特性是独立的，它将插入从正确的模块类型中派生出来的类。 如果将该特性应用于类，它将添加正确的模块类型的基本类。 正确类型由 `type` 参数的值决定：  
  
-   `type` = **dll**  
  
     [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) 用作基类，并使用需要 COM 服务器的标准 DLL 入口点。 这些入口点为 [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583)、 [DllRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms682162)、 [DllUnRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms691457)/ [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368)和 [DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/dd797891)。  
  
-   `type` = **exe**  
  
     [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) 用作基类和标准可执行文件的入口点 [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559)。  
  
-   `type` = **service**  
  
     [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) 用作基类和标准可执行文件的入口点 [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559)。  
  
-   `type` = **unspecified**  
  
     禁用与模块特性相关的 ATL 代码注入。  
  
## <a name="example"></a>示例  
 下面的代码演示如何在生成的.idl 文件中创建库块。  
  
```  
// cpp_attr_ref_module1.cpp  
// compile with: /LD  
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];  
```  
  
 下面的代码将演示可以提供函数的实现，因为使用 **模型**，该函数将在注入代码中显示。 有关查看插入的代码的详细信息，请参阅 [/Fx](../build/reference/fx-merge-injected-code.md) 。 若要重写一项由 **模块** 特性插入的功能，使用包含实现函数的类，并让 **模块** 特性应用到该类。  
  
```  
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
 [IDL 特性](../windows/idl-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [独立特性](../windows/stand-alone-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [usesgetlasterror](../windows/usesgetlasterror.md)   
 [库](http://msdn.microsoft.com/library/windows/desktop/aa367069)   
 [helpcontext](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   
 [Helpfile](../windows/helpfile.md)   
 [version](../windows/version-cpp.md)   
