---
title: "F. New Features and Clarifications in Version 2.0 | Microsoft Docs"
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
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# F. New Features and Clarifications in Version 2.0
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此附录摘要进行的关键更改 OpenMP C\/C\+\+ 规范在移动的与版本 1.0 到 2.0 版。  以下各项是新功能添加到规范:  
  
-   用 OpenMP 指令 \(在第 7 页\) 的[第2.1部分](../../parallel/openmp/2-1-directive-format.md) 允许的。  
  
-   `num_threads` 子句中添加。  此子句允许用户请求线程的特定数字并行构造 \(在第 8 页\) 的[第2.3部分](../../parallel/openmp/2-3-parallel-construct.md) 。  
  
-   `threadprivate` 指令扩展接受静态块范围变量 \(在第 23 页\) 的[第2.7.1部分](../../parallel/openmp/2-7-1-threadprivate-directive.md) 。  
  
-   C99 变长数组是完整类型和因此可以是任意位置指定的完整类型允许，例如在列表中 `private`、 `firstprivate`和 `lastprivate` 子句 \(在第 25 页\) 的[第2.7.2部分](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 。  
  
-   私有变量在并行区域可以再次被标记的专用在嵌套的指令 \(在第 25 页\) 的[第2.7.2.1部分](../../parallel/openmp/2-7-2-1-private.md) 。  
  
-   `copyprivate` 子句添加了。  它提供了一种机制使用私有变量广播从工作组中的成员的值与其他成员。  它可以替代使用共享变量的值的，同时允许这样的共享变量很难 \(例如，在需要不同的变量的递归在每个级别\)。  `copyprivate` 子句只能出现在 **single** 指令 \(在第 32 页\) 的[第2.7.2.8部分](../../parallel/openmp/2-7-2-8-copyprivate.md) 。  
  
-   计时实例 `omp_get_wtick` 和 `omp_get_wtime` 的添加类似于 MPI 实例。  这些功能用于执行壁钟计时 \(在第 44 页中的第 45 页\) 的[第3.3.1部分](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) 和 [第3.3.2部分](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) 是必需的。  
  
-   与实现中定义的行为列表中的附录在 OpenMP C\/C\+\+ 添加了。  实现在这些情况下定义和文档其行为 \(在第 97 页\) 的[附录 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) 。  
  
-   以下更改服务阐明或更正在前面的 OpenMP API 规范的功能 C\/C\+\+ 的:  
  
    -   阐明 `omp_set_nested` 和 `omp_set_dynamic` 行为，当 `omp_in_parallel` 返回非零未定义 \(在第 39 页中的第 40 页\) 的[第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 和 [第3.1.9部分](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 。  
  
    -   嵌套阐明了指令，在使用嵌套并行 \(在第 33 页\) 的[第2.9部分](../../parallel/openmp/2-9-directive-nesting.md) 。  
  
    -   锁初始化和锁定析构函数在并行在第 42 页\) 的区域 \(在第 42 页的[第3.2.1部分](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) 和 [第3.2.2部分](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) 可以调用。  
  
    -   新示例中添加了 \(在第 51 页\) 的[附录 A](../../parallel/openmp/a-examples.md) 。