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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 085bf20a12d9b77be0977521bde2ab75d9b2636a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918288"
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

*fd*<br/>
现有文件说明符。

## <a name="return-value"></a>返回值

如果*fd*有效，则返回操作系统文件句柄。 否则，将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将返回**INVALID_HANDLE_VALUE** （-1）。 它还将**errno**设置为**ebadf (**，以指示无效的文件句柄。 若要避免在将结果用作 Win32 文件句柄时出现警告，请将其转换为**句柄**类型。

> [!NOTE]
> 如果**stdin**、 **stdout**和**stderr**与流不关联（例如，在没有控制台窗口的 Windows 应用程序中），则这些流的文件描述符值将作为特殊值2返回[_fileno](fileno.md) 。 同样，如果使用0、1或2作为文件描述符参数而不是调用 **_fileno**的结果，则在文件描述符不与流相关联时， **_get_osfhandle**也将返回特殊值2，并且不设置**errno**。 但是，这不是有效的文件句柄值，尝试使用它的后续调用可能会失败。

有关**ebadf (** 和其他错误代码的详细信息，请参阅[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

若要关闭 **_get_osfhandle**获取其操作系统（OS）文件句柄的文件，请在文件描述符*fd*上调用[_close](close.md) 。 不要对此函数的返回值调用**CloseHandle** 。 基础 OS 文件句柄由*fd*文件描述符所有，并在*fd*上调用[_close](close.md)时关闭。 如果文件描述符由某个`FILE *`流拥有，则对该`FILE *`流调用[fclose](fclose-fcloseall.md)将关闭文件描述符和基础 OS 文件句柄。 在这种情况下，请不要在文件描述符上调用[_close](close.md) 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

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
