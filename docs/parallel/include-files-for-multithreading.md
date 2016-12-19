---
title: "多线程编程的包含文件 | Microsoft Docs"
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
helpviewer_keywords: 
  - "包含文件, 多线程处理"
  - "多线程处理 [C++], 包含文件"
  - "线程处理 [C++], 包含文件"
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多线程编程的包含文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在库中实现 C 运行库函数时，标准包含文件声明它们。  如果使用[完全优化](../build/reference/ox-full-optimization.md) \(\/Ox\) 或 [fastcall 调用约定](../build/reference/gd-gr-gv-gz-calling-convention.md) \(\/Gr\) 选项，编译器假设应使用寄存器调用约定调用所有函数。  运行库函数是使用 C 调用约定编译的，标准包含文件中的声明通知编译器生成对这些函数的正确外部引用。  
  
## 请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)