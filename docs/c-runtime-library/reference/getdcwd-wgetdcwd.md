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
ms.openlocfilehash: 45c03ed2c057781c082988ac15e838249db0f28a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689710"
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

如果**NULL**指定，则此函数分配的缓冲区至少*maxlen*使用大小**malloc**，和返回值的 **_getdcwd**是指向分配的缓冲区的指针。 可以通过调用释放缓冲区**免费**并将其传递指针。

*maxlen*<br/>
一个非零正整数，指定字符相对路径的最大长度： **char**有关 **_getdcwd**并**wchar_t**为 **_wgetdcwd**.

如果*maxlen*不是大于零中, 所述的无效参数处理程序[参数验证](../../c-runtime-library/parameter-validation.md)，调用。

## <a name="return-value"></a>返回值

表示指定的驱动器上的当前工作目录的完整路径的字符串指针或**NULL**，指示错误。

如果*缓冲区*指定为**NULL** ，并且没有足够的内存来分配*maxlen*字符，就会出错并且**errno**是设置为**ENOMEM**。 如果路径，其中包括终止 null 字符，长度超过*maxlen*，就会出错并**errno**设置为**ERANGE**。 有关这些错误代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Getdcwd**函数获取指定驱动器上的当前工作目录的完整路径，并将其存储在*缓冲区*。 如果当前工作目录设置为根目录，则字符串以反斜杠 (\\) 结尾。 如果当前工作目录设置为根目录之外的目录，则字符串以该目录的名称结尾，而不是以反斜杠结尾。

**_wgetdcwd**是宽字符版本 **_getdcwd**，并将其*缓冲区*参数和返回值都是宽字符字符串。 否则为 **_wgetdcwd**并 **_getdcwd**行为方式相同。

此函数是线程安全的，即使它依赖于本身不是线程安全的 **GetFullPathName**。 但是，则可以违反线程安全性，如果在多线程应用程序调用此函数和[GetFullPathNameA](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)。

具有此函数的版本 **_nolock**后缀，对此函数上行为相同，只不过它不是线程安全且不受干扰从其他线程。 有关详细信息，请参阅 [_getdcwd_nolock、_wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)。

当 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**定义，则调用 **_getdcwd**并 **_wgetdcwd** 对的调用替换为 **_getdcwd_dbg**并 **_wgetdcwd_dbg** ，以便能够调试内存分配。 有关详细信息，请参阅 [_getdcwd_dbg、_wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
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
