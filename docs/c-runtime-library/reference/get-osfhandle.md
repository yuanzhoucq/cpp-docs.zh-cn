---
title: _get_osfhandle
ms.date: 05/29/2018
apiname:
- _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: cc3b50e3d3f65bee83b8df83aa0adb5c8694e35a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821654"
---
# <a name="getosfhandle"></a>_get_osfhandle

检索与指定的文件说明符关联的操作系统文件句柄。

## <a name="syntax"></a>语法

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>参数

*fd*<br/>
现有文件说明符。

## <a name="return-value"></a>返回值

如果返回的操作系统文件句柄*fd*有效。 否则，将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，它将返回**INVALID_HANDLE_VALUE** (-1)。 它还设置**errno**到**EBADF**，指示无效的文件句柄。 若要避免警告结果用作 Win32 文件句柄时，将其转换为**处理**类型。

> [!NOTE]
> 当**stdin**， **stdout**，并**stderr**不与流 （例如，在一个 Windows 应用程序没有控制台窗口），关联的文件描述符值这些流将返回从[_fileno](fileno.md)为特殊值-2。 同样，如果使用 0、 1 或 2 而不是对的调用结果的文件描述符参数作为 **_fileno**， **_get_osfhandle**不相关联的文件描述符时也会返回特殊值-2在使用流，并且未设置**errno**。 但是，这不是有效的文件句柄值，并尝试使用它的后续调用都可能会失败。

有关详细信息**EBADF**和其他错误代码，请参阅[_doserrno、 errno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

若要关闭其操作系统 (OS) 的文件句柄通过的文件 **_get_osfhandle**，调用[_close](close.md)上的文件描述符*fd*。 永远不会调用**CloseHandle**上此函数的返回值。 基础 OS 文件句柄归*fd*的文件说明符，并关闭时[_close](close.md)上调用*fd*。 如果文件描述符归`FILE *`流，然后调用[fclose](fclose-fcloseall.md)上的`FILE *`流关闭文件描述符和基础 OS 文件句柄。 在这种情况下，不要调用[_close](close.md)上的文件描述符。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup、_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
