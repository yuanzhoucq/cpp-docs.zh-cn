---
title: _InterlockedAnd 内部函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedAnd_rel
- _InterlockedAnd_cpp
- _InterlockedAnd8_nf
- _InterlockedAnd
- _InterlockedAnd_HLERelease
- _InterlockedAnd8_np
- _InterlockedAnd16_rel
- _InterlockedAnd64_np
- _InterlockedAnd_np
- _InterlockedAnd64_HLERelease
- _InterlockedAnd64
- _InterlockedAnd64_nf
- _InterlockedAnd64_HLEAcquire
- _InterlockedAnd16
- _InterlockedAnd16_nf
- _InterlockedAnd8
- _InterlockedAnd_HLEAcquire
- _InterlockedAnd_acq
- _InterlockedAnd16_np
- _InterlockedAnd64_cpp
- _InterlockedAnd64_acq
- _InterlockedAnd16_acq
- _InterlockedAnd8_acq
- _InterlockedAnd64_rel
- _InterlockedAnd_nf
- _InterlockedAnd8_rel
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedAnd64_np intrinsic
- _InterlockedAnd intrinsic
- _InterlockedAnd64 intrinsic
- _InterlockedAnd8_rel intrinsic
- InterlockedAnd64 intrinsic
- _InterlockedAnd16_np intrinsic
- _InterlockedAnd64_nf intrinsic
- _InterlockedAnd_nf intrinsic
- _InterlockedAnd_np intrinsic
- _InterlockedAnd64_HLERelease intrinsic
- _InterlockedAnd16_rel intrinsic
- _InterlockedAnd_HLERelease intrinsic
- _InterlockedAnd64_acq intrinsic
- _InterlockedAnd16 intrinsic
- _InterlockedAnd8_nf intrinsic
- _InterlockedAnd64_rel intrinsic
- _InterlockedAnd8_np intrinsic
- _InterlockedAnd_rel intrinsic
- InterlockedAnd intrinsic
- _InterlockedAnd8_acq intrinsic
- _InterlockedAnd_acq intrinsic
- _InterlockedAnd64_HLEAcquire intrinsic
- _InterlockedAnd16_acq intrinsic
- _InterlockedAnd16_nf intrinsic
- _InterlockedAnd8 intrinsic
- _InterlockedAnd_HLEAcquire intrinsic
ms.assetid: ad271dc3-42cd-47d0-9f65-30d5cfeb66fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b991d4d0546ea20e26f2896bc78032e2fb1c6136
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540989"
---
# <a name="interlockedand-intrinsic-functions"></a>_InterlockedAnd 内部函数
**Microsoft 专用**  
  
 用于在由多线程共享的变量上执行原子按位“与”操作。  
  
## <a name="syntax"></a>语法  
  
```  
long _InterlockedAnd(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_acq(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_HLEAcquire(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_HLERelease(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_nf(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_np(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_rel(  
   long volatile * value,  
   long mask  
);  
char _InterlockedAnd8(  
   char volatile * value,  
   char mask  
);  
char _InterlockedAnd8_acq(  
   char volatile * value,  
   char mask  
);  
char _InterlockedAnd8_nf(  
   char volatile * value,  
   char mask  
);  
char _InterlockedAnd8_np(  
   char volatile * value,  
   char mask  
);  
char _InterlockedAnd8_rel(  
   char volatile * value,  
   char mask  
);  
short _InterlockedAnd16(  
   short volatile * value,  
   short mask  
);  
short _InterlockedAnd16_acq(  
   short volatile * value,  
   short mask  
);  
short _InterlockedAnd16_nf(  
   short volatile * value,  
   short mask  
);  
short _InterlockedAnd16_np(  
   short volatile * value,  
   short mask  
);  
short _InterlockedAnd16_rel(  
   short volatile * value,  
   short mask  
);  
__int64 _InterlockedAnd64(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_acq(  
   __int64 volatile* value,  
   __int64 mask  
);   
__int64 _InterlockedAnd64_HLEAcquire(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_HLERelease(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_nf(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_np(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_rel(  
   __int64 volatile* value,  
   __int64 mask  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in, out] `value`  
 指向第一个操作数的指针，将由结果替换。  
  
 [in] `mask`  
 第二个操作数。  
  
## <a name="return-value"></a>返回值  
 第一个操作数的原始值。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|标头|  
|---------------|------------------|------------|  
|`_InterlockedAnd`, `_InterlockedAnd8`, `_InterlockedAnd16`, `_InterlockedAnd64`|x86、 ARM、 x64|\<intrin.h>|  
|`_InterlockedAnd_acq`, `_InterlockedAnd_nf`, `_InterlockedAnd_rel`, `_InterlockedAnd8_acq`, `_InterlockedAnd8_nf`, `_InterlockedAnd8_rel`, `_InterlockedAnd16_acq`, `_InterlockedAnd16_nf`, `_InterlockedAnd16_rel`, `_InterlockedAnd64_acq`, `_InterlockedAnd64_nf`, `_InterlockedAnd64_rel`|ARM|\<intrin.h>|  
|`_InterlockedAnd_np`, `_InterlockedAnd8_np`, `_InterlockedAnd16_np`, `_InterlockedAnd64_np`|X64|\<intrin.h>|  
|`_InterlockedAnd_HLEAcquire`, `_InterlockedAnd_HLERelease`, `_InterlockedAnd64_HLEAcquire`, `_InterlockedAnd64_HLERelease`|x86、x64|\<immintrin.h>|  
  
## <a name="remarks"></a>备注  
 每个函数名称中的数字指定了自变量的位大小。  
  
 在 ARM 平台上，可以使用带 `_acq` 和 `_rel` 后缀的内部函数获取和发布语义，例如在临界区的起始位置。 带 `_nf`（“无围墙”）后缀的内部函数不能充当内存屏障。  
  
 带 `_np`（“无预取”）后缀的函数可以阻止编译器插入可能的预取操作。  
  
 在支持硬件锁省略 (HLE) 指令的 Intel 平台，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一个发送到处理器的提示，可以通过消除硬件中的锁写步骤来提升速度。 如果在不支持 HLE 的平台上调用这些函数，则忽略此提示。  
  
## <a name="example"></a>示例  
  
```  
// InterlockedAnd.cpp  
// Compile with: /Oi  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedAnd)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FFFF00;  
        long retval;  
        retval = _InterlockedAnd(&data1, data2);  
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);   
}  
```  
  
```Output  
0xff00 0xffff00 0xff00ff00  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)