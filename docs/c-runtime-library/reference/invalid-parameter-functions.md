---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 4/2/2020
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
- _o__invalid_parameter_noinfo
- _o__invalid_parameter_noinfo_noreturn
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
ms.openlocfilehash: 0f0a3ea3e1f2e43d53650b4017905c696269ce20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343946"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

C 运行时库使用这些函数来处理传递给 CRT 库函数的非有效参数。 代码也可能会使用这些函数来支持对非有效参数进行默认或自定义处理。

## <a name="syntax"></a>语法

```C
extern "C" void __cdecl
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);

extern "C" void __cdecl
_invalid_parameter_noinfo(void);

extern "C" __declspec(noreturn) void __cdecl
_invalid_parameter_noinfo_noreturn(void);

extern "C" __declspec(noreturn) void __cdecl
_invoke_watson(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## <a name="parameters"></a>参数

*expression*<br/>
一个表示源代码参数表达式无效的字符串。

*function_name*<br/>
调用该处理程序的函数名称。

*file_name*<br/>
在其中调用处理程序的源代码文件。

*line_number*<br/>
在其中调用处理程序的源代码中的行号。

*保留*<br/>
未使用。

## <a name="return-value"></a>返回值

这些函数不返回值。 **_invalid_parameter_noinfo_noreturn**和 **_invoke_watson**函数不返回到调用方，在某些情况下 **，_invalid_parameter**和 **_invalid_parameter_noinfo**可能无法返回到调用方。

## <a name="remarks"></a>备注

C 运行时库函数传递非有效参数时，库函数会调用一个*无效参数处理程序*，该函数可由程序员指定执行多项操作。 例如，它可能会将问题报告给用户、写入日志、中断调试器、 终止程序，或不执行任何操作。 如果程序员未指定任何函数，则调用默认处理程序 **_invoke_watson**。

默认情况下，当在调试代码中标识无效参数时，CRT 库函数使用详细参数调用函数 **_invalid_parameter。** 在非调试代码中，调用 **_invalid_parameter_noinfo**函数，该函数使用空参数调用 **_invalid_parameter**函数。 如果非调试 CRT 库函数需要程序终止，则调用 **_invalid_parameter_noinfo_noreturn**函数，该函数使用空参数调用 **_invalid_parameter**函数，然后调用 **_invoke_watson**函数以强制程序终止。

**_invalid_parameter**函数检查是否已设置用户定义的无效参数处理程序，如果是，则调用它。 例如，如果用户定义的线程本地处理程序是通过调用当前线程中的 [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 来设置的，那么在调用时将返回该函数。 另外，如果用户定义的全局无效参数处理程序是置通过调用 [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 来设置的，那么在调用时将返回该函数。 否则，将调用默认处理程序 **_invoke_watson。** **_invoke_watson**的默认行为是终止程序。 用户定义的处理程序可能会终止或返回。 我们建议用户定义的处理程序终止程序，除非确定认要进行恢复。

当调用默认处理程序 **_invoke_watson**时，如果处理器支持[__fastfail](../../intrinsics/fastfail.md)操作，则使用**FAST_FAIL_INVALID_ARG**参数调用该处理程序，并且进程将终止。 否则，将引发速快速失败异常，该异常可通过所连接的调试器捕获。 如果允许进程继续，则使用**STATUS_INVALID_CRUNTIME_PARAMETER**的异常代码状态调用 Windows**终止进程**函数将终止该进程。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|------------------|
|**_invalid_parameter，** **_invalid_parameter_noinfo**， **_invalid_parameter_noinfo_noreturn**， **_invoke_watson**|\<corecrt.h 1>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[参数验证](../../c-runtime-library/parameter-validation.md)<br/>
