---
title: _get_osfhandle
ms.date: 4/2/2020
api_name:
- _get_osfhandle
- _o__get_osfhandle
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
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: a12c0c93ae15350a4b91a8aa905acb941f8b6a10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345029"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

检索与指定的文件说明符关联的操作系统文件句柄。

## <a name="syntax"></a>语法

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>参数

*Fd*<br/>
现有文件说明符。

## <a name="return-value"></a>返回值

如果*fd*有效，则返回操作系统文件句柄。 否则，将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，它将返回**INVALID_HANDLE_VALUE** （-1）。 它还将**errno**设置到**EBADF，** 指示无效的文件句柄。 为避免将结果用作 Win32 文件句柄时出现警告，请将其转换为**HANDLE**类型。

> [!NOTE]
> 当**stdin、stdout**和**stderr**不与流关联时（例如，在没有控制台窗口的 Windows 应用程序中），这些流的文件描述符值将从**stdout**[_fileno](fileno.md)返回为特殊值 -2。 同样，如果使用 0、1 或 2 作为文件描述符参数而不是调用 **_fileno**的结果，则当文件描述符不与流关联且不设置**errno**时 **，_get_osfhandle**也会返回特殊值 -2。 但是，这不是有效的文件句柄值，尝试使用它的后续调用可能会失败。

有关**EBADF**和其他错误代码的详细信息，请参阅[_doserrno、errno、_sys_errlist和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

要关闭其操作系统 （OS） 文件句柄由 **_get_osfhandle**获取的文件，请调用[_close](close.md)文件描述符*fd*。 切勿在此函数的返回值上调用**CloseHandle。** 基础 OS 文件句柄由*fd*文件描述符拥有，并在*在 fd*上调用[_close](close.md)时关闭。 如果文件描述符由`FILE *`流拥有，则在该`FILE *`流上调用[fclose](fclose-fcloseall.md)将关闭文件描述符和基础 OS 文件句柄。 在这种情况下，不要在文件描述符上调用[_close。](close.md)

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup、_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
