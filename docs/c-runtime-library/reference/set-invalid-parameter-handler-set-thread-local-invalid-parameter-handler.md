---
title: _set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_invalid_parameter_handler
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
dev_langs:
- C++
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4808367c94ec6c869c7f3bcafd2965a317553a6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="setinvalidparameterhandler-setthreadlocalinvalidparameterhandler"></a>_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler

设置在 CRT 检测到无效自变量时要调用的函数。

## <a name="syntax"></a>语法

```C
_invalid_parameter_handler _set_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
```

### <a name="parameters"></a>参数

*pNew*<br/>
指向新的无效参数处理程序的函数指针。

## <a name="return-value"></a>返回值

指向调用前的无效参数处理程序的指针。

## <a name="remarks"></a>备注

许多 C 运行时函数检查已传递给它们的参数的有效性。 如果传递了无效自变量，则此函数可设置**errno**错误号或返回错误代码。 在此类情况下，还将调用无效参数处理程序。 C 运行时提供默认的全局无效参数处理程序，该处理程序将终止程序，并显示运行时错误消息。 你可以使用 **_set_invalid_parameter_handler**将自己的函数设置为全局无效参数处理程序。 C 运行时还支持一个线程本地无效参数处理程序。 如果线程本地的参数处理程序设置在线程中使用 **_set_thread_local_invalid_parameter_handler**，从的线程调用 C 运行时函数而不是全局的处理程序使用该处理程序。 一次只能将一个函数指定为全局无效实参处理程序。 只能将每个线程的一个函数指定为线程本地无效实参处理程序，但不同的线程可以具有不同的线程本地处理程序。 这样，用户可以更改在代码的一个部分中所使用的处理程序，而不影响其他线程的行为。

当运行时调用无效参数函数时，通常表示发生了不可恢复的错误。 你提供的无效参数处理程序函数应保存自身能够保存的所有数据，然后中止。 它不会将控件返回到主函数，除非您确信此错误是可恢复的。

无效参数处理程序函数必须具有以下原型：

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

*表达式*自变量是宽字符串表示形式自变量表达式引发错误。 *函数*参数是已接收无效自变量的 CRT 函数的名称。 *文件*自变量是 CRT 源文件包含的函数的名称。 *行*自变量是在该文件中的行号。 最后一个自变量是保留的。 所有参数都具有值**NULL**除非使用 CRT 库的调试版本。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_set_invalid_parameter_handler**， **_set_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib> 或 \<stdlib.h>|

**_Set_invalid_parameter_handler**和 **_set_thread_local_invalid_parameter_handler**函数是 Microsoft 特定。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

在下面的示例中，将使用无效参数错误处理程序来打印已接收无效参数和 CRT 源中的文件和行的函数。 当使用调试 CRT 库时，无效参数错误也将引发断言，此示例中已使用 [_CrtSetReportMode](crtsetreportmode.md) 禁用断言。

```C
// crt_set_invalid_parameter_handler.c
// compile with: /Zi /MTd
#include <stdio.h>
#include <stdlib.h>
#include <crtdbg.h>  // For _CrtSetReportMode

void myInvalidParameterHandler(const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf(L"Invalid parameter detected in function %s."
            L" File: %s Line: %d\n", function, file, line);
   wprintf(L"Expression: %s\n", expression);
   abort();
}

int main( )
{
   char* formatString;

   _invalid_parameter_handler oldHandler, newHandler;
   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);

   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   // Call printf_s with invalid parameters.

   formatString = NULL;
   printf(formatString);
}
```

```Output
Invalid parameter detected in function common_vfprintf. File: minkernel\crts\ucrt\src\appcrt\stdio\output.cpp Line: 32
Expression: format != nullptr
```

## <a name="see-also"></a>请参阅

[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[CRT 函数的安全增强版本](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
