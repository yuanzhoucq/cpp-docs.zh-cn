---
title: "assert 宏、_assert、_wassert | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "assert"
  - "_assert"
  - "_wassert"
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
  - "assert"
  - "_assert"
  - "_wassert"
  - "assert/_wassert"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "中止程序"
  - "assert 函数"
  - "assert 宏"
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# assert 宏、_assert、_wassert
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算表达式，如果结果为 `false`，则打印诊断消息并中止程序。  
  
## 语法  
  
```  
assert(   
   expression   
);  
void _assert(  
   char const* message,  
   char const* filename,  
   unsigned line  
);  
void _wassert(  
   wchar_t const* message,  
   wchar_t const* filename,  
   unsigned line  
);  
```  
  
#### 参数  
 `expression`  
 计算结果不为零 \(`true`\) 或为零 \(`false`\) 的标量表达式（包括指针表达式）。  
  
 `message`  
 要显示的消息。  
  
 `filename`  
 断言失败的源文件的名称。  
  
 `line`  
 断言失败处所在的源文件行号。  
  
## 备注  
 `assert` 宏通常用于标识程序开发过程中的逻辑错误。 出现意外情况时可用它停止程序执行，方法是实现 `expression` 参数来计算仅当程序操作不正确时的 `false`。 可通过定义宏 `NDEBUG` 在编译时关闭断言检查。 您可以关闭 `assert` 而无需通过修改您的源文件的宏 **\/DNDEBUG** 命令行选项。 可以在包含 \<assert.h\> 之前使用`#define NDEBUG` 指令，以便在源代码中关闭 `assert` 宏。  
  
 `assert` 宏将在 `expression` 计算结果为 `false` \(0\) 时打印诊断消息并调用 [abort](../../c-runtime-library/reference/abort.md) 终止程序执行。 如果 `expression` 为 `true`（非零），则不执行任何操作。 诊断消息包括失败的表达式、源文件的名称以及断言失败的行号。  
  
 诊断消息将用宽字符打印。 因此，它将按预期工作，即使表达式中存在 Unicode 字符也是如此。  
  
 诊断消息的目标取决于调用例程的应用程序的类型。 控制台应用程序始终通过 `stderr` 接收消息。 在基于 Windows 的应用程序中，`assert` 将调用 Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) 函数创建消息框来显示消息以及“确定”按钮。 当用户单击**“确定”**后，程序将立即中止。  
  
 当应用程序与运行库的调试版本链接，`assert` 将创建带三个按钮的消息框：**“中止”**、**“重试”**和**“忽略”**。 如果用户单击**“中止”**，则程序将立即中止。 如果用户单击**“重试”**，则将调用调试器，之后用户可以调试程序，前提是启用了实时 \(JIT\) 调试。 如果用户单击**“忽略”**，则 `assert` 将继续其常规执行：创建带**“确定”**按钮的消息框。 请注意，当存在错误条件时单击**“忽略”**可能导致未定义的行为。  
  
 有关 CRT 调试的详细信息，请参阅[CRT 调试技术](../Topic/CRT%20Debugging%20Techniques.md)。  
  
 `_assert` 和 `_wassert` 函数是内部 CRT 函数。 这两个函数可帮助最大程度地减少在对象文件中支持断言所需的代码。 建议不要直接调用这些函数。  
  
 当未定义 `NDEBUG` 时，C 运行库的发布版本和调试版本中均启用了 `assert` 宏。 当定义了 `NDEBUG` 时，该宏虽然可用，但不会计算其参数，因而并不起作用。 启用后， `assert` 宏会调用 `_wassert` 用于实现。 其他断言宏 [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)、[\_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 和 [\_ASSERT\_EXPR](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 也可用，但它们只有在已定义 [\_DEBUG](../../c-runtime-library/debug.md) 宏的情况下以及存在于与 C 运行时库调试版本关联的代码中时才会计算传递给它们的表达式。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`assert`, `_wassert`|\<assert.h\>|  
  
 `_assert` 函数的签名在头文件中不可用。`_wassert` 函数的签名只有在未定义 `NDEBUG` 宏时才可用。  
  
## 示例  
 在此程序中，`analyze_string` 函数使用 `assert` 宏来测试与字符串和长度相关的一些条件。 如果任意条件失败，则程序将打印指示失败原因的消息。  
  
```  
// crt_assert.c  
// compile by using: cl /W4 crt_assert.c  
#include <stdio.h>  
#include <assert.h>  
#include <string.h>  
  
void analyze_string( char *string );   // Prototype  
  
int main( void )  
{  
   char  test1[] = "abc", *test2 = NULL, test3[] = "";  
  
   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );  
   analyze_string( test1 );  
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );  
   analyze_string( test2 );  
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );  
   analyze_string( test3 );  
}  
  
// Tests a string to see if it is NULL,   
// empty, or longer than 0 characters.  
void analyze_string( char * string )  
{  
   assert( string != NULL );        // Cannot be NULL  
   assert( *string != '\0' );       // Cannot be empty  
   assert( strlen( string ) > 2 );  // Length must exceed 2  
}  
```  
  
 该程序会生成以下输出：  
  
```Output  
Analyzing string 'abc' Analyzing string '(null)' Assertion failed: string != NULL, file crt_assert.c, line 25  
```  
  
 断言失败后，可能会看到一个包含如下内容的消息框（具体取决于操作系统和运行时库的版本）：  
  
```Output  
此问题会导致程序无法正常工作。 Windows 将关闭该程序并通知是否有可用的解决方案。  
```  
  
 如果已安装调试器，请选择“调试”按钮以启动调试器，或选择“关闭程序”以退出。  
  
## .NET Framework 等效项  
 [System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)  
  
## 请参阅  
 [错误处理](../../c-runtime-library/error-handling-crt.md)   
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [raise](../../c-runtime-library/reference/raise.md)   
 [signal](../../c-runtime-library/reference/signal.md)   
 [\_ASSERT、\_ASSERTE、\_ASSERT\_EXPR 宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [\_DEBUG](../../c-runtime-library/debug.md)