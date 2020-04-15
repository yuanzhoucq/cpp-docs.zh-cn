---
title: _aligned_offset_recalloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_recalloc
- _o__aligned_offset_recalloc
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
- aligned_offset_recalloc
- _aligned_offset_recalloc
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
ms.openlocfilehash: 4c710712138d07191468cdc7ef02fc75e2f46dad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350540"
---
# <a name="_aligned_offset_recalloc"></a>_aligned_offset_recalloc

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

*number*<br/>
元素数量。

*大小*<br/>
每个元素的长度（以字节为单位）。

*对齐 (alignment)*<br/>
对齐值，必须是 2 的整数次幂。

*偏移量*<br/>
用于强制对齐的内存分配中的偏移量。

## <a name="return-value"></a>返回值

**_aligned_offset_recalloc**返回指向重新分配（并可能移动）内存块的空指针。 如果大小为零且缓冲区参数不是**NULL，** 或者没有足够的可用内存将块扩展到给定大小，则返回值为**NULL。** 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。

**_aligned_offset_recalloc**标记为`__declspec(noalias)`，`__declspec(restrict)`表示保证函数不修改全局变量，并且返回的指针不会别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

## <a name="remarks"></a>备注

与[_aligned_offset_malloc](aligned-offset-malloc.md)**一样，_aligned_offset_recalloc**允许在结构内的偏移量下对齐结构。

**_aligned_offset_recalloc**是基于**马洛克**。 有关使用 **_aligned_offset_malloc**的详细信息，请参阅[malloc](malloc.md)。 如果*memblock*为**NULL，** 则函数在内部调用 **_aligned_offset_malloc。**

如果内存分配失败或请求的大小（*数字* * *大小*）大于 **_HEAP_MAXREQ，** 此函数将**errno**设置**ENOMEM。** 有关**errno**的详细信息，请参阅[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外 **，_aligned_offset_recalloc**验证其参数。 如果*对齐*不是 2 的功率，或者如果*偏移*量大于或等于请求的大小和非零，则此函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则此函数将返回**NULL**并将**errno**设置到**EINVAL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<malloc.h>|

## <a name="see-also"></a>另请参阅

[数据对齐](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
