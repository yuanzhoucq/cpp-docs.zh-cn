---
title: _ReadBarrier
ms.date: 11/04/2016
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: d898f85398fffa79a9b484f0f82343b1675b61e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565156"
---
# <a name="readbarrier"></a>_ReadBarrier

**Microsoft 专用**

限制可重新排列调用点上的内存访问操作的编译器优化。

> [!CAUTION]
>  已全部弃用且不应使用 `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 编译器内部函数和 `MemoryBarrier` 宏。 对于线程间的通信，如使用机制[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)并[std:: atomic\<T >](../standard-library/atomic.md)中定义的[c + + 标准库](../standard-library/cpp-standard-library-reference.md). 对于硬件访问，使用[/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)编译器选项一起使用[易失性](../cpp/volatile-cpp.md)关键字。

## <a name="syntax"></a>语法

```
void _ReadBarrier(void);
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_ReadBarrier`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`_ReadBarrier` 内部函数将限制可删除或重新排列调用点上的内存访问操作的编译器优化。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[关键字](../cpp/keywords-cpp.md)