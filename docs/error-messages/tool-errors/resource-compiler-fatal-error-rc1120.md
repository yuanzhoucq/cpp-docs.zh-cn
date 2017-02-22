---
title: "资源编译器错误 RC1120 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC1120"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1120"
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 资源编译器错误 RC1120
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

内存不足，需要 number 字节  
  
 资源编译器没有足够的存储空间在其堆中存储项。  这通常是由太多符号引起的。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  增大 Windows 交换文件空间。  有关增大交换文件空间的更多信息，请参见 Windows 帮助中的虚拟内存。  
  
2.  消除不必要的包含文件，尤其是不需要的 `#define`s 和函数原型。  
  
3.  将当前文件拆分为几个较小的文件然后分别编译。  
  
4.  移除系统中正在运行的其他程序或驱动程序，这些程序可能正在消耗大量内存。