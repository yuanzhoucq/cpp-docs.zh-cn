---
title: "2.3 parallel Construct | Microsoft Docs"
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
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.3 parallel Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的指令定义并行区域，是程序的区域将由多个线程并行执行。  这是开始并行执行的基本构造。  
  
```  
#pragma omp parallel [clause[ [, ]clause] ...] new-line  
   structured-block  
```  
  
 *子句* 为下列之一:  
  
 **\(如果**标量*表达式***\)**  
  
 **\(专用** *变量列表* **\)**  
  
 **\(firstprivate** *变量列表* **\)**  
  
 **默认 \(共享&#124;任何内容\)**  
  
 **共享 \(** *变量列表* **\)**  
  
 **\(copyin** *变量列表* **\)**  
  
 **\(减少** *运算符* **:**  *变量列表* **\)**  
  
 **\(num\_threads**整数*表达式***\)**  
  
 当线程遇到并行构造时，线程团队创建，如果以下情况之一为真时:  
  
-   **如果** 子句不存在。  
  
-   **如果** 表达式计算为一个非零值。  
  
 此线程成为团队的主线程，与线程号的 0，并且，团队的所有线程，包括主线程，并行执行该区域。  如果 **如果** 表达式的值为零，序列化该区域。  
  
 若要确定请求的线程数，以下规则按顺序将考虑。  满足条件的第一个规则进行应用:  
  
1.  如果 **num\_threads** 子句存在，则整数表达式的值是请求的线程的数量。  
  
2.  如果 **omp\_set\_num\_threads** 库函数调用，则参数的值在最近执行的调用为请求线程的数量。  
  
3.  如果环境变量 **OMP\_NUM\_THREADS** 定义，则此环境变量的值是请求的线程的数量。  
  
4.  如果未使用上面的方法没有，则请求的线程的数目实现中定义。  
  
 如果 **num\_threads** 子句存在则取代 **omp\_set\_num\_threads** 库函数或它所应用的 **OMP\_NUM\_THREADS** 环境变量只需要的线程的数目并行区域。  后续并行区域不影响的受它。  
  
 还执行并行区域线程的数目由线程数动态调整是否启用。  如果动态调整处于禁用状态，则线程的请求数会执行并行区域。  动态调整则活动线程的请求数是可以执行并行区域线程的最大数目。  
  
 如果并行区域遇到，当线程数动态调整禁用了，并且，并行区域请求的线程的数目超过该数字为由运行时系统可以提供，程序的行为实现中定义。  实现可能，例如，中断程序的执行，也可以序列化并行区域。  
  
 **omp\_set\_dynamic** 库函数和 **OMP\_DYNAMIC** 环境变量可用于启用和禁用线程数动态调整。  
  
 实际承载线程的实际处理器数在任何给定时间实现中定义。  一旦创建，线程数。团队保持不变为该并行区域的持续时间。  它可以显式更改用户或自动则运行时系统从并行区域到另一个。  
  
 在并行区域的动态区域中包含的语句由每个线程执行，因此，每个线程可以执行与其他线程不同语句的路径。  在并行区域以外的词法区域遇到的指令引用孤立的指令。  
  
 具有一个暗含的关卡在并行区域末端。  团队只主线程继续执行在并行区域末端。  
  
 如果在执行并行区域的团队的线程遇到另一个并行构造，它创建新的团队，因此，它成为该新团队重要信息。  序列化默认情况下嵌套并行区域。  因此，在默认情况下，嵌套并行区域由团队执行中对一个线程。  使用 c 运行库函数 **omp\_set\_nested** 或环境变量 **OMP\_NESTED**，默认行为能更改。  但是，执行嵌套并行区域线程数。团队的实现中定义。  
  
 为 **并行** 指令的限制如下所示:  
  
-   最多一 **如果** 子句可以在指令。  
  
-   ，如果表达式或 **num\_threads** 表达式时，它是否未指定的中的任何副作用。  
  
-   **引发** 是在并行区域内必须导致执行在还原结构化同一个中的动态区域阻止，因此，必须引发异常的同一线程将其捕获。  
  
-   唯一 **num\_threads** 子句可以在指令。  **num\_threads** 表达式在并行区域的上下文之外进行计算，然后必须计算为正整数值。  
  
-   **如果** 和 **num\_threads** 子句的计算顺序是未指定的。  
  
## 交叉引用:  
  
-   **专用**、 **firstprivate**、 **默认**、 **共享**、 **copyin**和 **减少** 子句，请参见中的第 25 页的 [第2.7.2部分](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 。  
  
-   **OMP\_NUM\_THREADS** 环境变量，在第 48 页的 [第4.2部分](../../parallel/openmp/4-2-omp-num-threads.md) 。  
  
-   **omp\_set\_dynamic** 库函数，请参见中的第 39 页的 [第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 。  
  
-   **OMP\_DYNAMIC** 环境变量，请参见中的第 49 页的 [第4.3部分](../../parallel/openmp/4-3-omp-dynamic.md) 。  
  
-   **omp\_set\_nested** 功能，请参见中的第 40 页的 [第3.1.9部分](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 。  
  
-   **OMP\_NESTED** 环境变量，请参见中的第 49 页的 [第4.4部分](../../parallel/openmp/4-4-omp-nested.md) 。  
  
-   **omp\_set\_num\_threads** 库函数，请参见中的第 36 页的 [第3.1.1部分](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 。