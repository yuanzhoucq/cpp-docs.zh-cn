---
title: _expand
ms.date: 4/2/2020
api_name:
- _expand
- _o__expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: 7f2a789bc5f475411808bc00a4280b7573b67cf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347557"
---
# <a name="_expand"></a>_expand

更改内存块的大小。

## <a name="syntax"></a>语法

```C
void *_expand(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
指向之前已分配内存块的指针。

*大小*<br/>
新大小（字节）。

## <a name="return-value"></a>返回值

**_expand**返回指向重新分配的内存块的空指针。 **_expand，** 不像**真正的块**，不能移动一个方块来改变其大小。 因此，如果有足够的内存可用于展开块而不移动它，则**要_expand**的*memblock*参数与返回值相同。

**_expand**在操作过程中检测到错误时返回**NULL。** 例如，如果 **_expand**用于收缩内存块，它可能会检测小块堆或无效块指针中的损坏，并返回**NULL**。

如果没有足够的内存可用于在不移动块的情况下将块扩展到给定大小，则函数将返回**NULL**。 **_expand**永远不会返回扩展为小于请求的大小的块。 如果发生故障 **，errno**指示故障的性质。 有关**errno**的详细信息，请参阅[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 要检查项目的新大小，请使用 **_msize**。 要获取指向**void**以外的类型的指针，请使用返回值上强制转换的类型。

## <a name="remarks"></a>备注

**_expand**函数通过尝试展开或收缩块而不移动其在堆中的位置来更改以前分配的内存块的大小。 *memblock*参数指向块的开头。 *大小*参数提供块的新大小（以字节为单位）。 根据新大小和旧大小中的较短者，块内容保持不变。 *memblock*不应是已释放的块。

> [!NOTE]
> 在 64 位平台上，如果新大小小于当前大小 **，_expand**可能不会收缩块;特别是，如果块的大小小于 16K，因此在低碎片堆中分配 **，_expand**保留块不变并返回*memblock*。

当应用程序链接到 C 运行时库的调试版本时 **，_expand**解析为[_expand_dbg](expand-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

此函数验证其参数。 如果*memblock*是空指针，则此函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行 **，errno**将设置为**EINVAL，** 并且函数返回**NULL**。 如果*大小*大于 **_HEAP_MAXREQ** **，errno**设置为**ENOMEM，** 函数返回**NULL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[自由](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
