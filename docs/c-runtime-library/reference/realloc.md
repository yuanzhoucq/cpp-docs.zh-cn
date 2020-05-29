---
title: realloc
ms.date: 4/2/2020
api_name:
- realloc
- _o_realloc
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: 15c818ee6f70d02fb9b63f12deef6b1bf3698322
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917943"
---
# <a name="realloc"></a>realloc

重新分配内存块。

## <a name="syntax"></a>语法

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
指向之前已分配内存块的指针。

size <br/>
新大小（字节）。

## <a name="return-value"></a>返回值

**realloc**返回指向重新分配的（并且可能已移动的）内存块的**void**指针。

如果没有足够的可用内存将块扩展到给定大小，则原始块将保持不变，并返回**NULL** 。

如果*size*为零，则释放由*memblock*指向的块;返回值为**NULL**， *memblock*将指向已释放的块。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向非**void**类型的指针，请在返回值上使用类型转换。

## <a name="remarks"></a>备注

**Realloc**函数更改已分配内存块的大小。 *Memblock*参数指向内存块的开头。 如果*memblock*为**NULL**，则**realloc**的行为方式与**malloc**相同，并分配一个*大小*为字节的新块。 如果*memblock*不为**NULL**，则它应为先前对**calloc**、 **malloc**或**realloc**的调用返回的指针。

*Size*参数提供块的新大小（以字节为单位）。 块的内容不随其新旧大小而更改，尽管新块可以在不同的位置。 因为新块可以在新的内存位置，所以**realloc**返回的指针不一定是通过*memblock*参数传递的指针。 在缓冲区增长时， **realloc**不会为新分配的内存分配零。

如果内存分配失败或请求的内存量超过 **_HEAP_MAXREQ**，则**realloc**将**errno**设置为**ENOMEM** 。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**realloc**调用**Malloc**以便使用 c + + [_set_new_mode](set-new-mode.md)函数设置新的处理程序模式。 新处理程序模式指示在失败时， **malloc**是否调用由[_set_new_handler](set-new-handler.md)设置的新处理程序例程。 默认情况下，在无法分配内存时， **malloc**不会调用新的处理程序例程。 您可以重写此默认行为，以便在**realloc**无法分配内存时， **malloc**会调用新的处理程序例程，其方式与在同一原因下**新**运算符失败时相同。 若要重写默认值，请在程序的早期调用：

```C
_set_new_mode(1);
```

或链接到 NEWMODE.OBJ（请参阅[链接选项](../../c-runtime-library/link-options.md)）。

当应用程序与调试版的 C 运行时库链接时， **realloc**解析为[_realloc_dbg](realloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**realloc**被标记`__declspec(noalias)` `__declspec(restrict)`为，这意味着该函数保证不修改全局变量，并且返回的指针没有化名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**realloc**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[忙](free.md)<br/>
[malloc](malloc.md)<br/>
