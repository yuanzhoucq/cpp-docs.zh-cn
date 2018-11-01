---
title: _fread_nolock
ms.date: 11/04/2016
apiname:
- _fread_nolock
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
- _fread_nolock
- fread_nolock
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- fread_nolock function
- _fread_nolock function
- streams [C++], reading data from
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
ms.openlocfilehash: 81827363d670c7cdeeddcb86390323bf431c6f98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597283"
---
# <a name="freadnolock"></a>_fread_nolock

读取流中的数据，而不锁定其他线程。

## <a name="syntax"></a>语法

```C
size_t _fread_nolock(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>参数

*buffer*<br/>
数据的存储位置。

*size*<br/>
项目大小（以字节为单位）。

*count*<br/>
要读取的项的最大数量。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

请参阅 [fread](fread.md)。

## <a name="remarks"></a>备注

此函数是的非锁定版本**fread**。 它等同于**fread** ，只不过它不受干扰从其他线程。 它可能更快，因为它不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用此函数，如单线程应用程序或调用范围已处理线程隔离的区域。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fread_nolock**|\<stdio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
