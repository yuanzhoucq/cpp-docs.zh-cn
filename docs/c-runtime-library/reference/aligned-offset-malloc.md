---
title: _aligned_offset_malloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_malloc
- _o__aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 1f13afbab75d2926d1c642c1430a3ffe5ecbac8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350579"
---
# <a name="_aligned_offset_malloc"></a>_aligned_offset_malloc

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

*大小*<br/>
请求的内存分配的大小。

*对齐 (alignment)*<br/>
对齐值，必须是 2 的整数次幂。

*偏移量*<br/>
用于强制对齐的内存分配中的偏移量。

## <a name="return-value"></a>返回值

如果操作失败，指向已分配的内存块的指针或**NULL。**

## <a name="remarks"></a>备注

在嵌套元素上需要对齐的情况下 **，_aligned_offset_malloc**非常有用;例如，如果嵌套类上需要对齐。

**_aligned_offset_malloc**以**马洛克**为基础。有关详细信息，请参阅[malloc](malloc.md)。

**_aligned_offset_malloc**标记为`__declspec(noalias)`，`__declspec(restrict)`表示保证函数不修改全局变量，并且返回的指针不会别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

如果内存分配失败或请求的大小大于 **_HEAP_MAXREQ，** 此函数将**errno**设置**到 ENOMEM。** 有关**errno**的详细信息，请参阅[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外 **，_aligned_offset_malloc**验证其参数。 如果*对齐*不是 2 的功率，或者如果*偏移*量大于或等于*大小*和非零，则此函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则此函数将返回**NULL**并将**errno**设置到**EINVAL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>另请参阅

[数据对齐](../../c-runtime-library/data-alignment.md)<br/>
