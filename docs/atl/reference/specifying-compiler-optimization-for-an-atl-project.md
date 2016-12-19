---
title: "为 ATL 项目指定编译器优化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.optimization"
  - "vc.appwiz.ATL.vtable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 编译器优化"
  - "ATL_DISABLE_NO_VTABLE 宏"
  - "ATL_NO_VTABLE 宏"
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 为 ATL 项目指定编译器优化
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

默认情况下，[ATL 控件向导](../../atl/reference/atl-control-wizard.md)生成具有 ATL\_NO\_VTABLE 宏的新类，如下所示：  
  
```  
class ATL_NO_VTABLE CProjName  
{  
   ...  
};  
```  
  
 然后，ATL 如下定义 \_ATL\_NO\_VTABLE：  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
   #define ATL_NO_VTABLE  
#else  
   #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 如果不定义 \_ATL\_DISABLE\_NO\_VTABLE，则 ATL\_NO\_VTABLE 宏扩展到 `declspec(novtable)`。  在类声明中使用 `declspec(novtable)` 可防止 vtable 指针在类构造函数和析构函数中被初始化。  当生成项目时，链接器消除 vtable 和 vtable 指向的所有函数。  
  
 ATL\_NO\_VTABLE（因此是 `declspec(novtable)`）必须只能与一个无法直接创建的基类一起使用。  在项目中一定不能将 `declspec(novtable)` 与基本上是导出的类一起使用，因为该类（通常是 [CComObject](../../atl/reference/ccomobject-class.md)、[CComAggObject](../../atl/reference/ccomaggobject-class.md) 或 [CComPolyObject](../../atl/reference/ccompolyobject-class.md)）为项目初始化 vtable 指针。  
  
 一定不能从任何使用 `declspec(novtable)` 的对象的构造函数调用虚函数。  应该将那些调用移动到 [FinalConstruct](../Topic/CComObjectRootEx::FinalConstruct.md) 方法。  
  
 如果不能确定是否应该使用 `declspec(novtable)` 修饰符，则在包括所有其他 ATL 头文件之前，可以从任何类定义中移除 ATL\_NO\_VTABLE 宏，或者可以通过在 stdafx.h 中指定  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 全局禁用 ATL\_NO\_VTABLE 宏。  
  
## 请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [Visual C\+\+ 项目类型](../../ide/visual-cpp-project-types.md)   
 [使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)