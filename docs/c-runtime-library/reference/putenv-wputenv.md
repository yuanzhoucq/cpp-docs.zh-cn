---
title: _putenv、_wputenv
ms.date: 4/2/2020
api_name:
- _putenv
- _wputenv
- _o__putenv
- _o__wputenv
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 3e74959e6c6cdb2e27ce0d68ba40d02d64949904
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333032"
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

如果成功，则返回 0，如果出现错误，则返回 -1。

## <a name="remarks"></a>备注

**_putenv**函数添加新的环境变量或修改现有环境变量的值。 环境变量定义过程执行的环境（例如待与程序链接的库的默认搜索路径）。 **_wputenv**是 **_putenv**的宽字符版本;_wputenv*的串带*参数是 **_wputenv**宽字符字符串。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*envstring*参数必须是指向 value_string 形式*varname*=字符串的*指针，其中* *varname*是要添加或修改的环境变量的名称 *，value_string*是变量的值。 如果*varname*已经是环境的一部分，则其值将被*value_string*替换。否则，新的*varname*变量及其*value_string*值将添加到环境中。 可以通过指定空*value_string*从环境中删除变量，或者换句话说，通过仅指定*varname**来从环境中删除变量。

**_putenv**和 **_wputenv**仅影响当前流程的本地环境;不能使用它们来修改命令级环境。 也就是说，这些函数只在可由运行时库访问的数据结构上操作，并不在操作系统为进程创建的环境段上操作。 在当前进程终止时，环境将还原到调用进程的级别（在大多数情况下，为操作系统级别）。 但是，修改后的环境可以传递给**由_spawn、_exec**或**系统**创建的任何新流程 **_exec**，这些新流程会获得 **_putenv**和 **_wputenv**添加的任何新项目。

不要直接更改环境条目：而是使用 **_putenv**或 **_wputenv**来更改它。 特别是，**直接释放_environ_** 全局数组的元素可能会导致处理无效的内存。

**getenv**和 **_putenv**使用全局变量 **_environ**访问环境表;**_wgetenv**和 **_wputenv**使用 **_wenviron。** **_putenv**和 **_wputenv**可能会改变 **_environ**和 **_wenviron**的值，从而使 **_envp**参数无效为**主**参数 **，_wenvp****参数无效。** 因此，使用 **_environ**或 **_wenviron**访问环境信息更安全。 有关 **_putenv**和 **_wputenv**与全局变量的关系的详细信息，请参阅[_environ，_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **函数的_putenv**和 **_getenv**系列不具有线程安全。 **_getenv**可以在 **_putenv**修改字符串时返回字符串指针，从而导致随机失败。 确保对这些函数的调用同步。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

有关如何使用 **_putenv**的示例，请参阅[getenv，_wgetenv](getenv-wgetenv.md)。

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
