---
title: _fseek_nolock、_fseeki64_nolock | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fseek_nolock
- _fseeki64_nolock
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fseek_nolock
- _fseeki64_nolock
- fseek_nolock
- fseeki64_nolock
dev_langs:
- C++
helpviewer_keywords:
- _fseek_nolock function
- fseeki64_nolock function
- file pointers [C++], moving
- fseek_nolock function
- _fseeki64_nolock function
- seek file pointers
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b1ce866f7438ebc677156e6cfc9113f9725b65d
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2018
ms.locfileid: "42572433"
---
# <a name="fseeknolock-fseeki64nolock"></a>_fseek_nolock、_fseeki64_nolock

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

*offset*<br/>
*origin* 中的字节数。

*origin*<br/>
初始位置。

## <a name="return-value"></a>返回值

与相同[fseek](fseek-fseeki64.md)并[_fseeki64](fseek-fseeki64.md)分别。

## <a name="remarks"></a>备注

这些函数是的非锁定版本[fseek](fseek-fseeki64.md)并[_fseeki64](fseek-fseeki64.md)分别。 这些是与相同[fseek](fseek-fseeki64.md)并[_fseeki64](fseek-fseeki64.md) ，只不过它们不受干扰从其他线程。 这些函数可能更快，因为它们不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fseek_nolock**， **_fseeki64_nolock**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
