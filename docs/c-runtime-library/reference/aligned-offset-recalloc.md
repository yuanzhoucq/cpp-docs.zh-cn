---
title: _aligned_offset_recalloc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_offset_recalloc
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
- aligned_offset_recalloc
- _aligned_offset_recalloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9297defc32966209dd484da80e9230d6df5dbab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392977"
---
# <a name="alignedoffsetrecalloc"></a>_aligned_offset_recalloc

更改使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0。

## <a name="syntax"></a>语法

```C
void * _aligned_offset_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
当前的内存块指针。

*数*<br/>
元素数量。

*size*<br/>
每个元素的长度（以字节为单位）。

*对齐方式*<br/>
对齐值，必须是 2 的整数次幂。

*offset*<br/>
用于强制对齐的内存分配中的偏移量。

## <a name="return-value"></a>返回值

**_aligned_offset_recalloc**返回指向重新分配的 （并且可能已移动的） 内存块的 void 指针。 返回值是**NULL**如果大小为零且缓冲区自变量不**NULL**，或如果没有内存不足以将块展开到给定的大小。 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。

**_aligned_offset_recalloc**标记`__declspec(noalias)`和`__declspec(restrict)`，这意味着，保证函数不能修改全局变量，并且指针返回不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

## <a name="remarks"></a>备注

如[_aligned_offset_malloc](aligned-offset-malloc.md)， **_aligned_offset_recalloc**允许结构内的偏移量上对齐结构。

**_aligned_offset_recalloc**基于**malloc**。 有关使用 **_aligned_offset_malloc**，请参阅[malloc](malloc.md)。 如果*memblock*是**NULL**，函数调用 **_aligned_offset_malloc**内部。

此函数将**errno**到**ENOMEM**如果内存分配失败或请求的大小 (*数* * *大小*) 大于 **_HEAP_MAXREQ**。 有关详细信息**errno**，请参阅[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_offset_recalloc**验证其参数。 如果*对齐*不是 2 的幂或如果*偏移量*大于或等于请求的大小且不为零，此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则此函数将返回**NULL**和设置**errno**到**EINVAL**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<malloc.h>|

## <a name="see-also"></a>请参阅

[数据对齐](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
