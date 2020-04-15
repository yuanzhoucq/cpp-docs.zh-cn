---
title: _fseek_nolock、_fseeki64_nolock
ms.date: 4/2/2020
api_name:
- _fseek_nolock
- _fseeki64_nolock
- _o__fseek_nolock
- _o__fseeki64_nolock
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fseek_nolock
- _fseeki64_nolock
- fseek_nolock
- fseeki64_nolock
helpviewer_keywords:
- _fseek_nolock function
- fseeki64_nolock function
- file pointers [C++], moving
- fseek_nolock function
- _fseeki64_nolock function
- seek file pointers
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
ms.openlocfilehash: 3533e7897e9c460d3be73b8907a6bd3c96f6888f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345739"
---
# <a name="_fseek_nolock-_fseeki64_nolock"></a>_fseek_nolock、_fseeki64_nolock

将文件指针移到指定位置。

## <a name="syntax"></a>语法

```C
int _fseek_nolock(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64_nolock(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

*偏移量*<br/>
*origin* 中的字节数。

*起源*<br/>
初始位置。

## <a name="return-value"></a>返回值

分别与[fseek](fseek-fseeki64.md)和[_fseeki64](fseek-fseeki64.md)相同。

## <a name="remarks"></a>备注

这些函数分别是[fseek](fseek-fseeki64.md)和[_fseeki64](fseek-fseeki64.md)的非锁定版本。 它们与[fseek](fseek-fseeki64.md)和[_fseeki64](fseek-fseeki64.md)相同，只是它们不受其他线程的干扰。 这些函数可能更快，因为它们不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fseek_nolock**， **_fseeki64_nolock**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[倒](rewind.md)<br/>
