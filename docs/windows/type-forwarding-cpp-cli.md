---
title: 类型转发 (C + + /cli CLI) |Microsoft 文档
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
ms.openlocfilehash: 9caa2e18a1ec851967857eb068797e092835f587
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891087"
---
# <a name="type-forwarding-ccli"></a>类型转发 (C++/CLI)
*类型转发*允许你将移动一种类型从一个程序集 （程序集 A） 到另一个程序集 （程序集 B），以便不需要重新编译使用程序集 A.的客户端  
  
## <a name="all-platforms"></a>所有平台  
 所有运行时不支持此功能。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 在 Windows 运行时中不支持此功能。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时  
 下面的代码示例演示如何使用类型转发。  
  
### <a name="syntax"></a>语法  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### <a name="parameters"></a>参数  
 `new`  
 要向其中移动类型定义的程序集。  
  
 `type`  
 要移动到另一个程序集其定义的类型。  
  
### <a name="remarks"></a>备注  
 后一个组件 （程序集） 附带，客户端应用程序使用，你可以使用类型转发若要从组件 （程序集） 的类型移到另一个程序集，请提供更新的组件 （和所需的任何其他程序集） 和客户端应用程序仍将没有正在重新编译正常进行。  
  
 类型转发仅适用于引用的现有应用程序的组件。 当你重新生成应用程序时，必须使用应用程序中的所有类型的适当的程序集引用。  
  
 （A 类型） 将类型转发从程序集，则必须将添加`TypeForwardedTo`该类型，以及程序集引用的属性。 引用的程序集必须包含以下项之一：  
  
-   类型 a 定义  
  
-   A`TypeForwardedTo`类型 A，以及程序集引用的属性。  
  
 可以将其转发的类型的示例包括：  
  
-   ref 类  
  
-   值类  
  
-   枚举  
  
-   接口  
  
 不能转发以下类型：  
  
-   泛型类型  
  
-   本机类型  
  
-   嵌套类型 （如果你想要转发的嵌套的类型，应转发封闭类型）  
  
 可以将类型转发到任何面向公共语言运行时的语言编写的程序集。  
  
 因此，如果用于生成程序集 A.dll 源代码文件包含的类型定义 (`ref class MyClass`)，并且希望将该类型移到程序集 B.dll 的定义，你将：  
  
1.  移动`MyClass`类型对用于生成 B.dll 源代码文件的定义。  
  
2.  生成程序集 B.dll  
  
3.  删除`MyClass`类型从源代码中用于生成 A.dll，并将其替换为以下定义：  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  生成程序集 A.dll。  
  
5.  无需重新编译客户端应用程序使用 A.dll。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**