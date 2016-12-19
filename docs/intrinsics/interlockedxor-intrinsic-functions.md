---
title: "_InterlockedXor 内部函数 | Microsoft Docs"
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
  - "_InterlockedXor_nf"
  - "_InterlockedXor_np"
  - "_InterlockedXor64_HLERelease"
  - "_InterlockedXor8_acq"
  - "_InterlockedXor64_acq"
  - "_InterlockedXor64_rel"
  - "_InterlockedXor64_nf"
  - "_InterlockedXor_acq"
  - "_InterlockedXor16"
  - "_InterlockedXor64_np"
  - "_InterlockedXor64"
  - "_InterlockedXor_HLEAcquire"
  - "_InterlockedXor_HLERelease"
  - "_InterlockedXor_cpp"
  - "_InterlockedXor16_rel"
  - "_InterlockedXor8_rel"
  - "_InterlockedXor8"
  - "_InterlockedXor64_HLEAcquire"
  - "_InterlockedXor16_nf"
  - "_InterlockedXor16_acq"
  - "_InterlockedXor16_np"
  - "_InterlockedXor8_fn"
  - "_InterlockedXor8_np"
  - "_InterlockedXor64_cpp"
  - "_InterlockedXor_rel"
  - "_InterlockedXor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedXor 内部函数"
  - "_InterlockedXor64 内部函数"
  - "InterlockedXor 内部函数"
  - "InterlockedXor64 内部函数"
ms.assetid: faef1796-cb5a-4430-b1e2-9d5eaf9b4a91
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedXor 内部函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 在由多线程共享的变量上执行原子按位异或 \(XOR\) 操作。  
  
## 语法  
  
```  
long _InterlockedXor(    long volatile * Value,    long Mask ); long _InterlockedXor_acq(    long volatile * Value,    long Mask ); long _InterlockedXor_HLEAcquire(    long volatile * Value,    long Mask ); long _InterlockedXor_HLERelease(    long volatile * Value,    long Mask ); long _InterlockedXor_nf(    long volatile * Value,    long Mask ); long _InterlockedXor_np(    long volatile * Value,    long Mask ); long _InterlockedXor_rel(    long volatile * Value,    long Mask ); char _InterlockedXor8(    char volatile * Value,    char Mask ); char _InterlockedXor8_acq(    char volatile * Value,    char Mask ); char _InterlockedXor8_nf(    char volatile * Value,    char Mask ); char _InterlockedXor8_np(    char volatile * Value,    char Mask ); char _InterlockedXor8_rel(    char volatile * Value,    char Mask ); short _InterlockedXor16(    short volatile * Value,    short Mask ); short _InterlockedXor16_acq(    short volatile * Value,    short Mask ); short _InterlockedXor16_nf (    short volatile * Value,    short Mask ); short _InterlockedXor16_np (    short volatile * Value,    short Mask ); short _InterlockedXor16_rel(    short volatile * Value,    short Mask ); __int64 _InterlockedXor64(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedXor64_acq(    __int64 volatile * Value,    __int64 Mask );  __int64 _InterlockedXor64_HLEAcquire(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedXor64_HLERelease(    __int64 volatile * Value,    __int64 Mask );  __int64 _InterlockedXor64_nf(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedXor64_np(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedXor64_rel(    __int64 volatile * Value,    __int64 Mask );  
```  
  
#### 参数  
 \[in, out\] `Value`  
 指向第一个操作数的指针，将由结果替换。  
  
 \[in\] `Mask`  
 第二个操作数。  
  
## 返回值  
 第一个操作数的原始值。  
  
## 要求  
  
|内部函数|体系结构|Header|  
|----------|----------|------------|  
|`_InterlockedXor`, `_InterlockedXor8`, `_InterlockedXor16`, `_InterlockedXor64`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedXor_acq`, `_InterlockedXor_nf`, `_InterlockedXor_rel`, `_InterlockedXor8_acq`, `_InterlockedXor8_nf`, `_InterlockedXor8_rel`, `_InterlockedXor16_acq`, `_InterlockedXor16_nf`, `_InterlockedXor16_rel`, `_InterlockedXor64_acq`, `_InterlockedXor64_nf`, `_InterlockedXor64_rel`,|ARM|\<intrin.h\>|  
|`_InterlockedXor_np`, `_InterlockedXor8_np`, `_InterlockedXor16_np`, `_InterlockedXor64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedXor_HLEAcquire`, `_InterlockedXor_HLERelease`, `_InterlockedXor64_HLEAcquire`, `_InterlockedXor64_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 备注  
 每个函数名称中的数字指定了参数的位大小。  
  
 ARM 平台上，如果需要（例如在临界区的起点和终点）获取和发布语义，可以使用带 `_acq` 和 `_rel` 后缀的函数。  带 `_nf`（“无围墙”）后缀的 ARM 内部函数不能充当内存屏障。  
  
 带 `_np`（“无预取”）后缀的函数可以阻止编译器插入可能的预取操作。  
  
 在支持硬件锁省略 \(HLE\) 指令的 Intel 平台，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一个发送到处理器的提示，可以通过消除硬件中的锁写步骤来提升速度。  如果在不支持 HLE 的平台上调用这些函数，则忽略此提示。  
  
## 示例  
  
```  
// _InterLockedXor.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedXor)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FFFF00;  
        long retval;  
        retval = _InterlockedXor(&data1, data2);  
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);   
}  
```  
  
  **0xffff0000 0xffff00 0xff00ff00**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)