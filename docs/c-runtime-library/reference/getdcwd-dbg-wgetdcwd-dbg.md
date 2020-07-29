---
title: _getdcwd_dbg、_wgetdcwd_dbg
ms.date: 11/04/2016
api_name:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
ms.openlocfilehash: a31617445ccb0640042be41ee4f710e528b9ceb7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229449"
---
# <a name="_getdcwd_dbg-_wgetdcwd_dbg"></a>_getdcwd_dbg、_wgetdcwd_dbg

[_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md) 函数的调试版本（仅在调试过程中可用）。

## <a name="syntax"></a>语法

```C
char *_getdcwd_dbg(
   int drive,
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetdcwd_dbg(
   int drive,
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*光驱*<br/>
磁盘驱动器的名称。

*宽限*<br/>
路径的存储位置。

*maxlen*<br/>
路径的最大长度（字符）： **`char`** 适用于 **_getdcwd_dbg**和 **`wchar_t`** **_wgetdcwd_dbg**。

*blockType*<br/>
内存块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向请求分配操作的源文件名的指针或**NULL**。

*linenumber*<br/>
请求分配操作所在的源文件中的行号或**NULL**。

## <a name="return-value"></a>返回值

返回一个指向*缓冲区*的指针。 **空**返回值指示错误， **Errno**设置为**ENOMEM**，指示内存不足，无法分配*maxlen*字节（当**空**参数作为*缓冲区*提供时）或**ERANGE**（指示路径长度超过*maxlen*个字符）。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Getdcwd_dbg**和 **_wgetdcwd_dbg**函数与 **_getdcwd**和 **_wgetdcwd**相同，不同之处在于，定义 **_DEBUG**时，这些函数将使用**malloc**和 **_malloc_dbg**的调试版本来分配内存。 **NULL** *buffer* 有关详细信息，请参阅 [_malloc_dbg](malloc-dbg.md)。

在大多数情况下，无需显式调用这些函数。 您可以改为定义 **_CRTDBG_MAP_ALLOC**标志。 定义 **_CRTDBG_MAP_ALLOC**时，对 **_getdcwd**和 **_wgetdcwd**的调用将分别重新映射到 **_getdcwd_dbg**和 **_wgetdcwd_dbg**，并将*blockType*设置为 **_NORMAL_BLOCK**。 因此，无需显式调用这些函数，除非你希望将堆块标记为 **_CLIENT_BLOCK**。 有关详细信息，请参阅[调试堆的块类型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[目录控件](../../c-runtime-library/directory-control.md)<br/>
[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
