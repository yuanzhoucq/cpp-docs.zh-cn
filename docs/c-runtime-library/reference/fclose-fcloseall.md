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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b2ee14c5fc8bb47cc2652443c0263bd14147c90d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347493"
---
# <a name="fclose-_fcloseall"></a>fclose、_fcloseall

关闭流 （**关闭**） 或关闭所有打开的流 （**_fcloseall**）。

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

如果流成功关闭，**则关闭**返回 0。 **_fcloseall**返回关闭的流总数。 两个函数返回**EOF**以指示错误。

## <a name="remarks"></a>备注

**闭合**函数关闭*流*。 如果*流*为**NULL，** 则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行 **，fclose**将**errno**设置到**EINVAL**并返回**EOF**。 建议在调用此函数之前始终检查*流*指针。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**_fcloseall**函数关闭除**紧要**、**抖、****稳（** 和，在 MS-DOS，_stdaux和 **_stdprn）** 之外的所有开放流 **_stdaux**。 它还关闭并删除由**tmpfile**创建的任何临时文件。 在这两个函数中，与流相关联的所有缓冲区在关闭前都会进行刷新。 系统分配的缓冲区在流关闭时释放。 使用**setbuf**和**setvbuf**的用户分配的缓冲区不会自动释放。

**注意：** 将这些函数用于关闭流时，基础文件描述符和 OS 文件句柄（或套接字）以及流都将被关闭。 因此，如果文件最初是作为文件句柄或文件描述符打开的，并且用**fclose**关闭，则不要调用 **_close**来关闭文件描述符;不要调用 Win32 函数**CloseHandle**关闭文件句柄。

**fclose**和 **_fcloseall**包括代码，以防止其他线程的干扰。 有关**fclose**的非锁定版本，请参阅 **_fclose_nolock**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

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
