---
title: _InterlockedExchange 内部函数
ms.date: 12/17/2018
f1_keywords:
- _InterlockedExchange_rel
- _InterlockedExchange8_nf
- _InterlockedExchange_acq_cpp
- _InterlockedExchange_nf
- _InterlockedExchange64_nf
- _InterlockedExchange_HLEAcquire
- _InterlockedExchange_cpp
- _InterlockedExchange64_acq_cpp
- _InterlockedExchange64_acq
- _InterlockedExchange64_HLERelease
- _InterlockedExchange8_acq
- _InterlockedExchange16_acq
- _InterlockedExchange
- _InterlockedExchange64_HLEAcquire
- _InterlockedExchange8
- _InterlockedExchange64_rel
- _InterlockedExchange_acq
- _InterlockedExchange16
- _InterlockedExchange16_rel
- _InterlockedExchange16_nf
- _InterlockedExchange64
- _InterlockedExchange_HLERelease
- _InterlockedExchange64_cpp
- _InterlockedExchange8_rel
helpviewer_keywords:
- _InterlockedExchange8
- _InterlockedExchange64 intrinsic
- _InterlockedExchange_acq intrinsic
- InterlockedExchange64 intrinsic
- _InterlockedExchange64_acq intrinsic
- InterlockedExchange64_acq intrinsic
- _InterlockedExchange16_acq
- _InterlockedExchange8_acq
- _InterlockedExchange16
- _InterlockedExchange8_rel
- InterlockedExchange_acq intrinsic
- InterlockedExchange intrinsic
- _InterlockedExchange16_rel
- _InterlockedExchange16_nf
- _InterlockedExchange intrinsic
- _InterlockedExchange8_nf
ms.assetid: be2f232a-6301-462a-a92b-fcdeb8b0f209
ms.openlocfilehash: 3945b8a7516962531050e999e96bdef31b179bbb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59021490"
---
# <a name="interlockedexchange-intrinsic-functions"></a>_InterlockedExchange 内部函数

**Microsoft 专用**

生成原子指令以设置指定的值。

## <a name="syntax"></a>语法

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

#### <a name="parameters"></a>参数

*Target*<br/>
[in、 out]指向要交换的值。 此函数会将此变量设置为 `Value` 并返回其之前的值。

*值*<br/>
[in]指向值的值进行交换`Target`。

## <a name="return-value"></a>返回值

返回由 `Target` 指向的初始值。

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_InterlockedExchange`, `_InterlockedExchange8`, `_InterlockedExchange16`, `_InterlockedExchange64`|x86、 ARM、 x64|\<intrin.h>|
|`_InterlockedExchange_acq`, `_InterlockedExchange_nf`, `_InterlockedExchange_rel`, `_InterlockedExchange8_acq`, `_InterlockedExchange8_nf`, `_InterlockedExchange8_rel`, `_InterlockedExchange16_acq`, `_InterlockedExchange16_nf`, `_InterlockedExchange16_rel`, `_InterlockedExchange64_acq`, `_InterlockedExchange64_nf`, `_InterlockedExchange64_rel`,|ARM|\<intrin.h>|
|`_InterlockedExchange_HLEAcquire`, `_InterlockedExchange_HLERelease`, `_InterlockedExchange64_HLEAcquire`, `_InterlockedExchange64_HLERelease`|x86、x64|\<immintrin.h>|

## <a name="remarks"></a>备注

`_InterlockedExchange` 提供了编译器内部函数支持 Win32 Windows SDK [InterlockedExchange](/windows/desktop/api/winnt/nf-winnt-interlockedexchange)函数。

`_InterlockedExchange` 存在几种变体，这些变体根据其涉及的数据类型和是否使用特定于处理器获取或发布语义而有所不同。

当 `_InterlockedExchange` 函数对 32 位整数值操作时，`_InterlockedExchange8` 对 8 位整数值操作，`_InterlockedExchange16` 对 16 位整数值操作且 `_InterlockedExchange64` 对 64 位整数值操作。

在 ARM 平台上，可以使用带 `_acq` 和 `_rel` 后缀的内部函数获取和发布语义，例如在临界区的起始位置。 带 `_nf`（“无围墙”）后缀的内部函数不能充当内存屏障。

在支持硬件锁省略 (HLE) 指令的 Intel 平台，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一个发送到处理器的提示，可以通过消除硬件中的锁写步骤来提升速度。 如果在不支持 HLE 的平台上调用这些函数，则忽略此提示。

这些例程只能用作内部函数。

## <a name="example"></a>示例

有关如何使用的示例`_InterlockedExchange`，请参阅[_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)