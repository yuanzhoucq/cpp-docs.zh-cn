---
title: 指定 ATL 项目的编译器优化 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
dev_langs:
- C++
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0060437613bcdd6281ce5cceb112f5fd7f470bf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>指定 ATL 项目的编译器优化
默认情况下， [ATL 控件向导](../../atl/reference/atl-control-wizard.md)生成 ATL_NO_VTABLE 宏，使用的新类，如下所示：  
  
```  
class ATL_NO_VTABLE CProjName  
{  
 ...  
};  
```  
  
 ATL 然后定义 _ATL_NO_VTABLE，如下所示：  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
 #define ATL_NO_VTABLE  
#else  
 #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 如果未定义 _ATL_DISABLE_NO_VTABLE，ATL_NO_VTABLE 宏会扩展到`declspec(novtable)`。 使用`declspec(novtable)`类中声明防止 vtable 指针中的类构造函数和析构函数进行初始化。 生成你的项目时，链接器将消除 vtable 和 vtable 所指向的所有函数。  
  
 你必须使用 ATL_NO_VTABLE，并因此`declspec(novtable)`，仅与基类一起使用，不能直接创建。 不能使用`declspec(novtable)`与派生程度最高类在项目中，因为此类 (通常[CComObject](../../atl/reference/ccomobject-class.md)， [CComAggObject](../../atl/reference/ccomaggobject-class.md)，或[CComPolyObject](../../atl/reference/ccompolyobject-class.md))初始化你的项目的 vtable 指针。  
  
 您不能调用虚函数使用的任何对象的构造函数从`declspec(novtable)`。 应将移动到这些调用[FinalConstruct](ccomobjectrootex-class.md#finalconstruct)方法。  

  
 如果您不确定是否应使用`declspec(novtable)`修饰符，你可以从任何类定义中，删除 ATL_NO_VTABLE 宏或者你可以通过指定全局禁止  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 在 stdafx.h 文件中，在所有其他 ATL 之前标头将包含文件。  
  
## <a name="see-also"></a>请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [Visual c + + 项目类型](../../ide/visual-cpp-project-types.md)   
 [使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 运行时代码编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

