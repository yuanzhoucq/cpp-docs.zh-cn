---
title: _ReadWriteBarrier |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReadWriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86d9b970453e33aa12590f935689361d239025af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440363"
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier

**Microsoft 专用**

限制可重新排列调用点上的内存访问的编译器优化。

> [!CAUTION]
>  已全部弃用且不应使用 `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 编译器内部函数和 `MemoryBarrier` 宏。 对于线程间的通信，如使用机制[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)并[std:: atomic\<T >](../standard-library/atomic.md)，其定义中[c + + 标准库](../standard-library/cpp-standard-library-reference.md). 对于硬件访问，使用[/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)编译器选项一起使用[易失性](../cpp/volatile-cpp.md)关键字。

## <a name="syntax"></a>语法

```
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_ReadWriteBarrier`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`_ReadWriteBarrier` 内部函数将限制可删除或重新排列调用点上的内存访问的编译器优化。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_WriteBarrier](../intrinsics/writebarrier.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[关键字](../cpp/keywords-cpp.md)