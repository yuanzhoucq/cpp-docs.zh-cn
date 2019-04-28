---
title: _aligned_offset_malloc
ms.date: 11/04/2016
apiname:
- _aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 824edfd8bb96d805a030fb205dee62fa9eb4fd06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341764"
---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc

在指定对齐边界分配内存。

## <a name="syntax"></a>语法

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>参数

*size*<br/>
请求的内存分配的大小。

*alignment*<br/>
对齐值，必须是 2 的整数次幂。

*offset*<br/>
用于强制对齐的内存分配中的偏移量。

## <a name="return-value"></a>返回值

指向已分配的内存块的指针或**NULL**如果操作失败。

## <a name="remarks"></a>备注

**_aligned_offset_malloc**在一个嵌套的元素; 需要对齐方式的位置的情况下非常有用的示例中，如果嵌套类需要进行对齐的。

**_aligned_offset_malloc**基于**malloc**; 有关详细信息，请参阅[malloc](malloc.md)。

**_aligned_offset_malloc**砆`__declspec(noalias)`和`__declspec(restrict)`，这意味着确保该函数不能修改全局变量，并且指针返回不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

此函数将**errno**到**ENOMEM**如果内存分配失败或请求的大小是大于 **_HEAP_MAXREQ**。 有关详细信息**errno**，请参阅[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_offset_malloc**验证其参数。 如果*对齐*不是 2 的幂或如果*偏移量*大于或等于*大小*且非零值，此函数调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数返回**NULL** ，并设置**errno**到**EINVAL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>请参阅

[数据对齐](../../c-runtime-library/data-alignment.md)<br/>
