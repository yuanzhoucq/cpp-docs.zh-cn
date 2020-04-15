---
title: _heapadd
ms.date: 11/04/2016
api_name:
- _heapadd
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapadd
- _heapadd
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
ms.openlocfilehash: c5eeb66ff0e6fb05063ec395e12cd97106ad724d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351320"
---
# <a name="_heapadd"></a>_heapadd

将内存添加到堆。

> [!IMPORTANT]
> 此函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供此函数。

## <a name="syntax"></a>语法

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>参数

*memblock*<br/>
指向堆内存的指针。

*大小*<br/>
要添加的内存大小，以字节为单位。

## <a name="return-value"></a>返回值

如果成功，`_heapadd` 会返回 0；否则，此函数会返回 -1，并将 `errno` 设置为 `ENOSYS`。

有关此代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

从 Visual C++ 4.0 版开始，基础堆结构已移至 C 运行时库，以支持新的调试功能。 因此，基于 Win32 API 的任何平台上不再支持 `_heapadd` 。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|`_heapadd`|\<malloc.h>|\<errno.h>|

有关兼容性的详细信息，请参阅“简介”中的[兼容性](../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[内存分配](../c-runtime-library/memory-allocation.md)<br/>
[自由](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)
