---
title: fclose、_fcloseall
ms.date: 11/04/2016
apiname:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 4713ffb7ecdf8da73e5f949bbef7be124dfaf28a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536508"
---
# <a name="fclose-fcloseall"></a>fclose、_fcloseall

关闭流 (**fclose**) 或关闭所有打开的流 (**_fcloseall**)。

## <a name="syntax"></a>语法

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**fclose**如果流已成功关闭，则返回 0。 **_fcloseall**返回已关闭流的总数。 这两个函数返回**EOF**表示出现错误。

## <a name="remarks"></a>备注

**Fclose**函数关闭*流*。 如果*流*是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**fclose**设置**errno**到**EINVAL** ，并返回**EOF**。 建议*流*指针始终在调用此函数之前检查。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**_Fcloseall**函数将关闭所有打开的流，除了**stdin**， **stdout**， **stderr** (以及在 MS-DOS， **_stdaux**并 **_stdprn**)。 它还将关闭并删除创建的任何临时文件**tmpfile**。 在这两个函数中，与流相关联的所有缓冲区在关闭前都会进行刷新。 系统分配的缓冲区在流关闭时释放。 使用用户分配的缓冲区**setbuf**并**setvbuf**不会自动释放。

**注意：** 将这些函数用于关闭流时，基础文件描述符和 OS 文件句柄（或套接字）以及流都将被关闭。 因此，如果最初打开该文件作为文件处理文件描述符和关闭或与**fclose**，不要同时调用 **_close**到关闭的文件描述符; 不要调用 Win32 函数**CloseHandle**关闭文件句柄。

**fclose**并 **_fcloseall**包含代码，从而防止出现来自其他线程的干扰。 有关非锁定版本的**fclose**，请参阅 **_fclose_nolock**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [fopen](fopen-wfopen.md) 的示例。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
