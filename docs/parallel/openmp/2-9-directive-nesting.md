---
title: "2.9 Directive Nesting | Microsoft Docs"
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
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.9 Directive Nesting
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

动态嵌套指令必须遵循下列规则:  
  
-   **并行** 指令在另一 **并行** 内部逻辑上动态建立一个新的团队，只能由当前线程组成，因此，除非嵌套并行启用。  
  
-   **为**、 **部分**和绑定到同一 **并行** 的 **单个** 指令不允许互相嵌套。  
  
-   同名的**重要** 指令不允许互相嵌套。  请注意此限制不满足避免死锁。  
  
-   ，如果指令绑定到 **并行** 和区域相同，**为**、 **部分**和 **单个** 指令在 **重要**、 **排序**和 **母版** 区域的动态区域是不允许的。  
  
-   ，如果指令绑定到 **并行** 和区域相同，**障碍** 指令在 **为**、 **排序**、 **部分**、 **单个**、 **母版**和 **重要** 区域的动态区域是不允许的。  
  
-   ，如果 **母版** 指令绑定到 **并行** 和的工作划分指令相同，**母版** 指令在 **为**、 **部分**和 **单个** 指令的动态区域是不允许的。  
  
-   ，如果指令绑定到 **并行** 和区域相同，**排序** 指令在 **重要** 区域的动态区域不允许的。  
  
-   任何允许，则动态执行在并行区域中的指令还允许，在执行在并行区域之外。  在动态执行在用户指定的并行区域之外，指令由团队执行组成只能由主线程。