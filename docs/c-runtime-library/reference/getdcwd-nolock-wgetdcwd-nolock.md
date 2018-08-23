---
title: _getdcwd_nolock、_wgetdcwd_nolock | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wgetdcwd_nolock
- _getdcwd_nolock
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
- _wgetdcwd_nolock
- tgetdcwd_nolock
- wgetdcwd_nolock
- _getdcwd_nolock
- _tgetdcwd_nolock
- getdcwd_nolock
dev_langs:
- C++
helpviewer_keywords:
- getdcwd_nolock function
- _tgetdcwd_nolock function
- working directory
- tgetdcwd_nolock function
- _getdcwd_nolock function
- current working directory
- wgetdcwd_nolock function
- _wgetdcwd_nolock function
- directories [C++], current working
ms.assetid: d9bdf712-43f8-4173-8f9a-844e82beaa97
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa969bb756754c1a6e1d28ac1b029ee443666ea0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401573"
---
# <a name="getdcwdnolock-wgetdcwdnolock"></a>_getdcwd_nolock、_wgetdcwd_nolock

在指定的驱动器上获取当前工作目录的完整路径。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
char *_getdcwd_nolock(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd_nolock(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>参数

*驱动器*<br/>
硬盘驱动器。

*buffer*<br/>
路径的存储位置。

*maxlen*<br/>
以字符为单位的路径的最大长度： **char**为 **_getdcwd**和**wchar_t**为 **_wgetdcwd**。

## <a name="return-value"></a>返回值

请参阅 [_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md)。

## <a name="remarks"></a>备注

**_getdcwd_nolock**和 **_wgetdcwd_nolock**相同 **_getdcwd**和 **_wgetdcwd**分别，只不过它们不从受保护由其他线程的干扰。 它们可能更快，因为它们不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_nolock**|**_getdcwd_nolock**|**_getdcwd_nolock**|**_wgetdcwd_nolock**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_getdcwd_nolock**|\<direct.h>|
|**_wgetdcwd_nolock**|\<direct.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
