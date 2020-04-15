---
title: _aligned_msize
ms.date: 4/2/2020
api_name:
- _aligned_msize
- _o__aligned_msize
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
- _aligned_msize
- aligned_msize
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
ms.openlocfilehash: 21ae07c90bbf9a729a212a97b7de3e0916f8e2c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350592"
---
# <a name="_aligned_msize"></a>_aligned_msize

返回在堆中分配的存储块的大小。

## <a name="syntax"></a>语法

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
指向内存块的指针。

*对齐 (alignment)*<br/>
对齐值，必须是 2 的整数次幂。

*偏移量*<br/>
用于强制对齐的内存分配中的偏移量。

## <a name="return-value"></a>返回值

返回无符号整数形式的大小（以字节为单位）。

## <a name="remarks"></a>备注

**_aligned_msize**函数返回调用[_aligned_malloc](aligned-malloc.md)或[_aligned_realloc](aligned-realloc.md)分配的内存块的大小（以字节为单位）。 *对齐*值和*偏移*值必须与传递给分配块的函数的值相同。

当应用程序链接到 C 运行时库的调试版本时 **，_aligned_msize**解析为[_aligned_msize_dbg](aligned-msize-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

此函数验证其参数。 如果*memblock*是空指针，或者*对齐*不是 2 的电源 **，_msize**调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果处理了错误，函数将**errno**设置到**EINVAL**并返回 -1。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
