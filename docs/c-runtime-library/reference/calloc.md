---
title: calloc
description: C 运行时库函数 calloc 分配零初始化内存。
ms.date: 4/2/2020
api_name:
- calloc
- _o_calloc
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
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: 76243342233ea895b947d4aa4a246b316aa8f405
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918723"
---
# <a name="calloc"></a>calloc

使用初始化为 0 的元素分配内存中的数组。

## <a name="syntax"></a>语法

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>参数

*数字*<br/>
元素数量。

size <br/>
每个元素的长度（以字节为单位）。

## <a name="return-value"></a>返回值

**calloc**返回指向已分配空间的指针。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向非**void**类型的指针，请在返回值上使用类型转换。

## <a name="remarks"></a>备注

**Calloc**函数为数字元素数组分配存储空间，每个*数字*元素长度为*大小*字节。 将每个元素初始化为 0。

如果内存分配失败或请求的内存量超过 **_HEAP_MAXREQ**，则**calloc**将**errno**设置为**ENOMEM** 。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

在 Microsoft 实现中，如果*数字*或*大小*为零，则**calloc**将返回指向分配的非零大小块的指针。 尝试通过返回指针读取或写入会导致未定义的行为。

**calloc**使用 c + + [_set_new_mode](set-new-mode.md)函数设置*新的处理程序模式*。 新处理程序模式指示在失败时， **calloc**是否调用[_set_new_handler](set-new-handler.md)设置的新处理程序例程。 默认情况下， **calloc**不会在失败时调用新的处理程序例程来分配内存。 您可以重写此默认行为，以便在**calloc**无法分配内存时，它将调用新的处理程序例程，其方式与在同一原因下**新**运算符失败时相同。 若要重写默认值，请在程序的早期调用：

```C
_set_new_mode(1);
```

早于程序，或与 Newmode.obj 链接 *。OBJ* （请参阅[链接选项](../../c-runtime-library/link-options.md)）。

当应用程序与调试版的 C 运行时库链接时， **calloc**解析为[_calloc_dbg](calloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**calloc**被标记`__declspec(noalias)` `__declspec(restrict)`为，这意味着该函数保证不修改全局变量，并且返回的指针没有化名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**calloc**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[忙](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
