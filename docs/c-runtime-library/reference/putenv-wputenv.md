---
title: _putenv、_wputenv
ms.date: 11/04/2016
api_name:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
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
ms.openlocfilehash: 8fe699a476ea1dd09a6ce9922294bce398df16b2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949886"
---
# <a name="_putenv-_wputenv"></a>_putenv、_wputenv

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

如果成功，则返回 0; 如果出现错误，则返回-1。

## <a name="remarks"></a>备注

**_Putenv**函数添加了新的环境变量，或修改了现有环境变量的值。 环境变量定义过程执行的环境（例如待与程序链接的库的默认搜索路径）。 **_wputenv**是 **_putenv**的宽字符版本; **_wputenv**的*envstring*参数是宽字符字符串。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring*参数必须是指向*varname*=*value_string*形式的字符串的指针，其中*varname*是要添加或修改的环境变量的名称， *value_string*是变量的负值. 如果*varname*已是环境的一部分，则其值将替换为*value_string*;否则，新的*varname*变量及其*value_string*值将添加到环境中。 您可以通过指定一个空的*value_string*，或通过仅指定*varname*= 从环境中删除变量。

**_putenv**和 **_wputenv**仅影响当前进程的本地环境;不能使用它们来修改命令级别环境。 也就是说，这些函数只在可由运行时库访问的数据结构上操作，并不在操作系统为进程创建的环境段上操作。 在当前进程终止时，环境将还原到调用进程的级别（在大多数情况下，为操作系统级别）。 但是，可以将修改后的环境传递到 **_spawn**、 **_exec**或**系统**创建的任何新进程，这些新进程将获取 **_putenv**和 **_wputenv**添加的任何新项。

不要直接更改环境条目：改为使用 **_putenv**或 **_wputenv**对其进行更改。 具体而言，直接释放 **_environ []** 全局数组的元素可能会导致无效的内存被寻址。

**getenv**和 **_putenv**使用全局变量 **_environ**访问环境表; **_wgetenv**和 **_wputenv**使用 **_wenviron**。 **_putenv**和 **_wputenv**可能会更改 **_environ**和 **_wenviron**的值，从而使 **_envp**参数失效，**并使**_wenvp**参数失效**。 因此，使用 **_environ**或 **_wenviron**来访问环境信息更安全。 有关 **_putenv**和 **_wputenv**与全局变量的关系的详细信息，请参阅[_environ，_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_Putenv**和 **_getenv**系列的函数不是线程安全的。 当 **_putenv**正在修改字符串时， **_getenv**可能会返回字符串指针，从而导致随机失败。 确保对这些函数的调用同步。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

有关如何使用 **_putenv**的示例，请参阅[getenv、_wgetenv](getenv-wgetenv.md)。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
