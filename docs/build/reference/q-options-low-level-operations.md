---
title: "/Q 选项（低级别操作） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/q"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Q 编译器选项 [C++]"
  - "-Q 编译器选项 [C++]"
  - "/Q 编译器选项 [C++]"
ms.assetid: 9fa738b9-630a-4bde-bc87-bdfa30552be4
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# /Q 选项（低级别操作）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

你可以使用**\/Q** 编译器选项使您可以执行下列低级别编译器操作：  
  
-   [\/Qfast\_transcendentals（强制快速先验）](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)：生成快速先验。  
  
-   [\/QIfist（取消 \_ftol）](../../build/reference/qifist-suppress-ftol.md)：当需要从浮点类型转换为整型时取消 `_ftol`（仅限 x86）。  
  
-   [\/Qimprecise\_fwaits（移除 Try 块中的 fwaits）](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)：移除 `try` 块中的 `fwait` 命令。  
  
-   [\/Qpar（自动并行化程序）](../../build/reference/qpar-auto-parallelizer.md)：启用了标有循环的自动并行化[＃pragma循环（）](../../preprocessor/loop.md)指令。  
  
-   [\/Qpar\-report（自动并行化程序报告等级）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md):启用自动并行化的报告级别。  
  
-   [\/Qsafe\_fp\_loads](../../build/reference/qsafe-fp-loads.md)：禁止优化浮点寄存器加载和内存和MMX寄存器之间移动。  
  
-   [\/Qvec\-report（自动矢量化程序报告等级）](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md):启用自动矢量化的报告级别。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)