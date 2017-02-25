---
title: "_InterlockedExchangePointer 内部函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedExchangePointer_cpp"
  - "_InterlockedExchangePointer_rel"
  - "_InterlockedExchangePointer_nf"
  - "_InterlockedExchangePointer_HLERelease"
  - "_InterlockedExchangePointer_acq"
  - "_InterlockedExchangePointer"
  - "_InterlockedExchangePointer_acq_cpp"
  - "_InterlockedExchangePointer_HLEAcquire"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedExchangePointer 内部函数"
  - "_InterlockedExchangePointer_acq 内部函数"
  - "_InterlockedExchangePointer_HLEAcquire 内部函数"
  - "_InterlockedExchangePointer_HLERelease 内部函数"
  - "_InterlockedExchangePointer_nf 内部函数"
  - "_InterlockedExchangePointer_rel 内部函数"
  - "InterlockedExchangePointer 内部函数"
  - "InterlockedExchangePointer_acq 内部函数"
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _InterlockedExchangePointer 内部函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 执行原子交换操作，将作为第二个参数传入的地址复制到第一个参数并返回第一个参数的原始地址。  
  
## 语法  
  
```  
void * _InterlockedExchangePointer(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_acq(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_rel(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_nf(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_HLEAcquire(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_HLERelease(    void * volatile * Target,    void * Value );  
```  
  
#### 参数  
 \[in, out\] `Target`  
 指向要交换值的指针的指针。  函数将值设置为 `Value` 并返回之前的值。  
  
 \[in\] `Value`  
 要与由 `Target` 指向的值交换的值。  
  
## 返回值  
 函数返回由 `Target` 指向的初始值。  
  
## 要求  
  
|内部函数|体系结构|Header|  
|----------|----------|------------|  
|`_InterlockedExchangePointer`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM|\<intrin.h\>|  
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]，带 HLE 支持|\<immintrin.h\>|  
  
 在 x86 体系结构上，`_InterlockedExchangePointer` 是调用 `_InterlockedExchange` 的宏。  
  
## 备注  
 在 64 位系统上，这些参数都是 64 位并且必须在 64 位边界上对齐；否则，函数失效。  在 32 位系统上，这些参数都是 32 位并且必须在 32 位边界上对齐。  有关更多信息，请参阅[对齐](../cpp/align-cpp.md)。  
  
 ARM 平台上，如果需要（例如在临界区的起点和终点）获取和发布语义，可以使用带 `_acq` 和 `_rel` 后缀的函数。  带 `_nf`（“无围墙”）后缀的内部函数不能充当内存屏障。  
  
 在支持硬件锁省略 \(HLE\) 指令的 Intel 平台，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一个发送到处理器的提示，可以通过消除硬件中的锁写步骤来提升速度。  如果在不支持 HLE 的平台上调用这些函数，则忽略此提示。  
  
 这些例程只能用作内部函数。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)