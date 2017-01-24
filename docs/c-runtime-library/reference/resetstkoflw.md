---
title: "_resetstkoflw | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_resetstkoflw"
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
apitype: "DLLExport"
f1_keywords: 
  - "resetstkoflw"
  - "_resetstkoflw"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_resetstkoflw 函数"
  - "resetstkoflw 函数"
  - "堆栈溢出"
  - "堆栈, 恢复"
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _resetstkoflw
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从堆栈溢出还原。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
  
int _resetstkoflw ( void );  
  
```  
  
## 返回值  
 函数成功为非零，失败为零。  
  
## 备注  
 `_resetstkoflw` 函数可以将系统从堆栈溢出的情况恢复为正常，从而使程序得以继续运行，而不会由于出现异常错误而失败。  如果未调用 `_resetstkoflw` 函数，则在上一个异常后不会显示保护页。  当下次发生堆栈溢出时，根本不会显示异常，进程将在没有任何警告的情况下终止。  
  
 如果应用程序中的线程导致 **EXCEPTION\_STACK\_OVERFLOW** 异常，该线程使他的栈处于危险状态。  与其他异常相反的是例如 **EXCEPTION\_ACCESS\_VIOLATION** 或 **EXCEPTION\_INT\_DIVIDE\_BY\_ZERO**，这些栈不会被破坏。  当程序首先加载时，堆栈设置为一个非常小的值。  堆栈然后增大在需要时调整线程的需要。  这是通过在当前栈的结尾放置一个PAGE\_GUARD 页面来实现的。  有关更多信息，请参见[创建安全页](http://msdn.microsoft.com/library/windows/desktop/aa366549)。  
  
 当代码导致堆栈指针指向本页中的一个地址，则会发生异常，并且该系统进行以下三个操作：  
  
-   移除在显示保护页的 PAGE\_GUARD 保护，以便线程可以读取和写入数据到内存中。  
  
-   定位在一页的最后面分配一个新的保护页。  
  
-   重新运行引发异常的命令。  
  
 这样，系统会为线程自动增加堆栈大小。  进程中的每个线程都具有最大堆栈大小。  堆栈大小设置在生成时 [\/STACK（堆栈分配）](../../build/reference/stack-stack-allocations.md)，或者跟项目的 .def 文件中 [STACKSIZE](../../build/reference/stacksize.md) 报表中。  
  
 当超过最大堆栈大小时，系统将进行以下三个操作：  
  
-   在安全也移除PAGE\_GUARD保护，如先前所描述的。  
  
-   尝试在最后一个页下分配新显示保护页。  然而，由于超过了栈的最大范围，所以会失败。  
  
-   引发异常，以便线程可以在异常块中处理它。  
  
 请注意，在这个店，堆栈再也没有保护页。  下次程序始终增大堆栈的末尾，应具有显示保护页、程序编写在堆栈尾以外的和导致访问冲突。  
  
 调用 `_resetstkoflw` 还原保护页，只要以堆栈溢出异常后完成。  此功能可从 `__except` 的主体内调用块或 **\_\_except** 块的外部。  但是，应用时有一些限制。  `_resetstkoflw`从来不会从以下调用：  
  
-   筛选器表达式。  
  
-   筛选函数。  
  
-   从筛选器函数调用的函数。  
  
-   **catch** 块。  
  
-   `__finally` 块。  
  
 在这些点，堆栈完全不会展开。  
  
 堆栈溢出异常生成，因为结构化异常，而不是 C\+\+ 异常，因此，`_resetstkoflw` 没有用在普通的 **捕获** 块，因为它将不捕获溢出异常。  然而，如果 [\_set\_se\_translator](../../c-runtime-library/reference/set-se-translator.md) 用于实现 C\+\+ 引发一个异常的结构化异常转换器 \(在第二个示例中所示\)，堆栈溢出异常会导致可以由 c. c\+\+ catch 处理块的 c. c\+\+ 异常。  
  
 调用从结构化异常转换器函数引发的异常达到 c. c\+\+ 捕获的 **\_resetstkoflw** 块是不安全的。  在这种情况下，堆栈空间不会释放，并且堆栈指针没有在执行 catch 块外将重置，直到块，因此，即使析构函数为所有可损坏的对象调用，在 catch 块之前。  不应调用此函数，直到堆栈空间被释放，并重置堆栈指针。  因此，应在退出 catch 块之后调用它将阻止。  为可能的 ACE 堆栈空间应使用 catch 块，因为在自身发生尝试从前面的堆栈溢出还原 catch 的堆栈溢出块不可退回的，并且可能导致程序停止响应，在执行 catch 块中的溢出块触发器本身由同一 catch 处理块的异常。  
  
 具有 **\_resetstkoflw** 在正确的位置可能失败的情况，即使使用，如 **\_\_except** 块。  如果为，则在展开堆栈后，仍不留下的足够的堆栈空间执行 **\_resetstkoflw** 不写入堆栈的最后一页，**\_resetstkoflw** 无法重新设置堆栈的最后一页，因为显示保护页并返回 0，指示失败。  因此，此功能安全的用法应包括检查返回值而不是假定。  
  
 结构化异常处理将不捕获 `STATUS_STACK_OVERFLOW` 异常，则应用程序编译 `/clr` 或 `/clr:pure` \(请参见 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)\)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_resetstkoflw`|\<malloc.h\>|  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
 **Libraries:** 的所有版本 [CRT 库功能](../../c-runtime-library/crt-library-features.md).  
  
## 示例  
 下面的示例演示`_resetstkoflw`函数的推荐用法。  
  
```  
// crt_resetstkoflw.c  
// Launch program with and without arguments to observe  
// the difference made by calling _resetstkoflw.  
  
#include <malloc.h>  
#include <stdio.h>  
#include <windows.h>  
  
void recursive(int recurse)  
{  
   _alloca(2000);  
   if (recurse)  
      recursive(recurse);  
}  
  
// Filter for the stack overflow exception.  
// This function traps the stack overflow exception, but passes  
// all other exceptions through.   
int stack_overflow_exception_filter(int exception_code)  
{  
   if (exception_code == EXCEPTION_STACK_OVERFLOW)  
   {  
       // Do not call _resetstkoflw here, because  
       // at this point, the stack is not yet unwound.  
       // Instead, signal that the handler (the __except block)  
       // is to be executed.  
       return EXCEPTION_EXECUTE_HANDLER;  
   }  
   else  
       return EXCEPTION_CONTINUE_SEARCH;  
}  
  
int main(int ac)  
{  
   int i = 0;  
   int recurse = 1, result = 0;  
  
   for (i = 0 ; i < 10 ; i++)  
   {  
      printf("loop #%d\n", i + 1);  
      __try  
      {  
         recursive(recurse);  
  
      }  
  
      __except(stack_overflow_exception_filter(GetExceptionCode()))  
      {  
         // Here, it is safe to reset the stack.  
  
         if (ac >= 2)  
         {  
            puts("resetting stack overflow");  
            result = _resetstkoflw();  
         }  
      }  
  
      // Terminate if _resetstkoflw failed (returned 0)  
      if (!result)  
         return 3;  
   }  
  
   return 0;  
}  
```  
  
## 示例输出  
 没有程序参数：  
  
```  
loop #1  
```  
  
 程序停止响应，而无需执行进一步迭代。  
  
 包含程序参数：  
  
```  
loop #1  
resetting stack overflow  
loop #2  
resetting stack overflow  
loop #3  
resetting stack overflow  
loop #4  
resetting stack overflow  
loop #5  
resetting stack overflow  
loop #6  
resetting stack overflow  
loop #7  
resetting stack overflow  
loop #8  
resetting stack overflow  
loop #9  
resetting stack overflow  
loop #10  
resetting stack overflow  
```  
  
### 描述  
 下面的示例在结构化异常转换为 C\+\+ 异常的程序显示给 `_resetstkoflw` 的推荐使用。  
  
### 代码  
  
```  
// crt_resetstkoflw2.cpp  
// compile with: /EHa  
// _set_se_translator requires the use of /EHa  
#include <malloc.h>  
#include <stdio.h>  
#include <windows.h>  
#include <eh.h>  
  
class Exception { };  
  
class StackOverflowException : Exception { };  
  
// Because the overflow is deliberate, disable the warning that  
// this function will cause a stack overflow.  
#pragma warning (disable: 4717)  
void CauseStackOverflow (int i)  
{  
        // Overflow the stack by allocating a large stack-based array  
        // in a recursive function.  
        int a[10000];  
        printf("%d ", i);  
        CauseStackOverflow (i + 1);  
}  
  
void __cdecl SEHTranslator (unsigned int code, _EXCEPTION_POINTERS*)  
{  
   // For stack overflow exceptions, throw our own C++   
   // exception object.  
   // For all other exceptions, throw a generic exception object.  
   // Use minimal stack space in this function.  
   // Do not call _resetstkoflw in this function.  
  
   if (code == EXCEPTION_STACK_OVERFLOW)  
      throw StackOverflowException ( );  
   else  
      throw Exception( );  
}  
  
int main ( )  
{  
        bool stack_reset = false;  
        bool result = false;  
  
        // Set up a function to handle all structured exceptions,  
        // including stack overflow exceptions.  
        _set_se_translator (SEHTranslator);  
  
        try  
        {  
            CauseStackOverflow (0);  
        }  
        catch (StackOverflowException except)  
        {  
                // Use minimal stack space here.  
                // Do not call _resetstkoflw here.  
                printf("\nStack overflow!\n");  
                stack_reset = true;  
        }  
        catch (Exception except)  
        {  
                // Do not call _resetstkoflw here.  
                printf("\nUnknown Exception!\n");  
        }  
        if (stack_reset)  
        {  
          result = _resetstkoflw();  
          // If stack reset failed, terminate the application.  
          if (result == 0)  
             exit(1);  
        }  
  
        void* pv = _alloca(100000);  
        printf("Recovered from stack overflow and allocated 100,000 bytes"  
               " using _alloca.");  
  
   return 0;  
}  
```  
  
## 示例输出  
  
```  
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24  
Stack overflow!  
Recovered from stack overflow and allocated 100,000 bytes using _alloca.  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_alloca](../../c-runtime-library/reference/alloca.md)