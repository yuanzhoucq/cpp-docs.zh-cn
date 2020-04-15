---
title: _getdcwd、_wgetdcwd
ms.date: 4/2/2020
api_name:
- _getdcwd
- _wgetdcwd
- _o__getdcwd
- _o__wgetdcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
ms.openlocfilehash: 3a4ca8ff3f1153893282c65bc4c2becd687138ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344401"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd、_wgetdcwd

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

*驱动*<br/>
一个指定驱动器的非负整数（0 = 默认驱动器，1 = A，2 = B，依此类推）。

如果指定的驱动器不可用，或者无法确定驱动器类型（例如，可移动、固定、CD-ROM、RAM 磁盘或网络驱动器），则调用无效参数处理程序。 有关详细信息，请参阅[参数验证](../../c-runtime-library/parameter-validation.md)。

*缓冲区*<br/>
路径的存储位置，或为 **NULL**。

如果指定**NULL，** 则此函数通过使用**malloc**分配至少*最大大小的*缓冲区，**并且_getdcwd**的返回值是指向已分配的缓冲区的指针。 可以通过调用**空闲**并传递指针来释放缓冲区。

*马克斯伦*<br/>
指定路径最大长度的非零正整数，以字符表示 **：_getdcwd****的字符****wchar_t****，_wgetdcwdwchar_t。**

如果*maxlen*小于或等于零，则调用无效参数处理程序。 有关详细信息，请参阅[参数验证](../../c-runtime-library/parameter-validation.md)。

## <a name="return-value"></a>返回值

指向表示指定驱动器上当前工作目录的完整路径的字符串的指针，或**NULL**，指示错误。

如果*缓冲区*被指定为**NULL，** 并且内存不足以分配*maxlen*字符，则会发生错误并将**errno**设置为**ENOMEM**。 如果路径的长度（包括终止空字符）超过*maxlen，* 则会发生错误，并将**errno**设置为**ERANGE**。 有关这些错误代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_getdcwd**函数获取指定驱动器上当前工作目录的完整路径并将其存储在*缓冲区*中。 如果当前工作目录设置为根目录，则字符串以反斜杠 (\\) 结尾。 如果当前工作目录设置为根目录之外的目录，则字符串以该目录的名称结尾，而不是以反斜杠结尾。

**_wgetdcwd**是 **_getdcwd**的宽字符版本，其*缓冲区*参数和返回值是宽字符字符串。 否则 **，_wgetdcwd**和 **_getdcwd**行为相同。

此函数是线程安全的，即使它依赖于本身不是线程安全的 **GetFullPathName**。 但是，如果你的多线程应用程序调用此函数和 [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew)，则可以违反线程安全性。

具有 **_nolock**后缀的此函数的版本与此函数行为相同，只不过它不是线程安全的，并且不受到其他线程的干扰。 有关详细信息，请参阅 [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)。

定义 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**时，对 **_getdcwd**和 **_wgetdcwd**的调用将替换为对 **_getdcwd_dbg**和 **_wgetdcwd_dbg**的调用，以便您可以调试内存分配。 有关详细信息，请参阅[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参见 [_getdrive](getdrive.md)中的示例。

## <a name="see-also"></a>另请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
