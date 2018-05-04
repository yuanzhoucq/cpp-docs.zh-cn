---
title: _putenv、_wputenv | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
dev_langs:
- C++
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc7841963584bef19faf60de0112eeea25cb7ffd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="putenv-wputenv"></a>_putenv、_wputenv

创建、修改或删除环境变量。 提供这些函数的更多安全版本；请参阅 [_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _putenv(
   const char *envstring
);
int _wputenv(
   const wchar_t *envstring
);
```

### <a name="parameters"></a>参数

*envstring*<br/>
环境字符串定义。

## <a name="return-value"></a>返回值

返回成功时为 0 或-1，如果出现错误。

## <a name="remarks"></a>备注

**_Putenv**函数将新环境变量添加或修改现有环境变量的值。 环境变量定义过程执行的环境（例如待与程序链接的库的默认搜索路径）。 **_wputenv**是宽字符版本的 **_putenv**; *envstring*参数 **_wputenv**是宽字符字符串。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring*参数必须是指向形式的字符串的指针*varname*=*value_string*，其中*varname*是要添加或修改的环境变量的名称和*value_string*是变量的值。 如果*varname*已属于该环境，其值将由替换*value_string*; 否则为新*varname*变量并将其*value_string*值添加到环境。 可以从环境中删除变量通过指定一个空*value_string*，或换而言之，通过仅指定*varname*=。

**_putenv**和 **_wputenv**影响本地到当前进程环境; 不能用于修改命令级别环境。 也就是说，这些函数只在可由运行时库访问的数据结构上操作，并不在操作系统为进程创建的环境段上操作。 在当前进程终止时，环境将还原到调用进程的级别（在大多数情况下，为操作系统级别）。 但是，修改后的环境可以传递到创建的任何新进程 **_spawn**， **_exec**，或**系统**，这些新进程将获取由添加任何新项 **_putenv**和 **_wputenv**。

不要直接更改环境条目： 请改用 **_putenv**或 **_wputenv**若要更改它。 具体而言，直接释放的元素 **_environ []** 全局数组可能会导致无效的内存进行寻址。

**getenv**和 **_putenv**使用全局变量 **_environ**访问环境表;**_wgetenv**和 **_wputenv**使用 **_wenviron**。 **_putenv**和 **_wputenv**可能会更改的值 **_environ**和 **_wenviron**，因此失效 **_envp**自变量**主要**和 **_wenvp**参数**wmain**。 因此，它是安全使用 **_environ**或 **_wenviron**访问环境信息。 有关关系的详细信息 **_putenv**和 **_wputenv**全局变量，请参阅[_environ、 _wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_Putenv**和 **_getenv**系列的函数不是线程安全。 **_getenv**无法返回字符串指针时 **_putenv**正在修改的字符串，从而导致随机失败。 确保对这些函数的调用同步。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

有关如何使用的示例 **_putenv**，请参阅[getenv、 _wgetenv](getenv-wgetenv.md)。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
