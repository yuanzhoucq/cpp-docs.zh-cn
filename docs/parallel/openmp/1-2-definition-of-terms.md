---
title: "1.2 Definition of Terms | Microsoft Docs"
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
ms.assetid: fcaa8eb8-bbbf-4a24-ad0e-e299c442db79
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1.2 Definition of Terms
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以下术语用于此文档:  
  
 障碍  
 必须由团队的所有线程到达的同步点。  每个线程等待，直到在团队中的所有线程此时到达。  具有的指令标识显式障碍和实现中创建的隐式障碍。  
  
 构造  
 构造是语句。  它包括指令，并构造的后续块。  请注意一些指令不是构造的一部分。  \(请参见 *openmp 指令* 在 [附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)\)。  
  
 Directive — 指令  
 对. 或 C\+\+ **\#pragma** 中 **omp** 标识符、其他文本和新行。  指令中指定程序的行为。  
  
 动态区域  
 在 *词法区域的*任何语句，以及在因为语句的执行对该用户在区域中，的执行的函数中的任何语句。  动态区域也称为 *区域*。  
  
 词法区域  
 在词法包含的语句 *构造块*。  
  
 主线程  
 创建一个团队的线程，当一个 *并行区域* 中输入。  
  
 并行区域  
 绑定到 OpenMP 并行构造，并且可以由多个线程执行语句。  
  
 private  
 私有变量名称设置进行引用的线程是唯一存储的块。  请注意可通过多种方法指定变量是私有的:在并行区域的定义、 **threadprivate** 指令、 **专用**、 **firstprivate**、 **lastprivate**或 **减少** 对变量的子句或使用中为一个 **为** 循环的一个 **为**循环控制变量用在 **为** 或 **并行。** 指令之后。  
  
 区域  
 动态区域。  
  
 序列化的区域  
 *主线程* 仅执行语句在任何 *并行区域之外的*动态区域。  
  
 序列化  
 希望使用包括该并行构造主线程\) 仅有一个线程 \(，与执行序列化的顺序语句中的构造块 \(顺序，就象块不是并行构造部分\) 和不会 **omp\_in\_parallel \(\)** 返回的值的影响的线程团队的并行构造 \(不包括任何嵌套并行构造时 \(clr\)\)。  
  
 共享  
 唯一块存储的共享变量名称。  所有在团队线程此变量访问此唯一将阻止存储的访问。  
  
 构造块  
 构造块是语句 \(个或多个\) 具有单个项和一个退出。  不是构造的语句块，如果存在跳转到或在该语句外部 \(可 **longjmp**\(3C\) 的包含调用或使用 **引发**，但是，对 **退出** 的调用\)。  ，如果其执行始终首先在打开的 **{** 并始终以结束 **}**，是构造的复合语句块。  表达式语句、 select 语句、迭代语句或 **尝试** 块是构造块，如果将获取相应的复合语句它在 **{** 和 **}**是构造的块。  跳转语句，标记语句或非结构化声明语句块。  
  
 团队  
 团队在构造执行的一个或多个线程。  
  
 线程  
 有权执行的实体一序列化的控制流，对共享变量中设置私有变量和。  
  
 variable  
 标识符，可选择限定的命名空间名称，命名对象。