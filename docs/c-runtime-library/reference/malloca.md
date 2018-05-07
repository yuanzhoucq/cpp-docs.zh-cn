---
title: _malloca | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c6f6b731bce5667ca992e7181518bf0a9eb2b87
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="malloca"></a>_malloca

在堆栈上分配内存。 这是 [_alloca](alloca.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>参数

*size*<br/>
在堆栈中要分配的字节数。

## <a name="return-value"></a>返回值

**_Malloca**例程返回**void**到分配的空间，这可保证适当对齐任何类型的对象的存储的指针。 如果*大小*为 0， **_malloca**分配零长度项并将有效指针返回到该项目。

如果无法分配空间，将生成堆栈溢出异常。 堆栈溢出异常不是 C++ 异常，它是结构化异常。 必须使用[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md) (SEH)，而使用 C++ 异常处理。

## <a name="remarks"></a>备注

**_malloca**分配*大小*从程序堆栈或堆如果请求超过某个大小以字节为单位由给定字节 **_ALLOCA_S_THRESHOLD**。 之间的差异 **_malloca**和 **_alloca**在于 **_alloca**始终分配在堆栈上，而不考虑大小。 与不同 **_alloca**，这并不要求或允许对的调用**免费**可释放的内存，因此分配， **_malloca**需要使用[_freea](freea.md)来释放内存。 在调试模式下， **_malloca**始终从堆中分配内存。

没有与显式调用限制 **_malloca**的异常处理 (EH) 中。 在 x86 类处理器上运行的 EH 例程在自己的内存框架中工作：它们在未基于封闭函数堆栈指针当前位置的内存空间中执行其任务。 最常见的实现包括 Windows NT 结构化异常处理 (SEH) 和 C++ catch 子句表达式。 因此，显式调用 **_malloca**任何以下的方案将导致程序故障期间返回给调用 EH 例程中：

- Windows NT SEH 异常筛选器表达式： **__except** (`_malloca ()` )

- Windows NT SEH 最终异常处理程序： **__finally** {`_malloca ()` }

- C++ EH catch 子句表达式

但是， **_malloca**可以直接从调用 EH 例程中或从调用应用程序提供的回调之前列出的 EH 方案之一。

> [!IMPORTANT]
> 在 Windows XP 中，如果 **_malloca**调用在 try/catch 块中，必须调用[_resetstkoflw](resetstkoflw.md) catch 块中。

除了上述限制，当使用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)选项， **_malloca**不能在 **__except**块。 有关详细信息，请参阅 [/clr Restrictions](../../build/reference/clr-restrictions.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_malloca**|\<malloc.h>|

## <a name="example"></a>示例

```C
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

```C
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

### <a name="input"></a>输入

```Input
1000
```

### <a name="sample-output"></a>示例输出

```Output
Enter the number of bytes to allocate using _malloca: 1000
```

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
