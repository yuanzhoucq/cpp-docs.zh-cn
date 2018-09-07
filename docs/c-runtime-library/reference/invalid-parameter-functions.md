---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
apiname:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26e66b6ad47af521bb5188860d7d987e9d3b5f6b
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100829"
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

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

*表达式*<br/>
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

这些函数不返回值。 **_Invalid_parameter_noinfo_noreturn**并 **_invoke_watson**函数不返回给调用方，并在某些情况下， **_invalid_parameter**和 **_invalid_parameter_noinfo**可能不会返回给调用方。

## <a name="remarks"></a>备注

C 运行时库函数传递非有效参数时，库函数会调用一个*无效参数处理程序*，该函数可由程序员指定执行多项操作。 例如，它可能会将问题报告给用户、写入日志、中断调试器、 终止程序，或不执行任何操作。 如果没有函数指定默认处理程序，程序员 **_invoke_watson**，调用。

默认情况下，在调试代码中确定的非有效参数时的 CRT 库函数调用函数 **_invalid_parameter**使用 verbose 参数。 在非调试代码中， **_invalid_parameter_noinfo**调用函数时，它调用 **_invalid_parameter**函数使用空参数。 如果非调试 CRT 库功能要求程序终止 **_invalid_parameter_noinfo_noreturn**调用函数时，它调用 **_invalid_parameter**函数使用空通过调用的参数后, 接 **_invoke_watson**函数来强制终止程序。

**_Invalid_parameter**函数检查是否已设置用户定义的无效参数处理程序，以及如果是这样，调用它。 例如，如果用户定义的线程本地处理程序是通过调用当前线程中的 [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 来设置的，那么在调用时将返回该函数。 另外，如果用户定义的全局无效参数处理程序是置通过调用 [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 来设置的，那么在调用时将返回该函数。 否则为默认处理程序 **_invoke_watson**调用。 默认行为 **_invoke_watson**是终止该程序。 用户定义的处理程序可能会终止或返回。 我们建议用户定义的处理程序终止程序，除非确定认要进行恢复。

当默认处理程序 **_invoke_watson**调用时，如果处理器支持[__fastfail](../../intrinsics/fastfail.md)操作，使用的参数调用**FAST_FAIL_INVALID_ARG**并终止进程。 否则，将引发速快速失败异常，该异常可通过所连接的调试器捕获。 如果允许该进程继续，则将它终止通过调用 Windows **TerminateProcess**函数使用的异常代码状态**STATUS_INVALID_CRUNTIME_PARAMETER**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|------------------|
|**_invalid_parameter**， **_invalid_parameter_noinfo**， **_invalid_parameter_noinfo_noreturn**， **_invoke_watson**|\<corecrt.h 1>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[参数验证](../../c-runtime-library/parameter-validation.md)<br/>
