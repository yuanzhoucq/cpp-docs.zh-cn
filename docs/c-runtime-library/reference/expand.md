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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5abd90f6106cbca54a9c869841ff70383edb5edc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234141"
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

**_expand**返回指向重新分配的内存块的 void 指针。 与**realloc**不同， **_expand**无法移动块以更改其大小。 因此，如果有足够的内存可用于扩展块而不移动，则 **_expand**的*memblock*参数与返回值相同。

**_expand**在其操作过程中检测到错误时，将返回**NULL** 。 例如，如果使用 **_expand**来收缩内存块，则可能会检测到小块堆中的损坏或无效的块指针，并返回**NULL**。

如果内存不足，无法将块展开到给定的大小，则该函数将返回**NULL**。 **_expand**从不返回扩展到小于请求的大小的块。 如果发生失败， **errno**将指示失败的性质。 有关**errno**的详细信息，请参阅[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要检查项的新大小，请使用 **_msize**。 若要获取指向类型而非的指针 **`void`** ，请在返回值上使用类型转换。

## <a name="remarks"></a>备注

**_Expand**函数通过尝试扩展或收缩块，而不将其位置移到堆中来更改以前分配的内存块的大小。 *Memblock*参数指向块的开头。 *Size*参数提供块的新大小（以字节为单位）。 根据新大小和旧大小中的较短者，块内容保持不变。 *memblock*不应是已释放的块。

> [!NOTE]
> 在64位平台上，如果新大小小于当前大小，则 **_expand**可能不会将块收缩;特别是，如果块的大小小于16K，因而在低碎片堆中分配， **_expand**会保持块不变，并返回*memblock*。

当应用程序与调试版的 C 运行时库链接时， **_expand**解析为[_expand_dbg](expand-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

此函数验证其参数。 如果*memblock*为 null 指针，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且该函数将返回**NULL**。 如果*size*大于 **_HEAP_MAXREQ**，则**errno**设置为**ENOMEM** ，并且函数返回**NULL**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

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
[忙](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
