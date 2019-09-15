---
title: _resetstkoflw
ms.date: 11/04/2016
api_name:
- _resetstkoflw
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
- resetstkoflw
- _resetstkoflw
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
ms.openlocfilehash: 55ac25cda5e6c442e96cae025657454747d571d9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949293"
---
# <a name="_resetstkoflw"></a>_resetstkoflw

从堆栈溢出恢复。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>返回值

如果函数成功，则为非零值；如果失败，则为 0。

## <a name="remarks"></a>备注

**_Resetstkoflw**函数从堆栈溢出情况恢复，使程序可以继续，而不会因出现严重异常错误而失败。 如果未调用 **_resetstkoflw**函数，则在前一个异常后不会有任何防护页。 下次发生堆栈溢出时，将不会有任何异常，且进程会在无警告的情况下终止。

如果应用程序中的线程导致 **EXCEPTION_STACK_OVERFLOW** 异常，则该线程的堆栈将处于损坏状态。 这与其他异常（如 **EXCEPTION_ACCESS_VIOLATION** 或 **EXCEPTION_INT_DIVIDE_BY_ZERO**）不同，在那些异常中，堆栈是未损坏的。 首次加载程序时，堆栈将设置为任意的较小的值。 然后，堆栈会根据需要增长以满足线程的需求。 这将通过在当前堆栈的结尾处放置一个带 PAGE_GUARD 访问权的页面来实现。 有关更多信息，请参见[创建保护页](/windows/win32/Memory/creating-guard-pages)。

当代码导致堆栈指针指向此页上的一个地址时，会发生异常，并且系统将执行以下三个操作：

- 移除保护页上的 PAGE_GUARD 保护，以便线程可在内存中读取和写入数据。

- 分配一个新的保护页，新的页位于最后一个保护页的下方。

- 重新运行引发异常的命令。

通过这种方式，系统可以自动增大线程的堆栈大小。 进程中的每个线程都具有最大堆栈大小。 堆栈大小在编译时由 [/STACK（堆栈分配）](../../build/reference/stack-stack-allocations.md)设置，或由项目的 .def 文件中的 [STACKSIZE](../../build/reference/stacksize.md) 语句设置。

当超过最大堆栈大小时，系统将执行以下三个操作：

- 在保护页上移除 PAGE_GUARD 保护，如前所述。

- 尝试在最后一个保护页的下方分配新的保护页。 不过，此操作会因超过了最大堆栈大小而导致失败。

- 引发异常，以便线程可以在异常块中处理它。

请注意，此时堆栈不再具有保护页。 当程序下一次将堆栈增大到堆栈结尾（此处应有一个保护页）时，程序将在堆栈结尾之外写入并导致访问冲突。

调用 **_resetstkoflw** ，以便在发生堆栈溢出异常后恢复时还原保护页。 此函数可从 **__except**块的主体内部或 **__except**块外调用。 但是，对于何时使用该函数有一些限制。 绝不应从以下内容调用 **_resetstkoflw** ：

- 筛选器表达式。

- 筛选器函数。

- 从一个筛选器函数调用的函数。

- **catch** 块。

- **__Finally**块。

在这些点上，堆栈尚未充分展开。

堆栈溢出异常生成为结构化异常，而C++不是异常，因此 **_resetstkoflw**在普通**catch**块中不起作用，因为它不会捕获堆栈溢出异常。 但是，如果使用 [_set_se_translator](set-se-translator.md) 来实现引发 C++ 异常的结构化异常转换器（如第二个示例所示），则堆栈溢出异常会导致可由 C++ catch 块处理的 C++ 异常。

在 C++ catch 块中调用 **_resetstkoflw** 是不安全的，因为这是从通过结构化的异常转换器函数引发的异常到达的。 在这种情况下，不会释放堆栈空间，并且堆栈指针只有在 catch 块之外才会重置，即使已先于 catch 块对任何易损坏的对象调用析构函数。 在释放堆栈空间并且已重置堆栈指针之前，不应调用此函数。 因此，仅在退出 catch 块之后才调用它。 catch 块中应尽可能少地使用堆栈空间，因为在 catch 块自行尝试从上一个堆栈溢出中恢复时出现的堆栈溢出是不可恢复的，并且在 catch 块中的溢出触发其本身由同一个 catch 处理的异常时可能会导致程序停止响应。

在某些情况下，即使在正确的位置（例如，在 **__except** 块中）使用 **_resetstkoflw**，它也会失败。 甚至在展开堆栈后，如果仍未留下足够的堆栈空间来执行 **_resetstkoflw**，而且未写入到堆栈的最后一页，则 **_resetstkoflw** 无法将堆栈的最后一页重置为保护页并且将返回 0（这指示失败）。 因此，此函数的安全用法应包括检查返回值而不是假定可安全使用堆栈。

使用 **/clr**编译应用程序时，结构化异常处理将不会捕获**STATUS_STACK_OVERFLOW**异常（请参阅[/Clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)）。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_resetstkoflw**|\<malloc.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库**所有版本的[CRT 库功能](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>示例

下面的示例演示 **_resetstkoflw**函数的推荐用法。

```C
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

没有程序参数的示例输出：

```Output
loop #1
```

程序停止响应，而不执行进一步的迭代。

具有程序参数：

```Output
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

### <a name="description"></a>描述

下面的示例演示了在将结构化异常转换为C++异常的程序中，建议使用 _resetstkoflw。

### <a name="code"></a>代码

```cpp
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

```Output
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
Stack overflow!
Recovered from stack overflow and allocated 100,000 bytes using _alloca.
```

## <a name="see-also"></a>请参阅

[_alloca](alloca.md)<br/>
