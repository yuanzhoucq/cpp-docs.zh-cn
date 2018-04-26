---
title: _putenv_s、_wputenv_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wputenv_s
- _putenv_s
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
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
dev_langs:
- C++
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b1baab00d535581f753e512797308cecbc10373
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="putenvs-wputenvs"></a>_putenv_s、_wputenv_s

创建、修改或删除环境变量。 这些是安全性增强的 [_putenv、_wputenv](putenv-wputenv.md) 版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
errno_t _putenv_s(
   const char *varname,
   const char *value_string
);
errno_t _wputenv_s(
   const wchar_t *varname,
   const wchar_t *value_string
);
```

### <a name="parameters"></a>参数

*varname*<br/>
环境变量名称。

*value_string*<br/>
要将环境变量设置为的值。

## <a name="return-value"></a>返回值

如果成功，则返回 0；否则，返回错误代码。

### <a name="error-conditions"></a>错误条件

|*varname*|*value_string*|返回值|
|------------|-------------|------------------|
|**NULL**|任何|**EINVAL**|
|任何|**NULL**|**EINVAL**|

如果发生某个错误条件，这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回**EINVAL**并设置**errno**到**EINVAL**。

## <a name="remarks"></a>备注

**_Putenv_s**函数将新环境变量添加或修改现有环境变量的值。 环境变量定义过程执行的环境（例如待与程序链接的库的默认搜索路径）。 **_wputenv_s**是宽字符版本的 **_putenv_s**; *envstring*参数 **_wputenv_s**是宽字符字符串。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname*是要添加或修改的环境变量的名称和*value_string*是变量的值。 如果*varname*已属于该环境，其值将由替换*value_string*; 否则为新*varname*变量并将其*value_string*添加到环境。 可以从环境中删除变量通过指定一个空字符串 (即，"") 为*value_string*。

**_putenv_s**和 **_wputenv_s**影响本地到当前进程环境; 不能用于修改命令级别环境。 这些函数仅对运行库可访问的数据结构执行，而不对操作系统为进程创建的环境“段”运行。 在当前进程终止时，环境将还原到调用进程的级别，它在大多数情况下为操作系统级别。 但是，修改后的环境可以传递给任何新进程，由 **_spawn**， **_exec**，或**系统**，这些新进程将获取任何新项通过添加 **_putenv_s**和 **_wputenv_s**。

不要直接; 更改环境条目请改用 **_putenv_s**或 **_wputenv_s**若要更改它。 具体而言，直接释放的元素 **_environ []** 全局数组可能会导致无效内存寻址。

**getenv**和 **_putenv_s**使用全局变量 **_environ**访问环境表;**_wgetenv**和 **_wputenv_s**使用 **_wenviron**。 **_putenv_s**和 **_wputenv_s**也可能更改的值 **_environ**和 **_wenviron**，从而使*envp*参数**主要**和 **_wenvp**参数**wmain**。 因此，它是安全使用 **_environ**或 **_wenviron**访问环境信息。 有关详细信息的关系的 **_putenv_s**和 **_wputenv_s**全局变量，请参阅[_environ、 _wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_Putenv_s**和 **_getenv_s**系列的函数不是线程安全。 **_getenv_s**无法返回字符串指针时 **_putenv_s**是修改该字符串，从而导致随机失败。 确保对这些函数的调用同步。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

有关示例，演示如何使用 **_putenv_s**，请参阅[getenv_s、 _wgetenv_s](getenv-s-wgetenv-s.md)。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
