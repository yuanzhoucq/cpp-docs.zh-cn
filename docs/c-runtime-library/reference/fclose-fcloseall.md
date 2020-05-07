---
title: fclose、_fcloseall
ms.date: 4/2/2020
api_name:
- fclose
- _fcloseall
- _o__fcloseall
- _o_fclose
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 3f8567f7bb01c519938f5a4e28bbb33bce09dffe
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920231"
---
# <a name="fclose-_fcloseall"></a>fclose、_fcloseall

关闭流（**fclose**）或关闭所有打开的流（**_fcloseall**）。

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

如果流已成功关闭， **fclose**将返回0。 **_fcloseall**返回关闭的流总数。 这两个函数都返回**EOF**来指示错误。

## <a name="remarks"></a>备注

**Fclose**函数关闭*流*。 如果*stream*为**NULL**，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则**fclose**会将**Errno**设置为**EINVAL**并返回**EOF**。 建议在调用此函数之前始终检查*流*指针。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**_Fcloseall**函数关闭所有打开的流，除了**stdin**、 **stdout**、 **stderr** （在 MS-DOS 中， **_stdaux**和 **_stdprn**）。 它还关闭并删除由**tmpfile**创建的所有临时文件。 在这两个函数中，与流相关联的所有缓冲区在关闭前都会进行刷新。 系统分配的缓冲区在流关闭时释放。 用户使用**setbuf**和**setvbuf**分配的缓冲区不会自动释放。

**注意：** 将这些函数用于关闭流时，基础文件描述符和 OS 文件句柄（或套接字）以及流都将被关闭。 因此，如果最初以文件句柄或文件描述符的形式打开该文件，并使用**fclose**关闭该文件，则也不要调用 **_close**来关闭文件说明符;请勿调用 Win32 函数**CloseHandle**来关闭文件句柄。

**fclose**和 **_fcloseall**包含代码来防范其他线程的干扰。 有关**fclose**的非锁定版本，请参阅 **_fclose_nolock**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [fopen](fopen-wfopen.md) 的示例。

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen，_wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
