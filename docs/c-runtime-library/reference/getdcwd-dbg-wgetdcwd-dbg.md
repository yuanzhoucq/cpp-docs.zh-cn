---
title: _getdcwd_dbg、_wgetdcwd_dbg
ms.date: 11/04/2016
apiname:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
apitype: DLLExport
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
ms.openlocfilehash: 700cfe732dc390ca59a976694403bb3d91af5980
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331845"
---
# <a name="getdcwddbg-wgetdcwddbg"></a>_getdcwd_dbg、_wgetdcwd_dbg

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

*drive*<br/>
磁盘驱动器的名称。

*buffer*<br/>
路径的存储位置。

*maxlen*<br/>
以字符为单位的路径的最大长度： **char**有关 **_getdcwd_dbg**并**wchar_t**有关 **_wgetdcwd_dbg**。

*blockType*<br/>
内存块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向已请求分配操作的源文件名或**NULL**。

*linenumber*<br/>
请求分配操作所在的源文件中的行数或**NULL**。

## <a name="return-value"></a>返回值

返回一个指向*缓冲区*。 一个**NULL**返回值指示错误，并**errno**设置为**ENOMEM**，，该值指示是否有足够的内存来分配*maxlen*字节 (时**NULL**参数指定为*缓冲区*)，或设置为**ERANGE**，指示路径的长度超过*maxlen*字符。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Getdcwd_dbg**并 **_wgetdcwd_dbg**函数是相同 **_getdcwd**并 **_wgetdcwd**只不过，当 **_DEBUG**是定义，这些函数将使用的调试版本**malloc**并 **_malloc_dbg**来分配内存，如果**NULL**传递作为*缓冲区*参数。 有关详细信息，请参阅 [_malloc_dbg](malloc-dbg.md)。

在大多数情况下，无需显式调用这些函数。 相反，您可以定义 **_CRTDBG_MAP_ALLOC**标志。 当 **_CRTDBG_MAP_ALLOC**定义，则调用 **_getdcwd**并 **_wgetdcwd**重新映射到 **_getdcwd_dbg**和 **_wgetdcwd_dbg**，分别与*blockType*设置为 **_NORMAL_BLOCK**。 因此，不需要显式调用这些函数，除非你想要将标记作为堆块 **_CLIENT_BLOCK**。 有关详细信息，请参阅[调试堆的块类型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[目录控制](../../c-runtime-library/directory-control.md)<br/>
[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
