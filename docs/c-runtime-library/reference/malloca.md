---
title: "_malloca | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _malloca
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
apitype: DLLExport
f1_keywords:
- malloca
- _malloca
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 70a37640ec7f6024539ad1e2134152190e698133
ms.lasthandoff: 02/24/2017

---
# <a name="malloca"></a>_malloca
在堆栈上分配内存。 这是 [_alloca](../../c-runtime-library/reference/alloca.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
void *_malloca(   
   size_t size   
);  
```  
  
#### <a name="parameters"></a>参数  
 `size`  
 在堆栈中要分配的字节数。  
  
## <a name="return-value"></a>返回值  
 `_malloca` 例程向所分配的空间返回 `void` 指针，且确保其恰好与任意类型的对象存储空间对齐。 如果 `size` 为 0，则 `_malloca` 分配零长度的项并向该项返回有效的指针。  
  
 如果无法分配空间，将生成堆栈溢出异常。 堆栈溢出异常不是 C++ 异常，它是结构化异常。 必须使用[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md) (SEH)，而使用 C++ 异常处理。  
  
## <a name="remarks"></a>备注  
 如果请求超出了 `_ALLOCA_S_THRESHOLD` 指定的特定字节大小，则 `_malloca` 从程序堆栈或堆中分配 `size` 个字节。 `_malloca` 和 `_alloca` 之间的区别在于无论大小如何，`_alloca` 始终在堆上进行分配。 与不要求或不允许调用 `free` 来释放要分配的内存的 `_alloca` 不同，`_malloca` 要求使用 [_freea](../../c-runtime-library/reference/freea.md) 来释放内存。 在调试模式下，`_malloca` 始终从堆中分配内存。  
  
 在异常处理程序 (EH) 中显式调用 `_malloca` 存在一些限制。 在 x86 类处理器上运行的 EH 例程在自己的内存框架中工作：它们在未基于封闭函数堆栈指针当前位置的内存空间中执行其任务。 最常见的实现包括 Windows NT 结构化异常处理 (SEH) 和 C++ catch 子句表达式。 因此，在以下任意方案中显式调用 `_malloca` 会导致在返回至调用 EH 例程时程序失败：  
  
-   Windows NT SEH 异常筛选表达式：`__except` (`_malloca ()` )  
  
-   Windows NT SEH 最终异常处理程序：`__finally` {`_malloca ()` }  
  
-   C++ EH catch 子句表达式  
  
 但是，可以直接从 EH 例程中或从由上面列出的 EH 方案之一调用的应用程序提供的回调中调用 `_malloca`。  
  
> [!IMPORTANT]
>  在 Windows XP 中，如果在 try/catch 块内调用了 `_malloca`，则必须在 catch 块中调用 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)。  
  
 除以上限制外，在使用“[/clr (公共语言运行时编译)](../../build/reference/clr-common-language-runtime-compilation.md)”选项时，不能在 `__except` 块中使用 `_malloca`。 有关详细信息，请参阅 [/clr 限制](../../build/reference/clr-restrictions.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_malloca`|\<malloc.h>|  
  
## <a name="example"></a>示例  
  
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
  
## <a name="example"></a>示例  
  
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
  
## <a name="input"></a>输入  
  
```  
1000  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
Enter the number of bytes to allocate using _malloca: 1000  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)
