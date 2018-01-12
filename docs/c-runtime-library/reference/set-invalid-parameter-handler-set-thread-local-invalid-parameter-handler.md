---
title: "_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 336a2f362ac9a67cb8bb176948fbb7b5c83329a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setinvalidparameterhandler-setthreadlocalinvalidparameterhandler"></a>_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler
设置在 CRT 检测到无效自变量时要调用的函数。  
  
## <a name="syntax"></a>语法  
  
```  
_invalid_parameter_handler _set_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `pNew`  
 指向新的无效参数处理程序的函数指针。  
  
## <a name="return-value"></a>返回值  
 指向调用前的无效参数处理程序的指针。  
  
## <a name="remarks"></a>备注  
 许多 C 运行时函数检查已传递给它们的参数的有效性。 如果传递了无效参数，则此函数可设置 `errno` 错误号或返回错误代码。 在此类情况下，还将调用无效参数处理程序。 C 运行时提供默认的全局无效参数处理程序，该处理程序将终止程序，并显示运行时错误消息。 可以使用 `_set_invalid_parameter_handler` 将自己的函数设置为全局无效参数处理程序。 C 运行时还支持一个线程本地无效参数处理程序。 如果通过使用 `_set_thread_local_invalid_parameter_handler` 在线程中设置了线程本地参数处理程序，则从线程调用的 C 运行时函数使用该处理程序而不使用全局处理程序。 一次只能将一个函数指定为全局无效实参处理程序。 只能将每个线程的一个函数指定为线程本地无效实参处理程序，但不同的线程可以具有不同的线程本地处理程序。 这样，用户可以更改在代码的一个部分中所使用的处理程序，而不影响其他线程的行为。  
  
 当运行时调用无效参数函数时，通常表示发生了不可恢复的错误。 你提供的无效参数处理程序函数应保存自身能够保存的所有数据，然后中止。 它不会将控件返回到主函数，除非您确信此错误是可恢复的。  
  
 无效参数处理程序函数必须具有以下原型：  
  
```  
void _invalid_parameter(  
   const wchar_t * expression,  
   const wchar_t * function,   
   const wchar_t * file,   
   unsigned int line,  
   uintptr_t pReserved  
);  
```  
  
 `expression` 自变量是引发错误的自变量表达式的宽字符串表示形式。 `function` 自变量是已接收无效自变量的 CRT 函数的名称。 `file` 自变量是包含该函数的 CRT 源文件的名称。 `line` 自变量是该文件的行号。 最后一个自变量是保留的。 所有参数都具有值 `NULL`，除非使用 CRT 库的调试版本。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_set_invalid_parameter_handler`, `_set_thread_local_invalid_parameter_handler`|C: \<stdlib.h><br /><br /> C++: \<cstdlib> 或 \<stdlib.h>|  
  
 `_set_invalid_parameter_handler` 和 `_set_thread_local_invalid_parameter_handler` 函数是 Microsoft 的特定函数。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 在下面的示例中，将使用无效参数错误处理程序来打印已接收无效参数和 CRT 源中的文件和行的函数。 当使用调试 CRT 库时，无效参数错误也将引发断言，此示例中已使用 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 禁用断言。  
  
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
 [_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)   
 [CRT 函数的安全增强版本](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)   
 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)