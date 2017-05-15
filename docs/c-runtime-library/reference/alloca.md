---
title: "_alloca |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _alloca
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
- _alloca
- alloca
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 5875a26dc5758674665fba2fde5b51c2ff53420e
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="alloca"></a>_alloca
在堆栈上分配内存。 此函数已弃用，因为一个更安全版本可用;请参阅[_malloca](../../c-runtime-library/reference/malloca.md)。  
  
## <a name="syntax"></a>语法  
  
```  
void *_alloca(   
   size_t size   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `size`  
 在堆栈中要分配的字节数。  
  
## <a name="return-value"></a>返回值  
 `_alloca` 例程向所分配的空间返回 `void` 指针，且确保其恰好与任意类型的对象存储空间对齐。 如果 `size` 为 0，则 `_alloca` 分配零长度的项并向该项返回有效的指针。  
  
 如果无法分配空间，将生成堆栈溢出异常。 堆栈溢出异常不是 C++ 异常，它是结构化异常。 必须使用[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md) (SEH)，而使用 C++ 异常处理。  
  
## <a name="remarks"></a>备注  
 `_alloca`分配`size`从程序堆栈的字节。 在调用函数退出 （而不是在分配只是将传递超出范围） 时，会自动释放分配的空间。 因此，不要将传递返回的指针值`_alloca`的自变量作为[免费](../../c-runtime-library/reference/free.md)。  
  
 在异常处理程序 (EH) 中显式调用 `_alloca` 存在一些限制。 在 x86 类处理器上运行的 EH 例程在自己的内存框架中工作：它们在未基于封闭函数堆栈指针当前位置的内存空间中执行其任务。 最常见的实现包括 Windows NT 结构化异常处理 (SEH) 和 C++ catch 子句表达式。 因此，在以下任意方案中显式调用 `_alloca` 会导致在返回至调用 EH 例程时程序失败：  
  
-   Windows NT SEH 异常筛选表达式：`__except` (`_alloca ()` )  
  
-   Windows NT SEH 最终异常处理程序：`__finally` {`_alloca ()` }  
  
-   C++ EH catch 子句表达式  
  
 但是，可以直接从 EH 例程中或从由上面列出的 EH 方案之一调用的应用程序提供的回调中调用 `_alloca`。  
  
> [!IMPORTANT]
>  在 Windows XP 中，如果在 try/catch 块内调用了 `_alloca`，则必须在 catch 块中调用 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)。  
  
 除了上述限制，当使用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)选项，`_alloca`不能在`__except`块。 有关详细信息，请参阅 [/clr Restrictions](../../build/reference/clr-restrictions.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_alloca`|\<malloc.h>|  
  
## <a name="example"></a>示例  
  
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
  
```Output  
Allocated 1000 bytes of stack at 0x0012FB50  
```  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)   
 [_malloca](../../c-runtime-library/reference/malloca.md)
