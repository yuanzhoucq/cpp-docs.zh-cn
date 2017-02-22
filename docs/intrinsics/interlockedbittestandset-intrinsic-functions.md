---
title: "_interlockedbittestandset 内部函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_interlockedbittestandset_cpp"
  - "_interlockedbittestandset_HLEAcquire"
  - "_interlockedbittestandset64"
  - "_interlockedbittestandset"
  - "_interlockedbittestandset_rel"
  - "_interlockedbittestandset64_HLEAcquire"
  - "_interlockedbittestandset_HLERelease"
  - "_interlockedbittestandset_acq"
  - "_interlockedbittestandset_nf"
  - "_interlockedbittestandset64_cpp"
  - "_interlockedbittestandset64_HLERelease"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_interlockedbittestandset 内部函数"
  - "_interlockedbittestandset64 内部函数"
  - "lock_bts 指令"
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _interlockedbittestandset 内部函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成可以检查地址 `a` 的位 `b` 的指令，返回其当前值，然后将位设置为 1。  
  
## 语法  
  
```  
unsigned char _interlockedbittestandset(    long *a,    long b ); unsigned char _interlockedbittestandset_acq(    long *a,    long b ); unsigned char _interlockedbittestandset_HLEAcquire(    long *a,    long b ); unsigned char _interlockedbittestandset_HLERelease(    long *a,    long b ); unsigned char _interlockedbittestandset_nf(    long *a,    long b ); unsigned char _interlockedbittestandset_rel(    long *a,    long b ); unsigned char _interlockedbittestandset64(    __int64 *a,    __int64 b ); unsigned char _interlockedbittestandset64_HLEAcquire(    __int64 *a,    __int64 b ); unsigned char _interlockedbittestandset64_HLERelease(    __int64 *a,    __int64 b );  
```  
  
#### 参数  
 \[in\] `a`  
 指向要检查的内存的指针。  
  
 \[in\] `b`  
 要测试的位位置。  
  
## 返回值  
 在位置 `b` 上的位在其设置前的值。  
  
## 要求  
  
|内部函数|体系结构|Header|  
|----------|----------|------------|  
|`_interlockedbittestandset`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM|\<intrin.h\>|  
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
|`_interlockedbittestandset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 备注  
 在 x86 和 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 处理器上，这些内部函数使用 `lock bts` 指令读取并将指定的值设置为 1。  此操作为原子性操作。  
  
 在 ARM 处理器上，使用带 `_acq` 和 `_rel` 后缀的内部函数（例如在临界区的起点和结尾处）获取和发布语义。  带 `_nf`（“无围墙”）后缀的 ARM 内部函数不能充当内存屏障。  
  
 在支持硬件锁省略 \(HLE\) 指令的 Intel 处理器上，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一条发送到处理器的提示，可通过消除硬件中的锁写步骤加快速度。  如果在不支持 HLE 的处理器上调用这些函数，则忽略此提示。  
  
 这些例程只能用作内部函数。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)