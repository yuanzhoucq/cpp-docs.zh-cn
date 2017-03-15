---
title: "指定的 ATL 项目的编译器优化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: abdad4367e75c1971ba5d11af1a60992d1bb3dd4
ms.lasthandoff: 02/24/2017

---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>指定编译器优化为 ATL 项目
默认情况下， [ATL 控件向导](../../atl/reference/atl-control-wizard.md)生成与 ATL_NO_VTABLE 宏的新类，如下所示︰  
  
```  
class ATL_NO_VTABLE CProjName  
{  
 ...  
};  
```  
  
 ATL 然后定义了 _ATL_NO_VTABLE，如下所示︰  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
 #define ATL_NO_VTABLE  
#else  
 #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 如果未定义 _ATL_DISABLE_NO_VTABLE，ATL_NO_VTABLE 宏将扩展为`declspec(novtable)`。 使用`declspec(novtable)`类中声明可防止 vtable 指针在类构造函数和析构函数中初始化。 当生成项目时，链接器将消除 vtable 和 vtable 所指向的所有函数。  
  
 您必须使用 ATL_NO_VTABLE，进而`declspec(novtable)`，与仅基类，这些类不能直接创建。 您不能使用`declspec(novtable)`使用派生程度最高类在项目中，因为此类 (通常[CComObject](../../atl/reference/ccomobject-class.md)， [CComAggObject](../../atl/reference/ccomaggobject-class.md)，或[CComPolyObject](../../atl/reference/ccompolyobject-class.md)) 为你的项目对 vtable 指针进行初始化。  
  
 您不能调用虚函数使用的任何对象的构造函数中`declspec(novtable)`。 您应该将移到这些调用[FinalConstruct](ccomobjectrootex-class.md#finalconstruct)方法。  

  
 如果您不确定是否应使用`declspec(novtable)`修饰符，您可以从任何类定义中，删除 ATL_NO_VTABLE 宏或者也可以通过指定全局禁用  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 在 stdafx.h 文件中，在所有其他 ATL 之前将包含头文件。  
  
## <a name="see-also"></a>另请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [Visual c + + 项目类型](../../ide/visual-cpp-project-types.md)   
 [使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)


