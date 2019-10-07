---
title: _ReadWriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: d755d045970da01d2eee33377c1452191eac4fe2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217981"
---
# <a name="_readwritebarrier"></a>_ReadWriteBarrier

**Microsoft 专用**

限制可重新排列调用点上的内存访问的编译器优化。

> [!CAUTION]
> 已全部弃用且不应使用 `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 编译器内部函数和 `MemoryBarrier` 宏。 对于线程间的通信, 请使用[ C++标准库](../standard-library/cpp-standard-library-reference.md)中定义的机制, 例如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)和[std::\<原子 T >](../standard-library/atomic.md)。 对于硬件访问, 请将[/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)编译器选项与[volatile](../cpp/volatile-cpp.md)关键字一起使用。

## <a name="syntax"></a>语法

```C
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_ReadWriteBarrier`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

`_ReadWriteBarrier` 内部函数将限制可删除或重新排列调用点上的内存访问的编译器优化。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_WriteBarrier](../intrinsics/writebarrier.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[关键字](../cpp/keywords-cpp.md)
