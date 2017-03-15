---
title: "2.6.3 barrier Directive | Microsoft Docs"
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
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.3 barrier Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**障碍** 指令同步团队的所有线程。  当遇到，在团队的每个线程等待，直到所有其他到达了这一点。  **障碍** 指令的语法如下所示:  
  
```  
#pragma omp barrier new-line  
```  
  
 在团队的所有线程都遇到关卡之后，在团队的每个线程开始并行执行语句在障碍指令之后。  请注意，由于作为其语法的一部分， **障碍** 指令没有 c. 语言语句，对其位置的一些限制在程序中。  为正式语法参见 [附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) 。  下面的示例阐释了这些限制。  
  
```  
/* ERROR - The barrier directive cannot be the immediate  
*          substatement of an if statement  
*/  
if (x!=0)  
   #pragma omp barrier  
...  
  
/* OK - The barrier directive is enclosed in a  
*      compound statement.  
*/  
if (x!=0) {  
   #pragma omp barrier  
}  
```