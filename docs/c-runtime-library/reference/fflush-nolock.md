---
title: _fflush_nolock
ms.date: 11/04/2016
apiname:
- _fflush_nolock
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
- fflush_nolock
- _fflush_nolock
helpviewer_keywords:
- fflush_nolock function
- _fflush_nolock function
- streams, flushing
- flushing
ms.assetid: 5e33c4a1-b10c-4001-ad01-210757919291
ms.openlocfilehash: 721098899525df02dc3b3d121cf894f8056fcb98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334281"
---
# <a name="fflushnolock"></a>_fflush_nolock

刷新流，但不锁定线程。

## <a name="syntax"></a>语法

```C
int _fflush_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*stream*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

请参阅 [fflush](fflush.md)。

## <a name="remarks"></a>备注

此函数是的非锁定版本**fflush**。 它等同于**fflush** ，只不过它不受干扰从其他线程。 它可能更快，因为它不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用此函数，如单线程应用程序或调用范围已处理线程隔离的区域。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fflush_nolock**|\<stdio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
