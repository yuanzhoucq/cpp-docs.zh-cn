---
title: _recalloc
ms.date: 11/04/2016
apiname:
- _recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 3bcc238dcb950a8e30af16efc557e99d933efe92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436512"
---
# <a name="recalloc"></a>_recalloc

组合**realloc**并**calloc**。 重新分配内存中的数组并将其元素初始化为 0。

## <a name="syntax"></a>语法

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
指向之前已分配内存块的指针。

*数量*<br/>
元素数量。

*size*<br/>
每个元素的长度（以字节为单位）。

## <a name="return-value"></a>返回值

**_recalloc**将返回**void**指向重新分配的 （并且可能已移动的） 内存块。

如果没有足够的可用内存将块扩展到给定大小，原始块将保持不变，并**NULL**返回。

如果所请求的大小为零，则指向的块*memblock*释放; 返回值是**NULL**，并*memblock*仍指向已释放的块。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型以外**void**，使用类型强制转换返回值上。

## <a name="remarks"></a>备注

**_Recalloc**函数更改已分配的内存块的大小。 *Memblock*参数指向内存块的开头。 如果*memblock*是**NULL**， **_recalloc**的行为方式相同[calloc](calloc.md) ，并分配新的块的*数* * *大小*字节。 将每个元素初始化为 0。 如果*memblock*不是**NULL**，它应为以前调用返回的指针**calloc**， [malloc](malloc.md)，或[realloc](realloc.md).

因为新块可以在新的内存位置，通过返回的指针 **_recalloc**不保证可通过传递的指针*memblock*参数。

**_recalloc**设置**errno**到**ENOMEM**如果内存分配失败或请求的内存量超过 **_HEAP_MAXREQ**。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**recalloc**调用**realloc**若要使用 c + + [_set_new_mode](set-new-mode.md)函数设置新的处理程序模式。 新的处理程序模式将指示是否在失败时， **realloc**是所设置的调用新处理程序例程[_set_new_handler](set-new-handler.md)。 默认情况下**realloc**不会调用新处理程序例程上分配内存失败。 可以重写此默认行为，以便，当 **_recalloc**无法分配内存， **realloc**调用新处理程序例程中相同的方式**新**运算符出于相同原因失败时执行。 若要重写默认值，请在程序的早期调用：

```C
_set_new_mode(1);
```

或链接到 NEWMODE.OBJ。

当与 C 运行时库的调试版本链接应用程序 **_recalloc**解析为[_recalloc_dbg](recalloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**_recalloc**砆`__declspec(noalias)`和`__declspec(restrict)`，这意味着确保该函数不能修改全局变量，并且指针返回不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[链接选项](../../c-runtime-library/link-options.md)<br/>
