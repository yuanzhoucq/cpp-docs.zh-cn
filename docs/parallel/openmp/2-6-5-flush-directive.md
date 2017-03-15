---
title: "2.6.5 flush Directive | Microsoft Docs"
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
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.5 flush Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**刷新** 指令，显式或提示，指定是否 “帮助”序列点在哪些要求实现确保团队的所有线程具有某些对象的一个一致的视图 \(如指定\) 在内存中。  这意味着引用这些对象表达式以前的计算完成和后续计算尚未开始。  例如，编译器必须将对象的值从注册到内存，并且，硬件可能需要刷新写入缓冲区到内存和重新加载对象的值从内存中。  
  
 **刷新** 指令的语法如下所示:  
  
```  
#pragma omp flush [(variable-list)]  new-line  
```  
  
 如果需要同步的对象可完全由变量指定，则这些变量在选项卡中指定 *变量列表*。  如果指针位于 *变量列表*，不刷新，指针引用不的对象。  
  
 没有 *变量列表的* 一个 **刷新** 指令具有自动存储持续时间同步但不可访问对象的所有共享对象。  \(这与具有 *变量列表的***刷新** 可以具有更高的开销。\)没有 *变量列表的* 一个 **刷新** 指令为下面的指令提示:  
  
-   `barrier`  
  
-   在项以及从 **重要**退出  
  
-   在项以及从 `ordered`退出  
  
-   在项以及从 **并行**退出  
  
-   在从 **为**退出  
  
-   在从 **部分**退出  
  
-   在从 **单个**退出  
  
-   在项以及从 **并行。**退出  
  
-   在项以及从 **并行部分**退出  
  
 指令不提示 `nowait` 子句是否存在。  应当注意， **刷新** 指令没有为以下任一个提示:  
  
-   在对 **为**的项  
  
-   在进入到或从 **母版**退出  
  
-   在对 **部分**的项  
  
-   在对 **单个**的项  
  
 访问对象的值与 volatile 限定类型的行为的引用，就象指令的 **刷新** 指定在前面的对象序列点。  修改对象的值与 volatile 限定类型的引用的行为，就象指令的 **刷新** 指定该后续序列的对象点。  
  
 请注意，由于作为其语法的一部分， **刷新** 指令没有 c. 语言语句，对其位置的一些限制在程序中。  为正式语法参见 [附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) 。  下面的示例阐释了这些限制。  
  
```  
/* ERROR - The flush directive cannot be the immediate  
*          substatement of an if statement.  
*/  
if (x!=0)  
   #pragma omp flush (x)  
...  
  
/* OK - The flush directive is enclosed in a  
*      compound statement  
*/  
if (x!=0) {  
   #pragma omp flush (x)  
}  
```  
  
 为 **刷新** 指令的限制如下所示:  
  
-   在 **刷新** 指令指定的变量不能有引用类型。