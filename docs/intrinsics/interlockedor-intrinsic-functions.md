---
title: _InterlockedOr 内部函数
ms.date: 12/17/2018
f1_keywords:
- _InterlockedOr8_nf
- _InterlockedOr_HLEAcquire
- _InterlockedOr16_nf
- _InterlockedOr64
- _InterlockedOr8_np
- _InterlockedOr64_cpp
- _InterlockedOr8_acq
- _InterlockedOr_nf
- _InterlockedOr64_acq
- _InterlockedOr_np
- _InterlockedOr8
- _InterlockedOr
- _InterlockedOr64_np
- _InterlockedOr_acq
- _InterlockedOr64_HLERelease
- _InterlockedOr16_np
- _InterlockedOr_cpp
- _InterlockedOr8_rel
- _InterlockedOr64_rel
- _InterlockedOr16_acq
- _InterlockedOr_rel
- _InterlockedOr16_rel
- _InterlockedOr_HLERelease
- _InterlockedOr64_HLEAcquire
- _InterlockedOr16
- _InterlockedOr64_nf
helpviewer_keywords:
- _InterlockedOr_acq intrinsic
- InterlockedOr64 intrinsic
- _InterlockedOr_nf intrinsic
- _InterlockedOr intrinsic
- _InterlockedOr64_HLERelease intrinsic
- _InterlockedOr8_rel intrinsic
- _InterlockedOr8_np intrinsic
- _InterlockedOr64_nf intrinsic
- _InterlockedOr_HLERelease intrinsic
- _InterlockedOr16_np intrinsic
- InterlockedOr intrinsic
- _InterlockedOr8_nf intrinsic
- _InterlockedOr16_nf intrinsic
- _InterlockedOr8_acq intrinsic
- _InterlockedOr64 intrinsic
- _InterlockedOr16 intrinsic
- _InterlockedOr64_acq intrinsic
- _InterlockedOr64_HLEAcquire intrinsic
- _InterlockedOr_np intrinsic
- _InterlockedOr64_rel intrinsic
- _InterlockedOr64_np intrinsic
- _InterlockedOr_rel intrinsic
- _InterlockedOr8 intrinsic
- _InterlockedOr16_acq intrinsic
- _InterlockedOr16_rel intrinsic
- _InterlockedOr_HLEAcquire intrinsic
ms.assetid: 5f265240-7af8-44b7-b952-19f3a9c56186
ms.openlocfilehash: 9748099e4224a8c55cd4455a57c8e849531f1c9a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040470"
---
# <a name="interlockedor-intrinsic-functions"></a>_InterlockedOr 内部函数

**Microsoft 专用**

对由多线程共享的变量执行原子位或操作。

## <a name="syntax"></a>语法

```
long _InterlockedOr(
   long volatile * Value,
   long Mask
);
long _InterlockedOr_acq(
   long volatile * Value,
   long Mask
);
long _InterlockedOr_HLEAcquire(
   long volatile * Value,
   long Mask
);
long _InterlockedOr_HLERelease(
   long volatile * Value,
   long Mask
);
long _InterlockedOr_nf(
   long volatile * Value,
   long Mask
);
long _InterlockedOr_np(
   long volatile * Value,
   long Mask
);
long _InterlockedOr_rel(
   long volatile * Value,
   long Mask
);
char _InterlockedOr8(
   char volatile * Value,
   long Mask
);
char _InterlockedOr8_acq(
   char volatile * Value,
   char Mask
);
char _InterlockedOr8_nf(
   char volatile * Value,
   char Mask
);
char _InterlockedOr8_np(
   char volatile * Value,
   char Mask
);
char _InterlockedOr8_rel(
   char volatile * Value,
   char Mask
);
short _InterlockedOr16(
   short volatile * Value,
   short Mask
);
short _InterlockedOr16_acq(
   short volatile * Value,
   short Mask
);
short _InterlockedOr16_nf(
   short volatile * Value,
   short Mask
);
short _InterlockedOr16_np(
   short volatile * Value,
   short Mask
);
short _InterlockedOr16_rel(
   short volatile * Value,
   short Mask
);
__int64 _InterlockedOr64(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedOr64_acq(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedOr64_HLEAcquire(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedOr64_HLERelease(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedOr64_nf(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedOr64_np(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedOr64_rel(
   __int64 volatile * Value,
   __int64 Mask
);
```

#### <a name="parameters"></a>参数

*值*<br/>
[in、 out]指向要替换为结果的第一个操作数的指针。

*掩码*<br/>
[in]第二个操作数。

## <a name="return-value"></a>返回值

由第一个参数指向的原始值。

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_InterlockedOr`, `_InterlockedOr8`, `_InterlockedOr16`, `_InterlockedOr64`|x86、 ARM、 x64|\<intrin.h>|
|`_InterlockedOr_acq`, `_InterlockedOr_nf`, `_InterlockedOr_rel`, `_InterlockedOr8_acq`, `_InterlockedOr8_nf`, `_InterlockedOr8_rel`, `_InterlockedOr16_acq`, `_InterlockedOr16_nf`, `_InterlockedOr16_rel`, `_InterlockedOr64_acq`, `_InterlockedOr64_nf`, `_InterlockedOr64_rel`|ARM|\<intrin.h>|
|`_InterlockedOr_np`, `_InterlockedOr8_np`, `_InterlockedOr16_np`, `_InterlockedOr64_np`|X64|\<intrin.h>|
|`_InterlockedOr_HLEAcquire`, `_InterlockedOr_HLERelease`, `_InterlockedOr64_HLEAcquire`, `_InterlockedOr64_HLERelease`|x86、x64|\<immintrin.h>|

## <a name="remarks"></a>备注

每个函数名称中的数字指定了参数的位大小。

ARM 平台上，如果需要（例如在临界区的起点和终点）获取和发布语义，可以使用带 `_acq` 和 `_rel` 后缀的函数。 带 `_nf`（“无围墙”）后缀的 ARM 内部函数不能充当内存屏障。

带 `_np`（“无预取”）后缀的函数可以阻止编译器插入可能的预取操作。

在支持硬件锁省略 (HLE) 指令的 Intel 平台，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一个发送到处理器的提示，可以通过消除硬件中的锁写步骤来提升速度。 如果在不支持 HLE 的平台上调用这些函数，则忽略此提示。

## <a name="example"></a>示例

```
// _InterlockedOr.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_InterlockedOr)

int main()
{
        long data1 = 0xFF00FF00;
        long data2 = 0x00FFFF00;
        long retval;
        retval = _InterlockedOr(&data1, data2);
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);
}
```

```Output
0xffffff00 0xffff00 0xff00ff00
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)