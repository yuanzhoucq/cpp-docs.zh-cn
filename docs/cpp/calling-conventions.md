---
title: "调用约定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调用约定"
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 调用约定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\/C\+\+ 编译器提供了用于调用内部函数和外部函数的几个不同的约定。  了解这些不同的方法有助于调试程序以及将您的代码与汇编语言例程链接。  
  
 本主题中的各个主题说明了调用约定之间的差异、如何传递参数以及函数如何返回值。  它们也讨论了裸函数调用以及使您能够写入自己的 prolog 和 epilog 代码的高级功能。  
  
 有关调用 x64 处理器的约定的信息，请参阅[调用约定](../build/calling-convention.md)。  
  
## 本节中的主题  
  
-   [参数传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)（\_\_`cdecl`、\_\_**stdcall**、\_\_**fastcall** 及其他）  
  
-   [调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)  
  
-   [使用裸函数调用编写自定义 prolog\/epilog 代码](../cpp/naked-function-calls.md)  
  
-   [浮点协处理器和调用约定](../cpp/floating-point-coprocessor-and-calling-conventions.md)  
  
-   [已过时调用约定](../cpp/obsolete-calling-conventions.md)  
  
## 请参阅  
 [Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)