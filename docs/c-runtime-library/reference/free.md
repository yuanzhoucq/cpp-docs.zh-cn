---
title: free | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- free
apilocation:
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
apitype: DLLExport
f1_keywords:
- free
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35a1ae1a27b08db14673b125ecbc2978fd4738a3
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100478"
---
# <a name="free"></a>free

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

**免费**函数释放内存块 (*memblock*) 的以前分配通过调用**calloc**， **malloc**，或**realloc**。 已释放的字节数等于分配块时所请求的字节数 (或重新分配的情况下**realloc**)。 如果*memblock*是**NULL**，将忽略指针并**免费**立即返回。 尝试释放无效指针 (指向的未分配的内存块的指针**calloc**， **malloc**，或**realloc**) 可能会影响后续分配请求并导致错误。

如果在释放内存，出现错误**errno**的操作系统从性质上的失败的信息，以及设置。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

释放内存块后， [_heapmin](heapmin.md) 通过合并未使用的区域并将其释放回到操作系统，将堆上的可用内存量降至最低。 未释放给操作系统的已释放内存还原到可用池，并且可用于重新分配。

当与 C 运行时库的调试版本链接应用程序**免费**解析为[_free_dbg](free-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**免费**被标记为`__declspec(noalias)`，这意味着确保该函数不能修改全局变量。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md)。

若要释放使用 [_malloca](malloca.md) 分配的内存，请使用 [_freea](freea.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**free**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [malloc](malloc.md) 的示例。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
