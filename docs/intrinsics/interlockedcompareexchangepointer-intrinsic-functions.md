---
title: _InterlockedCompareExchangePointer 内部函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
dev_langs:
- C++
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7845b699fb5dd3f326780c18e6af9a4a3274e232
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372144"
---
# <a name="interlockedcompareexchangepointer-intrinsic-functions"></a>_InterlockedCompareExchangePointer 内部函数

**Microsoft 专用**

如果 `Exchange` 和 `Destination` 地址相等，则执行原子操作，将 `Comparand` 地址存储在 `Destination` 地址中。

## <a name="syntax"></a>语法

```
void * _InterlockedCompareExchangePointer (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_acq (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLEAcquire (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLERelease (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_nf (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_np (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
long _InterlockedCompareExchangePointer_rel (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
```

#### <a name="parameters"></a>参数

*目标*<br/>
[in、 out]指针到指向目标值。 忽略此标记。

*Exchange*<br/>
[in]交换指针。 忽略此标记。

*比较对象*<br/>
[in]若要与目标值比较的指针。 忽略此标记。

## <a name="return-value"></a>返回值

返回值是目标的初始值。

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_InterlockedCompareExchangePointer`|x86、 ARM、 x64|\<intrin.h>|
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h>|
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86、x64|\<immintrin.h>|

## <a name="remarks"></a>备注

`_InterlockedCompareExchangePointer` 执行 `Destination` 地址与 `Comparand` 地址之间的原子比较。 如果 `Destination` 地址与 `Comparand` 地址相等，则 `Exchange` 地址将存储在由 `Destination` 指定的地址中。 否则，不会执行任何操作。

`_InterlockedCompareExchangePointer` 提供了编译器内部函数支持 Win32 Windows SDK [_InterlockedCompareExchangePointer](https://msdn.microsoft.com/library/ff547863.aspx)函数。

有关如何使用的示例`_InterlockedCompareExchangePointer`，请参阅[_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。

ARM 平台上，如果需要（例如在临界区的起点和终点）获取和发布语义，可以使用带 `_acq` 和 `_rel` 后缀的函数。 带 `_nf`（“无围墙”)后缀的 ARM 内部函数不能充当内存屏障。

带 `_np`（“无预取”）后缀的函数可以阻止编译器插入可能的预取操作。

在支持硬件锁省略 (HLE) 指令的 Intel 平台，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一个发送到处理器的提示，可以通过消除硬件中的锁写步骤来提升速度。 如果在不支持 HLE 的平台上调用这些函数，则忽略此提示。

这些例程只能用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[关键字](../cpp/keywords-cpp.md)