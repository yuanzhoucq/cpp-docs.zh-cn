---
title: _expand
ms.date: 11/04/2016
apiname:
- _expand
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
ms.openlocfilehash: c1606bedbb1264bddb7674c829fe456f506d6584
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335199"
---
# <a name="expand"></a>_expand

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

*size*<br/>
新大小（字节）。

## <a name="return-value"></a>返回值

**_expand**返回指向重新分配的内存块的 void 指针。 **_expand**，但不同于**realloc**，无法移动块以更改其大小。 因此，如果有足够的内存可用于将块扩展而无需移动它，则*memblock*参数 **_expand**作为返回值相同。

**_expand**将返回**NULL**其操作过程时检测到错误。 例如，如果 **_expand**是用于收缩内存块，它可能会在小块堆或无效的块指针中检测到损坏并返回**NULL**。

如果没有足够的内存将块扩展到给定大小，而无需移动它，则该函数返回**NULL**。 **_expand**永远不会返回块扩展到大小小于请求。 如果失败，则**errno**指示故障的性质。 有关详细信息**errno**，请参阅[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要检查的项的新大小，请使用 **_msize**。 若要获取指向类型以外**void**，使用类型强制转换返回值上。

## <a name="remarks"></a>备注

**_Expand**函数通过尝试扩展或收缩块不在堆中移动其位置的情况下更改以前分配的内存块的大小。 *Memblock*参数指向块的开头。 *大小*参数提供以字节为单位的块的新大小。 根据新大小和旧大小中的较短者，块内容保持不变。 *memblock*不应为已释放的块。

> [!NOTE]
> 在 64 位平台上 **_expand**可能不收缩块，如果新大小小于当前大小; 具体而言，如果块的大小小于 16k，因此在低碎片堆中分配 **_expand**保持块保持不变并返回*memblock*。

当与 C 运行时库的调试版本链接应用程序 **_expand**解析为[_expand_dbg](expand-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

此函数验证其参数。 如果*memblock*是空指针，此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**并且该函数返回**NULL**。 如果*大小*大于 **_HEAP_MAXREQ**， **errno**设置为**ENOMEM**并且该函数返回**NULL**.

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
