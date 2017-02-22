---
title: "错误 C1002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1002"
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 错误 C1002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在第 2 遍中编译器的堆空间不足  
  
 编译器在它的第二遍扫描中用完了动态内存空间，可能是由于某个程序有太多的符号或复杂的表达式。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  将源文件分为几个更小的文件。  
  
2.  将表达式分为更小的子表达式。  
  
3.  移除消耗内存的其他程序或驱动程序。