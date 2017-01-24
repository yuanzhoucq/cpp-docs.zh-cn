---
title: "2.7.2.2 firstprivate | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.2 firstprivate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**firstprivate** 子句提供 **专用** 子句提供的功能的扩展。  **firstprivate** 子句的语法如下所示:  
  
```  
firstprivate(variable-list)  
```  
  
 指定的变量 *变量列表* 包含 **专用** 子句语义，如第 25 页的 [第2.7.2.1部分](../../parallel/openmp/2-7-2-1-private.md) 所述。  该初始化或构造。构造上面的线程的执行发生，就象它已完成一次线程，。  对于并行构造 **firstprivate** 子句，新私有对象的初始值为立即在线程的并行构造之前存在到达其原始对象的值。  对于的工作划分结构化 **firstprivate** 子句，新私有对象中的原始值执行的每个线程执行的工作划分构造是在某个时间点之前存在原始对象的值相同线程遇到的工作划分构造。  此外，对于 C\+\+ 对象，每个线程的新私有对象是原始对象构造的副本。  
  
 为 **firstprivate** 子句的限制如下所示:  
  
-   在 **firstprivate** 子句中指定的变量不能包含不完整类型或引用类型。  
  
-   使用指定的类类型的变量，当 **firstprivate** 必须有一个可访问，明确的复制构造函数。  
  
-   在并行区域内是专用或显示 **并行** 指令的 **减少** 子句的变量。 **firstprivate** 子句不能指定在绑定到并行构造的工作划分指令。