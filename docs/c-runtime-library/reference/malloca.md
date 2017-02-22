---
title: "_malloca | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_malloca"
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
  - "malloca"
  - "_malloca"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_malloca 函数"
  - "malloca 函数"
  - "内存分配, 堆栈"
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _malloca
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在堆栈上分配内存。  [\_alloca](../../c-runtime-library/reference/alloca.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
void *_malloca(   
   size_t size   
);  
```  
  
#### 参数  
 `size`  
 从堆栈中分配字节。  
  
## 返回值  
 `_malloca` 例程会返回一个 `void` 指针指向已分配的空间，可以确保对于任何类型的对象存储对齐。  如果 `size` 为 0，`_malloca` 将分配长度为零的项，并将有效指针返回到该项中。  
  
 如果无法分配空间，将引发堆栈溢出异常。  堆栈溢出异常不是 C\+\+ 异常，它是个结构化异常。  替换使用 C\+\+ 异常处理程序，必须改用 [结构化异常处理程序](../../cpp/structured-exception-handling-c-cpp.md) （SEH\)。  
  
## 备注  
 如果请求在 `_ALLOCA_S_THRESHOLD`中，为的字节超过特定大`_malloca` 将从程序堆栈或堆的 `size` 字节。  在 `_malloca` 和 `_alloca` 之间的差异在于 `_alloca` 在堆栈始终分配，而不管，范围。  与 `_alloca`不同，不需要同时不允许对 `free` 释放。分配的内存，`_malloca` 需要使用 [\_freea](../../c-runtime-library/reference/freea.md) 释放内存。  在调试模式下，`_malloca` 始终分配堆中的内存。  
  
 在异常处理程序中 \(EH\) 显式调用`_malloca` 有局限。  on x86 处理器 EH 例程的类运行在自己的内存运行帧：在这些不基于封闭函数的堆栈指针的当前位置的内存空间执行任务。  最常见的通用实现包括 Windows NT 结构化异常处理程序 \(SEH\) 和 C\+\+ 表达式子句。  因此，在返回调用的EH例程中，在程序失败任意以下的方案结果中显式调用`_malloca`：  
  
-   Windows NT 的 SEH 异常过滤表达式：`__except`  \(`_malloca ()` \)  
  
-   Windows NT SEH 最终异常处理程序：`__finally` {}`_malloca ()`  
  
-   C\+\+ EH catch 子句表达式  
  
 但是，`_malloca` 能直接从得到由前面列出的EH方案之一调用的应用程序提供的回调。  
  
> [!IMPORTANT]
>  在 Windows XP 中，如果在 try\/catch 块内部调用 `_malloca`，必须在 catch 块中调用 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)。  
  
 除了上述限制外，当使用 [\/clr \(公共语言运行时编译\)](../../build/reference/clr-common-language-runtime-compilation.md) 选项时，`_malloca` 不能在 `__except` 块中使用。  有关详细信息，请参阅 [\/clr Restrictions](../../build/reference/clr-restrictions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_malloca`|\<malloc.h\>|  
  
## 示例  
  
```  
// crt_malloca_simple.c  
#include <stdio.h>  
#include <malloc.h>  
  
void Fn()  
{  
   char * buf = (char *)_malloca( 100 );  
   // do something with buf  
   _freea( buf );  
}  
  
int main()  
{  
   Fn();  
}  
```  
  
## 示例  
  
```  
// crt_malloca_exception.c  
// This program demonstrates the use of  
// _malloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size;  
    int     numberRead = 0;  
    int     errcode = 0;  
    void    *p = NULL;  
    void    *pMarker = NULL;  
  
    while (numberRead == 0)  
    {  
        printf_s("Enter the number of bytes to allocate "  
                 "using _malloca: ");  
        numberRead = scanf_s("%d", &size);  
    }  
  
    // Do not use try/catch for _malloca,  
    // use __try/__except, since _malloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try  
    {  
        if (size > 0)  
        {  
            p =  _malloca( size );  
        }  
        else  
        {  
            printf_s("Size must be a positive number.");  
        }  
        _freea( p );  
    }  
  
    // Catch any exceptions that may occur.  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_malloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf("Could not reset the stack!");  
            _exit(1);  
        }  
    };  
}  
```  
  
## 输入  
  
```  
1000  
```  
  
## 示例输出  
  
```  
Enter the number of bytes to allocate using _malloca: 1000  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)