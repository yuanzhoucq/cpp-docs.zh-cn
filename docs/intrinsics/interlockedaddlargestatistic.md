---
title: "_InterlockedAddLargeStatistic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedAddLargeStatistic"
  - "_InterlockedAddLargeStatistic_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedAddLargeStatistic 内部函数"
  - "InterlockedAddLargeStatistic 内部函数"
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _InterlockedAddLargeStatistic
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 执行第一个操作数是为 64 位值的互锁的添加。  
  
## 语法  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### 参数  
 \[in, out\] `Addend`  
 对于第一个操作数的指向添加操作。  该值指向添加的结果替换。  
  
 \[in\] `Value`  
 第二个操作数对象;将的值赋给第一个操作数。  
  
## 返回值  
 第二个操作数对象的值。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_InterlockedAddLargeStatistic`|x86|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 ，因为它实现为两个不同锁定的命令，此内部不是原子的。  在另一个线程上发生此内部的执行过程中读取的基本 64 位可能导致读取的不一致的值。  
  
 此功能的行为就如同读\/写障碍。  有关更多信息，请参见 [\_ReadWriteBarrier](../intrinsics/readwritebarrier.md)。  
  
## 关闭 Microsoft 特定  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)