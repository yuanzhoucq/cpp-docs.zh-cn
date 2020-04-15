---
title: _set_new_handler
ms.date: 4/2/2020
api_name:
- _set_new_handler
- _o__set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: c3f1b9bd8bf2a4404e2239858e4c3c59b755bacd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332375"
---
# <a name="_set_new_handler"></a>_set_new_handler

如果 new 运算符无法分配内存，则将控制权传输到错误处理机制****。

## <a name="syntax"></a>语法

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>参数

*p 纽汉德勒*<br/>
指向应用程序提供的内存处理函数的指针。 自变量为 0 会导致新的处理程序被移除。

## <a name="return-value"></a>返回值

返回指向 **_set_new_handler**注册的前一个异常处理函数的指针，以便以后可以还原以前的函数。 如果未设置以前的函数，则返回值可用于还原默认行为;如果未设置以前的函数，则返回值可用于还原默认行为。此值可以是**NULL**。

## <a name="remarks"></a>备注

C++_set_new_handler **_set_new_handler**函数指定一个异常处理函数，如果**新**运算符无法分配内存，该函数将获得控制权。 如果**new**发生故障，运行时系统会自动调用作为参数传递给 **_set_new_handler**的异常处理函数。 **_PNH**在 New.h 中定义，是返回类型**int**并采用类型**size_t**的参数的函数的指针。 使用**size_t**指定要分配的空间量。

没有默认处理程序。

**_set_new_handler**本质上是一个垃圾回收方案。 如果您的函数返回非零值，则运行时系统会重试分配；如果您的函数返回 0，则将失败。

程序中 **_set_new_handler**函数的发生会将参数列表中指定的异常处理函数与运行时系统注册：

```cpp
// set_new_handler1.cpp
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <new.h>

int handle_program_memory_depletion( size_t )
{
   // Your code
}

int main( void )
{
   _set_new_handler( handle_program_memory_depletion );
   int *pi = new int[BIG_NUMBER];
}
```

您可以保存上次传递到 **_set_new_handler**函数的函数地址，并在以后恢复它：

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

C++ [_set_new_mode](set-new-mode.md) 函数将为 [malloc](malloc.md) 设置新的处理程序模式。 新的处理程序模式指示在发生故障时 **，malloc**是否将调用**由 _set_new_handler**设置的新处理程序例程。 默认情况下 **，malloc**不会在分配内存失败时调用新的处理程序例程。 您可以重写此默认行为，以便在**malloc**无法分配内存时 **，malloc**调用新处理程序例程的方式**与新运算符出于**相同原因失败时相同的方式调用新处理程序例程。 若要重写默认值，请调用：

```cpp
_set_new_mode(1);
```

在您程序的早期，或链接到 Newmode.obj。

如果提供了用户定义的`operator new`函数，则新处理程序函数不会在失败时自动调用。

有关详细信息，请参阅 *C++ 语言参考*中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md)。

对于所有动态链接的 DLL 或可执行文件，只有一个 **_set_new_handler**处理程序;即使您调用 **_set_new_handler**您的处理程序可能被另一个替换，或者您要替换由另一个 DLL 或可执行文件设置的处理程序。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

在此示例中，当分配失败时，控件权将转交给 MyNewHandler。 传递给 MyNewHandler 的参数是请求的字节数。 从 MyNewHandler 返回的值是一个指示是否应重试分配的标志：非零值指示应重试分配，零值指示分配已失败。

```cpp
// crt_set_new_handler.cpp
// compile with: /c
#include <stdio.h>
#include <new.h>
#define BIG_NUMBER 0x1fffffff

int coalesced = 0;

int CoalesceHeap()
{
   coalesced = 1;  // Flag RecurseAlloc to stop
   // do some work to free memory
   return 0;
}
// Define a function to be called if new fails to allocate memory.
int MyNewHandler( size_t size )
{
   printf("Allocation failed. Coalescing heap.\n");

   // Call a function to recover some heap space.
   return CoalesceHeap();
}

int RecurseAlloc() {
   int *pi = new int[BIG_NUMBER];
   if (!coalesced)
      RecurseAlloc();
   return 0;
}

int main()
{
   // Set the failure handler for new to be MyNewHandler.
   _set_new_handler( MyNewHandler );
   RecurseAlloc();
}
```

```Output
Allocation failed. Coalescing heap.

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[自由](free.md)<br/>
[realloc](realloc.md)<br/>
