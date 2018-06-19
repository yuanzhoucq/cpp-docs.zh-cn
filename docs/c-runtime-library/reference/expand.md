---
title: _expand | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f709df131ded856881dc171c2e1549d3d5d378e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402346"
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

**_expand**返回指向重新分配的内存块的 void 指针。 **_expand**与**realloc**，不能移动一个块，可以更改其大小。 因此，如果没有足够的内存可用于将块展开而无需移动它， *memblock*参数 **_expand**返回的值相同。

**_expand**返回**NULL**其操作期间时检测到错误。 例如，如果 **_expand**是用来收缩的内存块，它可能检测损坏的小块堆集或无效的块指针，并返回**NULL**。

如果没有足够内存可用于将块展开到给定的大小，而无需移动它，该函数返回**NULL**。 **_expand**永远不会返回一个块展开为大小小于请求。 如果发生故障， **errno**指示故障的性质。 有关详细信息**errno**，请参阅[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要检查的项的新大小，请使用 **_msize**。 若要获取指向类型而**void**，使用类型强制转换返回值上。

## <a name="remarks"></a>备注

**_Expand**函数尝试来展开或折叠而无需移动堆中的其位置的块中更改之前分配的内存块的大小。 *Memblock*参数指向的块的开头。 *大小*参数指定了新块大小，以字节为单位。 根据新大小和旧大小中的较短者，块内容保持不变。 *memblock*不应被释放的块。

> [!NOTE]
> 在 64 位平台上 **_expand**可能不协定块，如果新的大小小于比当前的大小; 具体而言，如果块的大小小于 16 K，且在低碎片堆中，因此分配 **_expand**离开块保持不变并返回*memblock*。

当与 C 运行时库的调试版本链接应用程序 **_expand**解析为[_expand_dbg](expand-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

此函数验证其参数。 如果*memblock*是 null 指针，此函数调用无效参数处理程序中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**和该函数将返回**NULL**。 如果*大小*大于 **_HEAP_MAXREQ**， **errno**设置为**ENOMEM**和该函数将返回**NULL**.

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
