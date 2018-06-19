---
title: _aligned_msize | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_msize
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
- _aligned_msize
- aligned_msize
dev_langs:
- C++
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2375ec8f61a95ec018ea55cc1f891ad8049748c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393100"
---
# <a name="alignedmsize"></a>_aligned_msize

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

*对齐方式*<br/>
对齐值，必须是 2 的整数次幂。

*offset*<br/>
用于强制对齐的内存分配中的偏移量。

## <a name="return-value"></a>返回值

返回无符号整数形式的大小（以字节为单位）。

## <a name="remarks"></a>备注

**_Aligned_msize**函数将返回以字节为单位，通过调用分配的内存块的大小， [_aligned_malloc](aligned-malloc.md)或[_aligned_realloc](aligned-realloc.md)。 *对齐*和*偏移量*值必须是传递给已分配块的函数的值相同。

当与 C 运行时库的调试版本链接应用程序 **_aligned_msize**解析为[_aligned_msize_dbg](aligned-msize-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

此函数验证其参数。 如果*memblock*是 null 指针或*对齐*不是 2 的幂 **_msize**中所述调用无效参数处理程序，[参数验证](../../c-runtime-library/parameter-validation.md). 如果处理该错误，该函数将设置**errno**到**EINVAL**并返回-1。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
