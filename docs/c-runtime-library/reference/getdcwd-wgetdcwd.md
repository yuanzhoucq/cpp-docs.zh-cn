---
title: _getdcwd、_wgetdcwd | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getdcwd
- _wgetdcwd
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
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
dev_langs:
- C++
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0ccc526b196982402ca3b795276df8c790ad35a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="getdcwd-wgetdcwd"></a>_getdcwd、_wgetdcwd

在指定的驱动器上获取当前工作目录的完整路径。

## <a name="syntax"></a>语法

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>参数

*驱动器*<br/>
一个指定驱动器的非负整数（0 = 默认驱动器，1 = A，2 = B，依此类推）。

如果指定的驱动器不可用，或者无法确定驱动器的类型（例如，可移动的、固定的、CD-ROM、RAM 磁盘或网络驱动器），则会调用 [Parameter Validation](../../c-runtime-library/parameter-validation.md)中介绍的无效参数处理程序。

*buffer*<br/>
路径的存储位置，或为 **NULL**。

如果**NULL**指定，则此函数分配的缓冲区至少*maxlen*大小使用**malloc**，和返回值的 **_getdcwd**是指向已分配的缓冲区的指针。 可以通过调用来释放缓冲区**免费**并将其传递指针。

*maxlen*<br/>
一个非零正整数，以字符为单位指定的路径的最大长度： **char**为 **_getdcwd**和**wchar_t**为 **_wgetdcwd**.

如果*maxlen*不大于零中, 所述的无效参数处理程序[参数验证](../../c-runtime-library/parameter-validation.md)，调用。

## <a name="return-value"></a>返回值

为表示指定驱动器上当前工作目录的完整路径的字符串的指针或**NULL**，指示错误。

如果*缓冲区*指定为**NULL**且存在内存不足，无法分配*maxlen*字符，出现错误和**errno**是设置为**ENOMEM**。 如果包含终止 null 字符的路径长度超过*maxlen*，发生错误和**errno**设置为**ERANGE**。 有关这些错误代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Getdcwd**函数将指定的驱动器上获取当前工作目录的完整路径并将其存储在*缓冲区*。 如果当前工作目录设置为根目录，则字符串以反斜杠 (\\) 结尾。 如果当前工作目录设置为根目录之外的目录，则字符串以该目录的名称结尾，而不是以反斜杠结尾。

**_wgetdcwd**是宽字符版本的 **_getdcwd**，并将其*缓冲区*参数和返回值都是宽字符字符串。 否则为 **_wgetdcwd**和 **_getdcwd**具有相同行为。

此函数是线程安全的，即使它依赖于本身不是线程安全的 **GetFullPathName**。 但是，如果你的多线程应用程序调用此函数和 **GetFullPathName**，则可以违反线程安全性。 有关详细信息，请转到 [MSDN 库](http://go.microsoft.com/fwlink/p/?linkid=150542)，然后搜索 **GetFullPathName**。

具有此函数的版本 **_nolock**后缀对此函数上行为相同，只不过它不是线程安全，并且不受干扰其他线程。 有关详细信息，请参阅 [_getdcwd_nolock、_wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)。

当 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**定义，则调用 **_getdcwd**和 **_wgetdcwd** 对的调用替换为 **_getdcwd_dbg**和 **_wgetdcwd_dbg** ，以便你能够调试内存分配。 有关详细信息，请参阅 [_getdcwd_dbg、_wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_getdrive](getdrive.md) 中的示例。

## <a name="see-also"></a>请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
