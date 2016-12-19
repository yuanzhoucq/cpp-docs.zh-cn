---
title: "生成文件预处理中的表达式 | Microsoft Docs"
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
  - "表达式 [C++], 生成文件预处理"
  - "生成文件, 预处理"
  - "预处理生成文件"
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成文件预处理中的表达式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\!IF** 或 **\!ELSE IF** `constantexpression` 由整型常数（使用十进制或 C 语言表示法）、字符串常数或命令组成。  使用括号将表达式分组。  表达式使用 C 样式的有符号长整型算法；数字为 32 位 2 的补数形式，范围在 \- 2147483648 到 2147483647 之间。  
  
 表达式可以使用在常数值、命令的退出代码、字符串、宏和文件系统路径上使用的运算符。  
  
## 您想进一步了解什么？  
 [生成文件预处理运算符](../build/makefile-preprocessing-operators.md)  
  
 [在预处理中执行程序](../build/executing-a-program-in-preprocessing.md)  
  
## 请参阅  
 [生成文件预处理](../build/makefile-preprocessing.md)