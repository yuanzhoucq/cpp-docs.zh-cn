---
title: 可用
ms.date: 4/2/2020
api_name:
- free
- _o_free
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: eefbe957ce5057b5038f98bc8da8fb2f0bdd3d1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345981"
---
# <a name="free"></a>可用

解除分配或释放内存块。

## <a name="syntax"></a>语法

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
要释放的以前分配的内存块。

## <a name="remarks"></a>备注

**自由**函数将分配以前由调用 call call 调用 call 分配给**的**内存块**malloc***（memblock）。* **realloc** 释放的字节数等效于分配块时请求的字节数（或重新分配，在**realloc**的情况下）。 如果*memblock*为**NULL，** 则指针将被忽略，**并且释放**将立即返回。 尝试释放无效指针（指向未由**calloc、malloc**或**realloc**分配的内存**malloc**块的指针）可能会影响后续分配请求并导致错误。

如果释放内存时出现错误，则使用操作系统中有关故障性质的信息设置**errno。** 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

释放内存块后， [_heapmin](heapmin.md) 通过合并未使用的区域并将其释放回到操作系统，将堆上的可用内存量降至最低。 未释放给操作系统的已释放内存还原到可用池，并且可用于重新分配。

当应用程序链接到 C 运行时库的调试版本时，**空闲**解析为[_free_dbg](free-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**free**被`__declspec(noalias)`标记，这意味着保证函数不修改全局变量。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md)。

若要释放使用 [_malloca](malloca.md) 分配的内存，请使用 [_freea](freea.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**自由**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [malloc](malloc.md) 的示例。

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
