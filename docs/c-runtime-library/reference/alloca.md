---
title: "_alloca | Microsoft Docs"
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
  - "_alloca"
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
  - "_alloca"
  - "alloca"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_alloca 函数"
  - "alloca 函数"
  - "内存分配, 堆栈"
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _alloca
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在堆栈上分配内存。  因为更安全版本可用，此函数已弃用；请参阅 [\_malloca](../../c-runtime-library/reference/malloca.md)。  
  
## 语法  
  
```  
void *_alloca(   
   size_t size   
);  
```  
  
#### 参数  
 \[in\] `size`  
 从堆栈中分配字节。  
  
## 返回值  
 `_alloca` 例程会返回一个 `void` 指针指向已分配的空间，可以确保对于任何类型的对象存储对齐。  如果 `size` 为 0，`_alloca` 将分配长度为零的项，并将有效指针返回到该项中。  
  
 如果无法分配空间，将引发堆栈溢出异常。  堆栈溢出异常不是 C\+\+ 异常，它是个结构化异常。  替换使用 C\+\+ 异常处理程序，必须改用 [结构化异常处理程序](../../cpp/structured-exception-handling-c-cpp.md) （SEH\)。  
  
## 备注  
 `_alloca` 从程序堆栈中分配 `size` 字节。  当调用函数退出时 \(不是当赋值仅超出范围时\)，分配的空间将自动释放。  因此，不要将返回的指针值通过 `_alloca` 作为参数传递到[空闲](../../c-runtime-library/reference/free.md)。  
  
 在异常处理程序中 \(EH\) 显式调用`_alloca` 有局限。  on x86 处理器 EH 例程的类运行在自己的内存运行帧：在这些不基于封闭函数的堆栈指针的当前位置的内存空间执行任务。  最常见的通用实现包括 Windows NT 结构化异常处理程序 \(SEH\) 和 C\+\+ 表达式子句。  因此，在返回调用的EH例程中，在程序失败任意以下的方案结果中显式调用`_alloca`：  
  
-   Windows NT 的 SEH 异常过滤表达式：`__except` \(`_alloca ()` \)  
  
-   Windows NT SEH 最终异常处理程序：`__finally` {}`_alloca ()`  
  
-   C\+\+ EH catch 子句表达式  
  
 但是，`_alloca` 能直接从得到由前面列出的EH方案之一调用的应用程序提供的回调。  
  
> [!IMPORTANT]
>  在 Windows XP 中，如果在 try\/catch 块内部调用 `_alloca`，必须在 catch 块中调用 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)。  
  
 除了上述限制外，当使用 [\/clr \(公共语言运行时编译\)](../../build/reference/clr-common-language-runtime-compilation.md) 选项时，`_alloca` 不能在 `__except` 块中使用。  有关详细信息，请参阅 [\/clr Restrictions](../../build/reference/clr-restrictions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_alloca`|\<malloc.h\>|  
  
## 示例  
  
```  
// crt_alloca.c  
// This program demonstrates the use of  
// _alloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size = 1000;  
    int     errcode = 0;  
    void    *pData = NULL;  
  
    // Note: Do not use try/catch for _alloca,  
    // use __try/__except, since _alloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try {  
        // An unbounded _alloca can easily result in a   
        // stack overflow.  
        // Checking for a size < 1024 bytes is recommended.  
        if (size > 0 && size < 1024)  
        {  
            pData = _alloca( size );  
            printf_s( "Allocated %d bytes of stack at 0x%p",  
                      size, pData);  
        }  
        else  
        {  
            printf_s("Tried to allocate too many bytes.\n");  
        }  
    }  
  
    // If an exception occured with the _alloca function  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_alloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf_s("Could not reset the stack!\n");  
            _exit(1);  
        }  
    };  
}  
```  
  
  **在 0x0012FB50 分配1000 个堆栈字节**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)   
 [\_malloca](../../c-runtime-library/reference/malloca.md)