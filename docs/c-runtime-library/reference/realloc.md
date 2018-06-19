---
title: realloc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- realloc
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
- _brealloc
- _nrealloc
- realloc
- _frealloc
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6452d14e0a8630c68d5e179fd94d531db1b667ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408089"
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

*size*<br/>
新大小（字节）。

## <a name="return-value"></a>返回值

**realloc**返回**void**重新分配的 （并且可能已移动的） 内存块指针。

如果不是内存不足以将块展开到给定的大小，原始块保留不变，和**NULL**返回。

如果*大小*为零，则通过指向的块*memblock*释放; 返回值是**NULL**，和*memblock*仍指向已释放的块。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而**void**，使用类型强制转换返回值上。

## <a name="remarks"></a>备注

**Realloc**函数更改分配的内存块的大小。 *Memblock*参数指向的内存块的开头。 如果*memblock*是**NULL**， **realloc**行为与相同的方式**malloc**和分配新块*大小*字节。 如果*memblock*不**NULL**，它应返回上次调用的指针**calloc**， **malloc**，或**realloc**.

*大小*自变量提供新块大小，以字节为单位。 块的内容不随其新旧大小而更改，尽管新块可以在不同的位置。 因为新的块可能在新的内存位置，指针返回**realloc**不保证可传递的指针*memblock*自变量。 **realloc**不为零新分配的内存在缓冲区增长的情况下。

**realloc**设置**errno**到**ENOMEM**如果内存分配失败或内存量请求超过 **_HEAP_MAXREQ**。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**realloc**调用**malloc**才能使用 c + + [_set_new_mode](set-new-mode.md)函数可设置新的处理程序模式。 新的处理程序模式指示是否在失败时， **malloc**是由设置调用新处理程序例程[_set_new_handler](set-new-handler.md)。 默认情况下， **malloc**不调用新处理程序例程上分配内存失败。 你可以重写此默认行为，以便，当**realloc**无法分配内存， **malloc**调用新处理程序例程中相同的方式**新**就是秒当失败时出于同样的原因。 若要重写默认值，请在程序的早期调用：

```C
_set_new_mode(1);
```

或链接到 NEWMODE.OBJ（请参阅[链接选项](../../c-runtime-library/link-options.md)）。

当与 C 运行时库的调试版本链接应用程序**realloc**解析为[_realloc_dbg](realloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**realloc**标记`__declspec(noalias)`和`__declspec(restrict)`，这意味着保证函数不能修改全局变量，并且指针返回不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**realloc**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
