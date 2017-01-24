---
title: "_InterlockedExchangeAdd 内部函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedExchangeAdd64_nf"
  - "_InterlockedExchangeAdd64_rel"
  - "_InterlockedExchangeAdd16_rel"
  - "_InterlockedExchangeAdd_acq"
  - "_InterlockedExchangeAdd_nf"
  - "_InterlockedExchangeAdd_rel"
  - "_InterlockedExchangeAdd8_acq"
  - "_InterlockedExchangeAdd16_nf"
  - "_InterlockedExchangeAdd_acq_cpp"
  - "_InterlockedExchangeAdd64_acq_cpp"
  - "_InterlockedExchangeAdd16_acq"
  - "_InterlockedExchangeAdd_HLERelease"
  - "_InterlockedExchangeAdd64_cpp"
  - "_InterlockedExchangeAdd64_HLERelease"
  - "_InterlockedExchangeAdd64_acq"
  - "_InterlockedExchangeAdd8"
  - "_InterlockedExchangeAdd64"
  - "_InterlockedExchangeAdd8_nf"
  - "_InterlockedExchangeAdd16"
  - "_InterlockedExchangeAdd64_rel_cpp"
  - "_InterlockedExchangeAdd_cpp"
  - "_InterlockedExchangeAdd8_rel"
  - "_InterlockedExchangeAdd_HLEAcquire"
  - "_InterlockedExchangeAdd64_HLEAcquire"
  - "_InterlockedExchangeAdd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedExchangeAdd 内部函数"
  - "_InterlockedExchangeAdd_acq 内部函数"
  - "_InterlockedExchangeAdd_HLEAcquire 内部函数"
  - "_InterlockedExchangeAdd_HLERelease 内部函数"
  - "_InterlockedExchangeAdd_nf 内部函数"
  - "_InterlockedExchangeAdd_rel 内部函数"
  - "_InterlockedExchangeAdd16 内部函数"
  - "_InterlockedExchangeAdd16_acq 内部函数"
  - "_InterlockedExchangeAdd16_nf 内部函数"
  - "_InterlockedExchangeAdd16_rel 内部函数"
  - "_InterlockedExchangeAdd64 内部函数"
  - "_InterlockedExchangeAdd64_acq 内部函数"
  - "_InterlockedExchangeAdd64_HLEAcquire 内部函数"
  - "_InterlockedExchangeAdd64_HLERelease 内部函数"
  - "_InterlockedExchangeAdd64_nf 内部函数"
  - "_InterlockedExchangeAdd64_rel 内部函数"
  - "_InterlockedExchangeAdd8 内部函数"
  - "_InterlockedExchangeAdd8_acq 内部函数"
  - "_InterlockedExchangeAdd8_nf 内部函数"
  - "_InterlockedExchangeAdd8_rel 内部函数"
  - "InterlockedExchangeAdd 内部函数"
  - "InterlockedExchangeAdd_acq 内部函数"
  - "InterlockedExchangeAdd_rel 内部函数"
  - "InterlockedExchangeAdd64 内部函数"
  - "InterlockedExchangeAdd64_acq 内部函数"
  - "InterlockedExchangeAdd64_rel 内部函数"
ms.assetid: 25809e1f-9c60-4492-9f7c-0fb59c8d13d2
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedExchangeAdd 内部函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 对 Win32 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [\_InterlockedExchangeAdd Intrinsic Functions](../intrinsics/interlockedexchangeadd-intrinsic-functions.md) 函数提供编译器内部函数支持。  
  
## 语法  
  
```  
long _InterlockedExchangeAdd(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_acq(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_rel(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_nf(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_HLEAcquire(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_HLERelease(    long volatile * Addend,    long Value ); char _InterlockedExchangeAdd8(    char volatile * Addend,    char Value ); char _InterlockedExchangeAdd8_acq(    char volatile * Addend,    char Value ); char _InterlockedExchangeAdd8_rel(    char volatile * Addend,    char Value ); char _InterlockedExchangeAdd8_nf(    char volatile * Addend,    char Value ); short _InterlockedExchangeAdd16(    short volatile * Addend,    short Value ); short _InterlockedExchangeAdd16_acq(    short volatile * Addend,    short Value ); short _InterlockedExchangeAdd16_rel(    short volatile * Addend,    short Value ); short _InterlockedExchangeAdd16_nf(    short volatile * Addend,    short Value ); __int64 _InterlockedExchangeAdd64(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_acq(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_rel(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_nf(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_HLEAcquire(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_HLERelease(    __int64 volatile * Addend,    __int64 Value );   
```  
  
#### 参数  
 \[in, out\] `Addend`  
 要相加的值；由加法得出的结果代替。  
  
 \[in\] `Value`  
 要相加的值。  
  
## 返回值  
 返回值是由 `Addend` 参数指向的变量的初始值。  
  
## 要求  
  
|内部函数|体系结构|Header|  
|----------|----------|------------|  
|`_InterlockedExchangeAdd`, `_InterlockedExchangeAdd8`, `_InterlockedExchangeAdd16`, `_InterlockedExchangeAdd64`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedExchangeAdd_acq`, `_InterlockedExchangeAdd_rel`, `_InterlockedExchangeAdd_nf`, `_InterlockedExchangeAdd8_acq`, `_InterlockedExchangeAdd8_rel`, `_InterlockedExchangeAdd8_nf`,`_InterlockedExchangeAdd16_acq`, `_InterlockedExchangeAdd16_rel`, `_InterlockedExchangeAdd16_nf`, `_InterlockedExchangeAdd64_acq`, `_InterlockedExchangeAdd64_rel`, `_InterlockedExchangeAdd64_nf`|ARM|\<intrin.h\>|  
|`_InterlockedExchangeAdd_HLEAcquire`, `_InterlockedExchangeAdd_HLERelease`, `_InterlockedExchangeAdd64_HLEAcquire`, `_InterlockedExchangeAdd64_HLErelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 备注  
 `_InterlockedExchangeAdd` 存在几种变体，这些变体根据其涉及的数据类型和是否使用特定于处理器获取或发布语义而有所不同。  
  
 当 `_InterlockedExchangeAdd` 函数对 32 位整数值操作时，`_InterlockedExchangeAdd8` 对 8 位整数值操作，`_InterlockedExchangeAdd16` 对 16 位整数值操作且 `_InterlockedExchangeAdd64` 对 64 位整数值操作。  
  
 ARM 平台上，如果需要（例如在临界区的起点和终点）获取和发布语义，可以使用带 `_acq` 和 `_rel` 后缀的函数。  带 `_nf`（“无围墙”）后缀的内部函数不能充当内存屏障。  
  
 在支持硬件锁省略 \(HLE\) 指令的 Intel 平台，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一个发送到处理器的提示，可以通过消除硬件中的锁写步骤来提升速度。  如果在不支持 HLE 的平台上调用这些函数，则忽略此提示。  
  
 这些例程只能用作内部函数。  因此，无论使用的是 [\/Oi](../build/reference/oi-generate-intrinsic-functions.md) 还是 [\#pragma intrinsic](../preprocessor/intrinsic.md)，它们都是内部函数。  对于这些内部函数，不能使用 [\#pragma function](../preprocessor/function-c-cpp.md)。  
  
## 示例  
 有关如何使用 `_InterlockedExchangeAdd` 的示例，请参阅 [\_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)