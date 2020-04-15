---
title: _beginthread、_beginthreadex
ms.date: 4/2/2020
api_name:
- _beginthread
- _beginthreadex
- _o__beginthread
- _o__beginthreadex
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
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
ms.openlocfilehash: 2d2851a7e76a43501145b1e55e8028b72c2a8afb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348675"
---
# <a name="_beginthread-_beginthreadex"></a>_beginthread、_beginthreadex

创建线程。

## <a name="syntax"></a>语法

```cpp
uintptr_t _beginthread( // NATIVE CODE
   void( __cdecl *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthread( // MANAGED CODE
   void( __clrcall *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthreadex( // NATIVE CODE
   void *security,
   unsigned stack_size,
   unsigned ( __stdcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
uintptr_t _beginthreadex( // MANAGED CODE
   void *security,
   unsigned stack_size,
   unsigned ( __clrcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
```

### <a name="parameters"></a>参数

*start_address*<br/>
启动开始执行新线程的例程的地址。 对于 **_beginthread**，调用[约定__cdecl（](../../cpp/cdecl.md)对于本机代码）或[__clrcall（](../../cpp/clrcall.md)对于托管代码）;对于 **_beginthreadex**，[它__stdcall（](../../cpp/stdcall.md)对于本机代码）或[__clrcall（](../../cpp/clrcall.md)对于托管代码）。

*stack_size*<br/>
新线程的堆栈大小或 0。

*阿格列斯*<br/>
要传递给新线程的参数列表或**NULL**。

*安全性*<br/>
指向 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 结构的指针，此结构确定返回的句柄是否由子进程继承。 如果*安全*为**NULL，** 则无法继承该句柄。 对于 Windows 95 应用程序，必须**为 NULL。**

*initflag*<br/>
控制新线程的初始状态的标志。 将*initflag*设置为 0 以立即运行，或**CREATE_SUSPENDED**以在挂起状态下创建线程;使用[ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread)执行线程。 将*initflag*设置为**STACK_SIZE_PARAM_IS_A_RESERVATION**标志，以使用*stack_size*作为堆栈的初始保留大小（以字节为单位）;如果未指定此标志 *，stack_size*指定提交大小。

*地addr*<br/>
指向接收线程标识符的 32 位变量。 如果是**NULL，** 则不使用。

## <a name="return-value"></a>返回值

如果成功，这些函数中的每一个都会返回一个句柄到新创建的线程;如果成功，则每个函数都会向新创建的线程返回一个句柄。但是，如果新创建的线程退出速度过快 **，_beginthread**可能不会返回有效的句柄。 （请参阅备注部分的讨论。在错误时 **，_beginthread**返回 -1L，如果线程太多，**则将 errno**设置为**EAGAIN;** 如果参数无效或堆栈大小不正确，则将错误设置为**EAGAIN;** 如果资源不足（如内存），则将错误设置为**EAGAIN。** 错误时 **，_beginthreadex**返回 0，并设置**errno**和 **_doserrno。**

如果*start_address*为**NULL，** 则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将**errno**设置为**EINVAL**并返回 -1。

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关**uintptr_t**的详细信息，请参阅[标准类型](../../c-runtime-library/standard-types.md)。

## <a name="remarks"></a>备注

**_beginthread**函数创建一个线程，该线程开始在*start_address*处执行例程。 *start_address*处的例程必须使用 **__cdecl（** 对于本机代码）或 **__clrcall（** 对于托管代码）调用约定，并且不应具有返回值。 当线程从该例程返回时，就会自动终止。 有关线程的详细信息，请参阅[针对旧代码的多线程支持 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

**_beginthreadex**与 Win32 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) API 更类似于 **_beginthread。** **_beginthreadex**在以下方面不同于 **_beginthread：**

- **_beginthreadex**有三个额外的参数 *：initflag、**安全和***线程添加器**。 新线程可以在具有指定安全性的挂起状态下创建，并且可以使用*thrdaddr*（线程标识符）进行访问。

- 传递给 *_beginthreadexstart_address*的例程必须使用 **__stdcall（** 对于本机代码）或 **_beginthreadex****__clrcall（** 对于托管代码）调用约定，并且必须返回线程退出代码。

- **_beginthreadex**在故障时返回 0，而不是 -1L。

- 使用 **_beginthreadex**创建的线程由对[_endthreadex](endthread-endthreadex.md)的调用终止。

与 **_beginthread**相比 **，_beginthreadex**函数使您能够对线程的创建方式进行更多的控制。 **_endthreadex**功能也更加灵活。 例如，使用 **_beginthreadex**，可以使用安全信息、设置线程的初始状态（运行或挂起），并获取新创建的线程的线程标识符。 您还可以使用 **_beginthreadex**返回的线程句柄与同步 API 一起，而_beginthread无法执行该**操作。**

使用 **_beginthreadex**比 **_beginthread**更安全。 如果 **_beginthread**生成的线程快速退出，则返回给 **_beginthread**调用方的句柄可能无效或指向另一个线程。 但是 **，_beginthreadex**返回的句柄必须由 **_beginthreadex**的调用方关闭，因此，如果 **_beginthreadex**未返回错误，则保证该句柄是有效的句柄。

您可以显式调用[_endthread](endthread-endthreadex.md)或 **_endthreadex**以终止线程;否则，您可以显式调用线程。但是，当线程从作为参数传递的例程返回时，将自动调用 **_endthread**或 **_endthreadex。** 终止调用 **_endthread**或 **_endthreadex**的线程有助于确保正确恢复分配给该线程的资源。

**_endthread**自动关闭线程句柄，而 **_endthreadex**则不关闭线程句柄。 因此，当您使用 **_beginthread**和 **_endthread**时，不要通过调用 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API 显式关闭线程句柄。 该行为与 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API 不同。

> [!NOTE]
> 对于与 Libcmt.lib 链接的可执行文件，不要调用 Win32 **ExitThread** API，以免阻止运行时系统回收已分配的资源。 **_endthread****和_endthreadex**回收分配的线程资源，然后调用**ExitThread**。

调用 **_beginthread**或 **_beginthreadex**时，操作系统处理堆栈的分配;您不必将线程堆栈的地址传递给这些函数中的任何一个。 此外 *，stack_size*参数可以是 0，在这种情况下，操作系统使用的值与为主线程指定的堆栈相同的值。

*arglist*是要传递给新创建的线程的参数。 通常这是数据项的地址，例如字符串。 如果不需要 *，arglist*可以是**NULL，****但必须**_beginthread和 **_beginthreadex**才能传递给新线程。 如果任何线程调用[中止](abort.md)、**退出****、_exit**或**退出进程**，则所有线程都终止。

使用每个进程全局当前区域设置信息初始化新线程区域设置。 如果每个线程区域设置通过调用[_configthreadlocale（](configthreadlocale.md)全局或仅针对新线程）启用，则线程可以通过调用**setlocale**或 **_wsetlocale**独立于其他线程更改其区域设置。 没有每个线程区域设置标志集的线程可能会影响所有其他线程中区域设置信息，这些线程也没有设置每个线程区域设置标志集，以及所有新创建的线程。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

对于 **/clr**代码 **，_beginthread**和 **_beginthreadex**各有两个重载。 一个采用本机调用约定函数指针，另一个采用 **__clrcall**函数指针。 第一个重载不是应用程序安全域且永远不会是。 如果要编写 **/clr**代码，必须确保新线程在访问托管资源之前输入正确的应用程序域。 例如，可以使用 [call_in_appdomain 函数](../../dotnet/call-in-appdomain-function.md)来完成该操作。 第二个重载是应用程序域安全;新创建的线程将始终位于 **_beginthread**或 **_beginthreadex**调用方的应用程序域中。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md) 的多线程版本。

要使用 **_beginthread**或 **_beginthreadex，** 应用程序必须与其中一个多线程 C 运行时库链接。

## <a name="example"></a>示例

下面的示例使用 **_beginthread**和 **_endthread。**

```C
// crt_BEGTHRD.C
// compile with: /MT /D "_X86_" /c
// processor: x86
#include <windows.h>
#include <process.h>    /* _beginthread, _endthread */
#include <stddef.h>
#include <stdlib.h>
#include <conio.h>

void Bounce( void * );
void CheckKey( void * );

// GetRandom returns a random integer between min and max.
#define GetRandom( min, max ) ((rand() % (int)(((max) + 1) - (min))) + (min))
// GetGlyph returns a printable ASCII character value
#define GetGlyph( val ) ((char)((val + 32) % 93 + 33))

BOOL repeat = TRUE;                 // Global repeat flag
HANDLE hStdOut;                     // Handle for console window
CONSOLE_SCREEN_BUFFER_INFO csbi;    // Console information structure

int main()
{
    int param = 0;
    int * pparam = &param;

    // Get display screen's text row and column information.
    hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );
    GetConsoleScreenBufferInfo( hStdOut, &csbi );

    // Launch CheckKey thread to check for terminating keystroke.
    _beginthread( CheckKey, 0, NULL );

    // Loop until CheckKey terminates program or 1000 threads created.
    while( repeat && param < 1000 )
    {
        // launch another character thread.
        _beginthread( Bounce, 0, (void *) pparam );

        // increment the thread parameter
        param++;

        // Wait one second between loops.
        Sleep( 1000L );
    }
}

// CheckKey - Thread to wait for a keystroke, then clear repeat flag.
void CheckKey( void * ignored )
{
    _getch();
    repeat = 0;    // _endthread implied
}

// Bounce - Thread to create and control a colored letter that moves
// around on the screen.
//
// Params: parg - the value to create the character from
void Bounce( void * parg )
{
    char       blankcell = 0x20;
    CHAR_INFO  ci;
    COORD      oldcoord, cellsize, origin;
    DWORD      result;
    SMALL_RECT region;

    cellsize.X = cellsize.Y = 1;
    origin.X = origin.Y = 0;

    // Generate location, letter and color attribute from thread argument.
    srand( _threadid );
    oldcoord.X = region.Left = region.Right =
        GetRandom(csbi.srWindow.Left, csbi.srWindow.Right - 1);
    oldcoord.Y = region.Top = region.Bottom =
        GetRandom(csbi.srWindow.Top, csbi.srWindow.Bottom - 1);
    ci.Char.AsciiChar = GetGlyph(*((int *)parg));
    ci.Attributes = GetRandom(1, 15);

    while (repeat)
    {
        // Pause between loops.
        Sleep( 100L );

        // Blank out our old position on the screen, and draw new letter.
        WriteConsoleOutputCharacterA(hStdOut, &blankcell, 1, oldcoord, &result);
        WriteConsoleOutputA(hStdOut, &ci, cellsize, origin, &region);

        // Increment the coordinate for next placement of the block.
        oldcoord.X = region.Left;
        oldcoord.Y = region.Top;
        region.Left = region.Right += GetRandom(-1, 1);
        region.Top = region.Bottom += GetRandom(-1, 1);

        // Correct placement (and beep) if about to go off the screen.
        if (region.Left < csbi.srWindow.Left)
            region.Left = region.Right = csbi.srWindow.Left + 1;
        else if (region.Right >= csbi.srWindow.Right)
            region.Left = region.Right = csbi.srWindow.Right - 2;
        else if (region.Top < csbi.srWindow.Top)
            region.Top = region.Bottom = csbi.srWindow.Top + 1;
        else if (region.Bottom >= csbi.srWindow.Bottom)
            region.Top = region.Bottom = csbi.srWindow.Bottom - 2;

        // If not at a screen border, continue, otherwise beep.
        else
            continue;
        Beep((ci.Char.AsciiChar - 'A') * 100, 175);
    }
    // _endthread given to terminate
    _endthread();
}
```

按任意键结束示例应用程序。

## <a name="example"></a>示例

以下示例代码演示如何使用 **_beginthreadex**与同步 API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)一起返回的线程句柄。 主线程需等待第二个线程终止才能继续。 当第二个线程调用 **_endthreadex**，它会导致其线程对象进入信号状态。 这将允许主线程继续运行。 这不能用 **_beginthread**和 **_endthread，** 因为 **_endthread**调用**CloseHandle，** 这将在线程对象设置为信号状态之前销毁它。

```cpp
// crt_begthrdex.cpp
// compile with: /MT
#include <windows.h>
#include <stdio.h>
#include <process.h>

unsigned Counter;
unsigned __stdcall SecondThreadFunc( void* pArguments )
{
    printf( "In second thread...\n" );

    while ( Counter < 1000000 )
        Counter++;

    _endthreadex( 0 );
    return 0;
}

int main()
{
    HANDLE hThread;
    unsigned threadID;

    printf( "Creating second thread...\n" );

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc, NULL, 0, &threadID );

    // Wait until second thread terminates. If you comment out the line
    // below, Counter will not be correct because the thread has not
    // terminated, and Counter most likely has not been incremented to
    // 1000000 yet.
    WaitForSingleObject( hThread, INFINITE );
    printf( "Counter should be 1000000; it is-> %d\n", Counter );
    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
Creating second thread...
In second thread...
Counter should be 1000000; it is-> 1000000
```

## <a name="see-also"></a>另请参阅

- [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)
- [_endthread、_endthreadex](endthread-endthreadex.md)
- [中止](abort.md)
- [exit、_Exit、_exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
