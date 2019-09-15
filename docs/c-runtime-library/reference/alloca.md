---
title: _alloca
ms.date: 11/04/2016
api_name:
- _alloca
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _alloca
- alloca
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
ms.openlocfilehash: 2212f9e40c78932b63eebfc221ad2f07fa3d3f9d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943701"
---
# <a name="_alloca"></a>_alloca

在堆栈上分配内存。 此函数已弃用，因为更安全的版本可用;请参阅[_malloca](malloca.md)。

## <a name="syntax"></a>语法

```C
void *_alloca(
   size_t size
);
```

### <a name="parameters"></a>参数

*size*<br/>
在堆栈中要分配的字节数。

## <a name="return-value"></a>返回值

**_Alloca**例程返回指向已分配空间的**void**指针，该指针保证能针对任何类型的对象的存储进行适当的调整。 如果*size*为0，则 **_alloca**分配一个长度为零的项，并返回指向该项的有效指针。

如果无法分配空间，将生成堆栈溢出异常。 堆栈溢出异常不是 C++ 异常，它是结构化异常。 必须使用[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md) (SEH)，而使用 C++ 异常处理。

## <a name="remarks"></a>备注

**_alloca**从程序堆栈分配*大小*字节。 释放调用函数时，将自动释放已分配的空间（而不是在分配超出范围时）。 因此，请不要将 **_alloca**返回的指针值作为参数传递给[free](free.md)。

在异常处理程序（EH）中显式调用 **_alloca**存在一些限制。 在 x86 类处理器上运行的 EH 例程在其自己的内存帧中运行：它们在内存空间中执行其任务，这些任务不基于封闭函数的堆栈指针的当前位置。 最常见的实现包括 Windows NT 结构化异常处理 (SEH) 和 C++ catch 子句表达式。 因此，在以下任何一种情况下，显式调用 **_alloca**会导致在返回到调用 EH 例程期间程序失败：

- Windows NT SEH 异常筛选器表达式：`__except ( _alloca() )`

- Windows NT SEH 最终异常处理程序：`__finally { _alloca() }`

- C++ EH catch 子句表达式

但是，可以从 EH 例程内或从应用程序提供的回调中直接调用 **_alloca** ，此回调是前面列出的一个 EH 方案调用的。

> [!IMPORTANT]
> 在 Windows XP 中，如果在 try/catch 块中调用 **_alloca** ，则必须在 catch 块中调用[_resetstkoflw](resetstkoflw.md) 。

除了上述限制之外，在使用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)选项时，不能在 **__except**块中使用 **_alloca** 。 有关详细信息，请参阅 [/clr Restrictions](../../build/reference/clr-restrictions.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_alloca**|\<malloc.h>|

## <a name="example"></a>示例

```C
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

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
[_malloca](malloca.md)<br/>
