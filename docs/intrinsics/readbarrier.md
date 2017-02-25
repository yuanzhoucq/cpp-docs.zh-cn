---
title: "_ReadBarrier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ReadBarrier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ReadBarrier 内部"
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _ReadBarrier
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 限制可重新排列调用点上的内存访问操作的编译器优化。  
  
> [!CAUTION]
>  已全部弃用且不应使用 `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 编译器内部函数和 `MemoryBarrier` 宏。  对于线程间的通信，请使用在 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)中定义的机制，例如 [atomic\_thread\_fence](../Topic/atomic_thread_fence%20Function.md) 和 [std::atomic\<T\>](../standard-library/atomic.md)。  对于硬件访问，请结合使用 [\/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) 编译器选项以及 [volatile](../cpp/volatile-cpp.md) 关键字。  
  
## 语法  
  
```  
void _ReadBarrier(void);  
```  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`_ReadBarrier`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `_ReadBarrier` 内部函数将限制可删除或重新排列调用点上的内存访问操作的编译器优化。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)