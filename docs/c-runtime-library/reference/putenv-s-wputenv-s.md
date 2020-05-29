---
title: _putenv_s、_wputenv_s
ms.date: 4/2/2020
api_name:
- _wputenv_s
- _putenv_s
- _o__putenv_s
- _o__wputenv_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
ms.openlocfilehash: ade4fe613a2fd57df67f58c496b62d7192354654
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918871"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s、_wputenv_s

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
|**Null**|any|**EINVAL**|
|any|**Null**|**EINVAL**|

如果发生某个错误条件，这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回**EINVAL** ，并将**Errno**设置为**EINVAL**。

## <a name="remarks"></a>备注

**_Putenv_s**函数添加了新的环境变量，或修改了现有环境变量的值。 环境变量定义过程执行的环境（例如待与程序链接的库的默认搜索路径）。 **_wputenv_s**是 **_putenv_s**的宽字符版本;**_wputenv_s**的*envstring*参数是宽字符字符串。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname*是要添加或修改的环境变量的名称， *value_string*是变量的值。 如果*varname*已是环境的一部分，则其值将替换为*value_string*;否则，新的*varname*变量及其*value_string*将添加到环境中。 您可以通过为*value_string*指定一个空字符串（即 ""）来从环境中删除变量。

**_putenv_s**和 **_wputenv_s**只会影响当前进程的本地环境;不能使用它们来修改命令级别环境。 这些函数仅对运行库可访问的数据结构执行，而不对操作系统为进程创建的环境“段”运行。 在当前进程终止时，环境将还原到调用进程的级别，它在大多数情况下为操作系统级别。 但是，可以将修改后的环境传递到 **_spawn**、 **_exec**或**系统**创建的任何新进程，这些新进程将获取 **_putenv_s**和 **_wputenv_s**添加的所有新项。

不要直接更改环境条目;请改用 **_putenv_s**或 **_wputenv_s**来更改它。 具体而言，直接释放 **_environ []** 全局数组的元素可能会导致无效内存。

**getenv**和 **_putenv_s**使用全局变量 **_environ**来访问环境表;使用 **_wenviron** **_wgetenv**和 **_wputenv_s** 。 **_putenv_s**和 **_wputenv_s**可能更改 **_environ**和 **_wenviron**的值，从而使 **_wenvp** **main**参数*与* **wmain**参数的值无效。 因此，使用 **_environ**或 **_wenviron**来访问环境信息更安全。 有关 **_putenv_s**和 **_wputenv_s**与全局变量的关系的详细信息，请参阅[_environ，_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_Putenv_s**和 **_getenv_s**系列函数不是线程安全的。 当 **_putenv_s**修改字符串时， **_getenv_s**可能返回字符串指针，从而导致随机失败。 确保对这些函数的调用同步。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

有关演示如何使用 **_putenv_s**的示例，请参阅[getenv_s，_wgetenv_s](getenv-s-wgetenv-s.md)。

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
