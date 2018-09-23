---
title: 全局变量 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.variables
dev_langs:
- C++
helpviewer_keywords:
- global variables
- variables, global
- global variables, Microsoft run-time library
ms.assetid: 01d1551c-2f0c-4f72-935c-6442caccf84f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79359f6f86c66dc37f95c0675675b07888a31646
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058310"
---
# <a name="global-variables"></a>全局变量

Microsoft C 运行时库提供了以下全局变量或宏。 已弃用几个全局变量或宏，以便使用我们建议的更安全的函数版本，而非全局变量。

|变量|描述|
|--------------|-----------------|
|[__argc、\__argv、\__wargv](../c-runtime-library/argc-argv-wargv.md)|包含命令行自变量。|
|[_daylight、_dstbias、_timezone，和 _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)|已否决。 请改为使用 `_get_daylight`、`_get_dstbias`、`_get_timezone` 和 `_get_tzname`。<br /><br /> 调整本地时间；用于一些日期和时间函数。|
|[errno、_doserrno、_sys_errlist 和 _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)|已否决。 请改为使用 `_get_errno`、`_set_errno`、`_get_doserrno`、`_set_doserrno`、`perror` 和 `strerror`。<br /><br /> 存储错误代码和相关信息。|
|[_environ、_wenviron](../c-runtime-library/environ-wenviron.md)|已否决。 请改为使用 `getenv_s`、`_wgetenv_s`、`_dupenv_s`、`_wdupenv_s`、`_putenv_s` 和 `_wputenv_s`。<br /><br /> 指向进程环境字符串的指针数组的指针；在启动时进行初始化。|
|[_fmode](../c-runtime-library/fmode.md)|已否决。 请改为使用 `_get_fmode` 或 `_set_fmode`。<br /><br /> 设置默认文件转换模式。|
|[_iob](../c-runtime-library/iob.md)|控制台、文件和设备的 I/O 控制结构的数组。|
|[_pctype、_pwctype、_wctype、_mbctype、_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)|包含由 character-classification 函数使用的信息。|
|[_pgmptr、_wpgmptr](../c-runtime-library/pgmptr-wpgmptr.md)|已否决。 请改为使用 `_get_pgmptr` 或 `_get_wpgmptr`。<br /><br /> 在程序启动时初始化到该程序的完全限定路径或相对路径、完整程序名或不包含其文件扩展名的程序名，具体取决于调用该程序的方式。|

## <a name="see-also"></a>请参阅

[C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)<br/>
[__argc、\__argv、\__wargv](../c-runtime-library/argc-argv-wargv.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)<br/>
[perror](../c-runtime-library/reference/perror-wperror.md)<br/>
[strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)<br/>
[_get_doserrno](../c-runtime-library/reference/get-doserrno.md)<br/>
[_set_doserrno](../c-runtime-library/reference/set-doserrno.md)<br/>
[_get_errno](../c-runtime-library/reference/get-errno.md)<br/>
[_set_errno](../c-runtime-library/reference/set-errno.md)<br/>
[_dupenv_s、_wdupenv_s](../c-runtime-library/reference/dupenv-s-wdupenv-s.md)<br/>
[getenv、_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s、_wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv、_wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s、_wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)