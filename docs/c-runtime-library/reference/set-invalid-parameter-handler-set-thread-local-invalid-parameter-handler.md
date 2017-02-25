---
title: "_set_invalid_parameter_handler _set_thread_local_invalid_parameter_handler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_invalid_parameter_handler"
  - "_set_thread_local_invalid_parameter_handler"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "set_invalid_parameter_handler"
  - "_set_invalid_parameter_handler"
  - "_set_thread_local_invalid_parameter_handler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "无效参数处理程序"
  - "set_invalid_parameter_handler 函数"
  - "_set_invalid_parameter_handler 函数"
  - "_set_thread_local_invalid_parameter_handler 函数"
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _set_invalid_parameter_handler _set_thread_local_invalid_parameter_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置在 CRT 检测到无效自变量时要调用的函数。  
  
## 语法  
  
```  
_invalid_parameter_handler _set_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
```  
  
#### 参数  
 \[in\] `pNew`  
 指向新的无效参数处理程序的函数指针。  
  
## 返回值  
 指向调用前的无效参数处理程序的指针。  
  
## 备注  
 许多 C 运行时函数检查的参数传递给它们的有效性。 如果传递了无效参数，则此函数可设置 `errno` 错误号或返回错误代码。 在此类情况下，还将调用无效参数处理程序。 C 运行时提供的默认全局无效参数处理程序将终止程序，并显示运行时错误消息。 您可以使用 `_set_invalid_parameter_handler` 若要将您自己的函数设置的全局无效参数处理程序。 C 运行库还支持一个线程本地无效参数处理程序。 如果线程本地参数处理程序设置在一个线程中使用 `_set_thread_local_invalid_parameter_handler`, ，从线程中调用 C 运行库函数使用该处理程序而不是全局的处理程序。 只能将一个函数可以指定为全局的无效参数处理程序中，一次中。 只能将一个函数可以指定为每个线程，该线程本地无效参数处理程序，但不同的线程可以具有不同的线程本地处理程序。 这样，您可以更改您的代码的一个部分中使用而不会影响其他线程的行为的处理程序。  
  
 当运行时调用无效参数函数时，它通常表示发生了不可恢复的错误。 您提供的无效参数处理程序函数应将保存所有数据，它可以然后中止。 它不会将控件返回到主函数，除非您确信此错误是可恢复的。  
  
 无效参数处理程序函数必须具有以下原型：  
  
```c  
void _invalid_parameter(  
   const wchar_t * expression,  
   const wchar_t * function,   
   const wchar_t * file,   
   unsigned int line,  
   uintptr_t pReserved  
);  
```  
  
 `expression` 参数是宽字符串表示形式引发了错误的参数表达式。`function` 参数是已接收无效参数的 CRT 函数的名称。`file` 参数是 CRT 源文件包含该函数的名称。`line` 参数是该文件中的行号。 最后一个自变量是保留的。 所有参数都具有值 `NULL`，除非使用 CRT 库的调试版本。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_set_invalid_parameter_handler`, `_set_thread_local_invalid_parameter_handler`|C: \< stdlib.h \><br /><br /> C \+ \+: \< cstdlib \> 或 \< stdlib.h \>|  
  
 `_set_invalid_parameter_handler` 和 `_set_thread_local_invalid_parameter_handler` 函数是 Microsoft 专用。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 在下面的示例中，将使用无效参数错误处理程序来打印已接收无效参数和 CRT 源中的文件和行的函数。 当使用调试 CRT 库时，无效参数错误也会引发一个断言，在此示例使用中禁用 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md)。  
  
```c  
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
在函数 common_vfprintf 中检测到的参数无效。 文件︰ minkernel\crts\ucrt\src\appcrt\stdio\output.cpp 行︰ 32 表达式︰ 格式 ！ = nullptr  
```  
  
## 请参阅  
 [\_get\_invalid\_parameter\_handler \_get\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)   
 [CRT 函数的安全增强版本](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)