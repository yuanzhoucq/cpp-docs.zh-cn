---
title: "2.7.2.8 copyprivate | Microsoft Docs"
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
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.8 copyprivate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**copyprivate** 子句提供了一种机制使用私有变量广播从工作组中的成员的值与其他成员。  它可以替代使用共享变量的值的，同时允许这样的共享变量很难 \(例如，在需要不同的变量的递归在每个级别\)。  **copyprivate** 子句只能出现在 **单个** 指令。  
  
 **copyprivate** 子句的语法如下所示:  
  
```  
  
copyprivate(  
variable-list  
)  
  
```  
  
 **copyprivate** 子句的效果对其变量变量列表时，在构造的执行块与 **单个** 构造后，，因此，在任何一个团队的线程将障碍在构造结束时之前。  然后，在团队中的其他线程，每个的变量在 *变量列表*，变量成为定义 \(如同按指派\) 与相应的变量的值在执行结构化构造的线程的块。  
  
 为 **copyprivate** 子句的限制如下所示:  
  
-   在 **copyprivate** 子句中指定的变量不能出现在同一个 **单个** 指令的 **专用** 或 **firstprivate** 子句。  
  
-   如果使用 **copyprivate** 子句的一个 **单个** 指令在并行区域的动态区域遇到，在 **copyprivate** 子句中指定的所有变量必须是专用在封闭上下文。  
  
-   在 **copyprivate** 子句中指定的变量必须有一个可访问的明确的复制赋值运算符。