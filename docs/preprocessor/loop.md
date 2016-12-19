---
title: "循环 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "loop_CPP"
  - "vc-pragma.loop"
dev_langs: 
  - "C++"
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 循环
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制自动并行化如何考虑循环代码和\/或从自动向量化进行的考虑中排除循环。  
  
## 语法  
  
```  
  
#pragma loop( hint_parallel(n) )  
```  
  
```  
  
#pragma loop( no_vector )  
```  
  
```  
  
#pragma loop( ivdep )  
```  
  
#### 参数  
 `hint_parallel(` `n` `)`  
 对编译器应跨 `n` 个线程并行化此循环的提示（其中 `n` 为正整数文本或零）。  如果 `n` 为零，则在运行时使用最大数量的线程。  这是对编译器的提示而不是命令，并且并不保证会并行化循环。  如果循环具有数据依赖项或结构问题，例如，循环存储到在循环体外使用的标量，则将不会并行化循环。  
  
 除非指定了 [\/Qpar](../build/reference/qpar-auto-parallelizer.md) 编译器开关，否则编译器将忽略此选项。  
  
 `no_vector`  
 默认情况下，自动向量化处于启用状态，并且将尝试向量化其计算为从中受益的所有循环。  请指定此杂注以对杂注后面的循环禁用自动向量化。  
  
 `ivdep`  
 对编译器忽略此循环的向量依赖项的提示。  请将其与 `hint_parallel` 结合使用。  
  
## 备注  
 若要使用 `loop` 杂注，请将其放在紧靠循环定义之前，而不是放在循环定义中。  杂注对它后面的循环的范围有效。  您可按任意顺序将多个杂注应用于一个循环，但必须在单独的杂注语句中声明每个杂注。  
  
## 请参阅  
 [自动并行化和自动矢量化](../parallel/auto-parallelization-and-auto-vectorization.md)   
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)