---
title: "Compiler Options Macros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "编译器选项, 宏"
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# Compiler Options Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些宏管理特定编译器功能。  
  
|||  
|-|-|  
|[\_ATL\_ALL\_WARNINGS](../Topic/_ATL_ALL_WARNINGS.md)|启用项目中的错误的符号从ATL的早期版本转换为。|  
|[\_ATL\_APARTMENT\_THREADED](../Topic/_ATL_APARTMENT_THREADED.md)|如果一个或多个对象所使用单元线程处理，请定义。|  
|[\_ATL\_CSTRING\_EXPLICIT\_CONSTRUCTORS](../Topic/_ATL_CSTRING_EXPLICIT_CONSTRUCTORS.md)|确定 `CString` 构造函数显式的，使所有意外的转换。|  
|[\_ATL\_ENABLE\_PTM\_WARNING](../Topic/_ATL_ENABLE_PTM_WARNING.md)|定义此宏为了使用C\+\+满足条件的语法，生成C4867编译器错误，则非标准语法用于初始化指向成员函数时。|  
|[\_ATL\_FREE\_THREADED](../Topic/_ATL_FREE_THREADED.md)|如果一个或多个对象所使用释放或非特定线程处理，请定义。|  
|[\_ATL\_MULTI\_THREADED](../Topic/_ATL_MULTI_THREADED.md)|指示项目的符号将标记为两者的对象，随机或非。  应使用宏 [\_ATL\_FREE\_THREADED](../Topic/_ATL_FREE_THREADED.md)。|  
|[\_ATL\_NO\_AUTOMATIC\_NAMESPACE](../Topic/_ATL_NO_AUTOMATIC_NAMESPACE.md)|防止对命名空间的默认用作ATL的符号。|  
|[\_ATL\_NO\_COM\_SUPPORT](../Topic/_ATL_NO_COM_SUPPORT.md)|防止与COM的代码生成与您的项目的符号。|  
|[ATL\_NO\_VTABLE](../Topic/ATL_NO_VTABLE.md)|在选件类的构造函数和析构函数可防止vtable指针初始化的符号。|  
|[ATL\_NOINLINE](../Topic/ATL_NOINLINE.md)|指示一个函数的符号不应内联。|  
|[\_ATL\_SINGLE\_THREADED](../Topic/_ATL_SINGLE_THREADED.md)|所有条件，则您的对象使用单个线程模型，请定义。|  
  
## 请参阅  
 [Macros](../../atl/reference/atl-macros.md)