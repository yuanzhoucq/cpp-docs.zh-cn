---
title: "_InterlockedExchange 内部函数 | Microsoft Docs"
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
  - "_InterlockedExchange_rel"
  - "_InterlockedExchange8_nf"
  - "_InterlockedExchange_acq_cpp"
  - "_InterlockedExchange_nf"
  - "_InterlockedExchange64_nf"
  - "_InterlockedExchange_HLEAcquire"
  - "_InterlockedExchange_cpp"
  - "_InterlockedExchange64_acq_cpp"
  - "_InterlockedExchange64_acq"
  - "_InterlockedExchange64_HLERelease"
  - "_InterlockedExchange8_acq"
  - "_InterlockedExchange16_acq"
  - "_InterlockedExchange"
  - "_InterlockedExchange64_HLEAcquire"
  - "_InterlockedExchange8"
  - "_InterlockedExchange64_rel"
  - "_InterlockedExchange_acq"
  - "_InterlockedExchange16"
  - "_InterlockedExchange16_rel"
  - "_InterlockedExchange16_nf"
  - "_InterlockedExchange64"
  - "_InterlockedExchange_HLERelease"
  - "_InterlockedExchange64_cpp"
  - "_InterlockedExchange8_rel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedExchange 内部函数"
  - "_InterlockedExchange_acq 内部函数"
  - "_InterlockedExchange16"
  - "_InterlockedExchange16_acq"
  - "_InterlockedExchange16_nf"
  - "_InterlockedExchange16_rel"
  - "_InterlockedExchange64 内部函数"
  - "_InterlockedExchange64_acq 内部函数"
  - "_InterlockedExchange8"
  - "_InterlockedExchange8_acq"
  - "_InterlockedExchange8_nf"
  - "_InterlockedExchange8_rel"
  - "InterlockedExchange 内部函数"
  - "InterlockedExchange_acq 内部函数"
  - "InterlockedExchange64 内部函数"
  - "InterlockedExchange64_acq 内部函数"
ms.assetid: be2f232a-6301-462a-a92b-fcdeb8b0f209
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedExchange 内部函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成原子指令以设置指定的值。  
  
## 语法  
  
```  
long _InterlockedExchange(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_acq(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_HLEAcquire(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_HLERelease(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_nf(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_rel(  
   long volatile * Target,  
   long Value  
);  
char _InterlockedExchange8(  
   char volatile * Target,  
   char Value  
);  
char _InterlockedExchange8_acq(  
   char volatile * Target,  
   char Value  
);  
char _InterlockedExchange8_nf(  
   char volatile * Target,  
   char Value  
);  
char _InterlockedExchange8_rel(  
   char volatile * Target,  
   char Value  
);  
short _InterlockedExchange16(  
   short volatile * Target,  
   short Value  
);  
short _InterlockedExchange16_acq(  
   short volatile * Target,  
   short Value  
);  
short _InterlockedExchange16_nf(  
   short volatile * Target,  
   short Value  
);  
short _InterlockedExchange16_rel(  
   short volatile * Target,  
   short Value  
);  
__int64 _InterlockedExchange64(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_acq(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_HLEAcquire(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_HLERelease(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_nf(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_rel(  
   __int64 volatile * Target,  
   __int64 Value  
);  
```  
  
#### 参数  
 \[in, out\] `Target`  
 指向要交换的值。  此函数会将此变量设置为 `Value` 并返回其之前的值。  
  
 \[in\] `Value`  
 要与由 `Target` 指向的值交换的值。  
  
## 返回值  
 返回由 `Target` 指向的初始值。  
  
## 要求  
  
|内部函数|体系结构|标头|  
|----------|----------|--------|  
|`_InterlockedExchange`, `_InterlockedExchange8`, `_InterlockedExchange16`, `_InterlockedExchange64`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedExchange_acq`、`_InterlockedExchange_nf`、`_InterlockedExchange_rel`、`_InterlockedExchange8_acq`、`_InterlockedExchange8_nf`、`_InterlockedExchange8_rel`、`_InterlockedExchange16_acq`、`_InterlockedExchange16_nf`、`_InterlockedExchange16_rel`、`_InterlockedExchange64_acq`、`_InterlockedExchange64_nf`、`_InterlockedExchange64_rel`、|ARM|\<intrin.h\>|  
|`_InterlockedExchange_HLEAcquire`, `_InterlockedExchange_HLERelease`, `_InterlockedExchange64_HLEAcquire`, `_InterlockedExchange64_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 备注  
 `_InterlockedExchange` 为 Win32 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [InterlockedExchange](http://msdn.microsoft.com/library/ms683590.aspx) 函数提供编译器内部支持。  
  
 `_InterlockedExchange` 存在几种变体，这些变体根据其涉及的数据类型和是否使用特定于处理器获取或发布语义而有所不同。  
  
 当 `_InterlockedExchange` 函数对 32 位整数值操作时，`_InterlockedExchange8` 对 8 位整数值操作，`_InterlockedExchange16` 对 16 位整数值操作且 `_InterlockedExchange64` 对 64 位整数值操作。  
  
 在 ARM 平台上，可以使用带 `_acq` 和 `_rel` 后缀的内部函数获取和发布语义，例如在临界区的起始位置。  带 `_nf`（“无围墙”）后缀的内部函数不能充当内存屏障。  
  
 在支持硬件锁省略 \(HLE\) 指令的 Intel 平台，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一个发送到处理器的提示，可以通过消除硬件中的锁写步骤来提升速度。  如果在不支持 HLE 的平台上调用这些函数，则忽略此提示。  
  
 这些例程只能用作内部函数。  
  
## 示例  
 有关如何使用 `_InterlockedExchange` 的示例，请参阅 [\_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)