---
title: _aligned_recalloc
ms.date: 11/04/2016
apiname:
- _aligned_recalloc
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
- aligned_recalloc
- _aligned_recalloc
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
ms.openlocfilehash: ce505c5a389d4ff6aa12a88bfc47fb0a6f026eea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335602"
---
# <a name="alignedrecalloc"></a>_aligned_recalloc

更改使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0。

## <a name="syntax"></a>语法

```C
void * _aligned_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
当前的内存块指针。

*number*<br/>
元素数量。

*size*<br/>
每个元素的大小（以字节为单位）。

*alignment*<br/>
对齐值，必须是 2 的整数次幂。

## <a name="return-value"></a>返回值

**_aligned_recalloc**返回指向重新分配的 （并且可能已移动的） 内存块的 void 指针。 返回值是**NULL**如果大小为零且缓冲区参数不是**NULL**，或如果没有足够的可用内存将块扩展到给定大小。 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。

重新分配内存并更改块对齐是错误的。

## <a name="remarks"></a>备注

**_aligned_recalloc**基于**malloc**。 有关使用详细信息 **_aligned_offset_malloc**，请参阅[malloc](malloc.md)。

此函数将**errno**到**ENOMEM**如果内存分配失败或请求的大小是大于 **_HEAP_MAXREQ**。 有关详细信息**errno**，请参阅[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_recalloc**验证其参数。 如果*对齐*不为 2，此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数返回**NULL** ，并设置**errno**到**EINVAL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_aligned_recalloc**|\<malloc.h>|

## <a name="see-also"></a>请参阅

[数据对齐](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
