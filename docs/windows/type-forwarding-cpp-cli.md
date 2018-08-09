---
title: 类型转发 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- type forwarding, Visual C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 627b0a881795a963e3739accc351ee684b7b8232
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644929"
---
# <a name="type-forwarding-ccli"></a>类型转发 (C++/CLI)
*类型转发*，可将移动一个类型从一个程序集 （程序集 A） 到另一个程序集 （程序集 B），这样一来，不需要重新编译客户端使用程序集 a。  
  
## <a name="all-platforms"></a>所有平台  
 在所有运行时中不支持此功能。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 在 Windows 运行时中不支持此功能。  
  
### <a name="requirements"></a>要求  
 编译器选项：`/ZW`  
  
## <a name="common-language-runtime"></a>公共语言运行时  
 下面的代码示例演示如何使用类型转发。  
  
### <a name="syntax"></a>语法  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### <a name="parameters"></a>参数  
 *new*  
 要在其中移动的类型定义程序集。  
  
 *type*  
 要移动到另一个程序集其定义的类型。  
  
### <a name="remarks"></a>备注  
 后 （程序集） 的组件提供，使用客户端应用程序，可以使用类型转发将类型从组件 （程序集） 移到另一个程序集，提供更新的组件 （和任何所需的其他程序集） 和客户端应用程序仍无正在重新编译。  
  
 类型转发仅适用于现有的应用程序被引用的组件。 当您重新生成应用程序时，必须在应用程序中使用的所有类型的适当的程序集引用。  
  
 在从程序集转发类型 （类型 A），你必须添加`TypeForwardedTo`为程序集引用或该类型的属性。 引用的程序集必须包含以下项之一：  
  
-   类型 a 定义  
  
-   一个`TypeForwardedTo`为类型 A 和程序集引用的属性。  
  
 可将它们转发的类型的示例包括：  
  
-   ref 类  
  
-   值类  
  
-   枚举  
  
-   接口  
  
 不能转发以下类型：  
  
-   泛型类型  
  
-   本机类型  
  
-   嵌套类型 （如果你想要将嵌套的类型转发，应转发的封闭类型）  
  
 可以将类型转发到在任何面向公共语言运行时的语言中编写的程序集。  
  
 因此，如果用于生成 A.dll 的程序集源代码文件包含的类型定义 (`ref class MyClass`)，以及你要以移动该类型定义中的对程序集 B.dll，需要：  
  
1.  移动`MyClass`类型定义用于生成 B.dll 源代码文件。  
  
2.  生成程序集 B.dll  
  
3.  删除`MyClass`类型的源代码，用于生成 A.dll，并将其替换为以下定义：  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  生成 A.dll 的程序集。  
  
5.  无需重新编译客户端应用程序使用 A.dll。  
  
### <a name="requirements"></a>要求  
 编译器选项：`/clr`