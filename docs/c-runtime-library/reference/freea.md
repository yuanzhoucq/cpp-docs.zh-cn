---
title: _freea | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _freea
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
apitype: DLLExport
f1_keywords:
- freea
- _freea
dev_langs:
- C++
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac01f965e159dae19bbbd748c1692058063a211
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="freea"></a>_freea

解除分配或释放内存块。

## <a name="syntax"></a>语法

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
要释放的以前分配的内存块。

## <a name="return-value"></a>返回值

无。

## <a name="remarks"></a>备注

**_Freea**函数释放的内存块 (*memblock*)，为以前分配通过调用[_malloca](malloca.md)。 **_freea**检查以确定是否堆或堆栈上分配内存时。 如果被在堆栈上分配 **_freea**不执行任何操作。 如果被分配到堆上，则已释放的字节数等于分配块时请求的字节数。 如果*memblock*是**NULL**，忽略指针和 **_freea**立即返回。 尝试释放了无效的指针 (指向由未分配的内存块的指针 **_malloca**) 可能会影响后续分配请求，并会导致错误。

**_freea**调用**免费**内部如果找到，堆上分配内存。 内存是在堆上还是在堆栈上由内存中的标记决定，该内存地址紧接所分配的内存。

如果在释放内存，发生错误**errno**从操作系统的特性的失败的信息，以及设置。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

释放内存块后， [_heapmin](heapmin.md) 通过合并未使用的区域并将其释放回到操作系统，将堆上的可用内存量降至最低。 未释放给操作系统的已释放内存还原到可用池，并且可用于重新分配。

调用 **_freea**必须附带对所有调用 **_malloca**。 它也是错误的调用 **_freea**两次在相同的内存。 特别是与 C 运行时库的调试版本链接应用程序时[_malloc_dbg](malloc-dbg.md)启用通过定义功能 **_CRTDBG_MAP_ALLOC**，很容易地查找缺少或重复调用 **_freea**。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**_freea**标记`__declspec(noalias)`，这意味着，保证函数不能修改全局变量。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_freea**|\<stdlib.h> 和 \<malloc.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参见 [_malloca](malloca.md) 的示例。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
