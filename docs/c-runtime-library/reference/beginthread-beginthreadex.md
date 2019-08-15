---
title: _beginthread、_beginthreadex
ms.date: 02/27/2018
apiname:
- _beginthread
- _beginthreadex
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 27bc850281f7591b4fa23a03e9adc3bc02bda87b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500309"
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
启动开始执行新线程的例程的地址。 对于 **_beginthread**, 调用约定为[__cdecl](../../cpp/cdecl.md) (对于本机代码) 或[__clrcall](../../cpp/clrcall.md) (对于托管代码);对于 **_beginthreadex**, 它是[__stdcall](../../cpp/stdcall.md) (对于本机代码) 或[__clrcall](../../cpp/clrcall.md) (对于托管代码)。

*stack_size*<br/>
新线程的堆栈大小或 0。

*arglist*<br/>
要传递到新线程的参数列表, 或为**NULL**。

*安全性*<br/>
指向 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 结构的指针，此结构确定返回的句柄是否由子进程继承。 如果*安全性*为**NULL**, 则不能继承句柄。 对于 Windows 95 应用程序, 必须为**NULL** 。

*initflag*<br/>
控制新线程的初始状态的标志。 将*initflag*设置为0可立即运行, 或设置为**CREATE_SUSPENDED**以在挂起状态下创建线程;使用[ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread)执行线程。 将*initflag*设置为**STACK_SIZE_PARAM_IS_A_RESERVATION**标志, 以将*STACK_SIZE*用作堆栈的初始保留大小 (以字节为单位);如果未指定此标志, *stack_size*将指定提交大小。

*thrdaddr*<br/>
指向接收线程标识符的 32 位变量。 如果**为 NULL**, 则不使用。

## <a name="return-value"></a>返回值

如果成功, 则这些函数将返回新创建的线程的句柄;但是, 如果新创建的线程退出速度太快, **_beginthread**可能不会返回有效句柄。 （请参见“备注”节中的讨论。）出现错误时, 如果线程过多, **_beginthread**将返回-1L, **Errno**设置为**EAGAIN** , 如果参数无效或堆栈大小不正确, 则为**EINVAL** ; 如果资源不足, 则设置为**EACCES**如内存)。 出现错误时, **_beginthreadex**将返回 0, 并设置**errno**和 **_doserrno** 。

如果*start_address*为**NULL**, 则将调用无效参数处理程序, 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则这些函数会将**errno**设置为**EINVAL** , 并返回-1。

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关**uintptr_t**的详细信息, 请参阅[标准类型](../../c-runtime-library/standard-types.md)。

## <a name="remarks"></a>备注

**_Beginthread**函数创建一个在*start_address*开始执行例程的线程。 *Start_address*处的例程必须使用 **__cdecl** (对于本机代码) 或 **__clrcall** (对于托管代码) 调用约定, 并且应没有返回值。 当线程从该例程返回时，就会自动终止。 有关线程的详细信息，请参阅[针对旧代码的多线程支持 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

与 **_beginthread**相比, **_Beginthreadex**类似于 Win32 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) API。 **_beginthreadex**在以下方面与 **_beginthread**不同:

- **_beginthreadex**有三个附加参数: *initflag*、 *Security*和**threadaddr**。 可以使用指定的安全性在挂起状态下创建新线程, 并且可以使用*thrdaddr*(它是线程标识符) 进行访问。

- 传递给 **_beginthreadex**的*start_address*中的例程必须使用 **__stdcall** (对于本机代码) 或 **__clrcall** (用于托管代码) 调用约定, 并且必须返回线程退出代码。

- 如果失败, **_beginthreadex**将返回 0, 而不是-1L。

- 使用 **_beginthreadex**创建的线程由对[_endthreadex](endthread-endthreadex.md)的调用终止。

与 **_beginthread**相比, **_beginthreadex**函数可以更好地控制如何创建线程。 **_Endthreadex**函数也更为灵活。 例如, 使用 **_beginthreadex**时, 可以使用安全信息、设置线程的初始状态 (运行或挂起) 并获取新创建的线程的线程标识符。 你还可以将 **_beginthreadex**返回的线程句柄与同步 api 一起使用, 而不能使用 **_beginthread**来执行此操作。

使用 **_beginthreadex**比 **_beginthread**更安全。 如果由 **_beginthread**生成的线程很快退出, 则返回到 **_beginthread**调用方的句柄可能无效或指向另一个线程。 但是, 由 **_beginthreadex**返回的句柄必须由 **_beginthreadex**的调用方关闭, 因此如果 **_beginthreadex**未返回错误, 则可以保证其为有效句柄。

可以显式调用[_endthread](endthread-endthreadex.md)或 **_endthreadex**以终止线程;但是, 当线程从作为参数传递的例程中返回时, 会自动调用 **_endthread**或 **_endthreadex** 。 使用对 **_endthread**或 **_endthreadex**的调用来终止线程有助于确保正确恢复为线程分配的资源。

**_endthread**会自动关闭线程句柄, 而 **_endthreadex**则不会。 因此, 使用 **_beginthread**和 **_endthread**时, 不要通过调用 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API 来显式关闭线程句柄。 该行为与 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API 不同。

> [!NOTE]
> 对于与 Libcmt.lib 链接的可执行文件, 请不要调用 Win32 **ExitThread** API, 这样就不会阻止运行时系统回收已分配的资源。 **_endthread**和 **_endthreadex**回收分配的线程资源, 然后调用**ExitThread**。

调用 **_beginthread**或 **_beginthreadex**时, 操作系统将处理堆栈的分配;无需将线程堆栈的地址传递给这些函数中的任何一个。 此外, *stack_size*参数可以为 0, 在这种情况下, 操作系统使用的值与为主线程指定的堆栈相同。

*arglist*是要传递到新创建的线程的参数。 通常这是数据项的地址，例如字符串。 如果不需要, *arglist*可以为**NULL** , 但必须为 **_beginthread**和 **_beginthreadex**给定一些值才能传递到新线程。 如果任何线程调用[abort](abort.md)、 **exit**、 **_exit**或**ExitProcess**, 则所有线程都将终止。

新线程的区域设置通过使用按进程全局当前区域设置信息初始化。 如果通过对[_configthreadlocale](configthreadlocale.md)的调用 (全局或仅针对新线程) 启用了每个线程区域设置, 则线程可以通过调用**setlocale**或 **_wsetlocale**独立于其他线程来更改其区域设置。 未设置每个线程的区域设置标志的线程可能会影响还未设置每个线程区域设置标志的所有其他线程中的区域设置信息, 以及所有新创建的线程。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

对于 **/clr**代码, 每个 **_beginthread**和 **_beginthreadex**都有两个重载。 一种采用本机调用约定函数指针, 另一种采用 **__clrcall**函数指针。 第一个重载不是应用程序安全域且永远不会是。 如果要编写 **/clr**代码, 则必须确保新线程在访问托管资源之前进入正确的应用程序域。 例如，可以使用 [call_in_appdomain 函数](../../dotnet/call-in-appdomain-function.md)来完成该操作。 第二个重载是应用程序域安全的;新创建的线程始终会在 **_beginthread**或 **_beginthreadex**调用方的应用程序域中结束。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行库](../../c-runtime-library/crt-library-features.md) 的多线程版本。

若要使用 **_beginthread**或 **_beginthreadex**, 应用程序必须与一个多线程 C 运行库链接。

## <a name="example"></a>示例

下面的示例使用 **_beginthread**和 **_endthread**。

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

下面的示例代码演示了如何将 **_beginthreadex**返回的线程句柄与同步 API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)结合使用。 主线程需等待第二个线程终止才能继续。 当第二个线程调用 **_endthreadex**时, 它会使其线程对象转为终止状态。 这将允许主线程继续运行。 不能对 **_beginthread**和 **_endthread**执行此操作, 因为 **_endthread**会调用**CloseHandle**, 这会销毁线程对象, 然后将其设置为终止状态。

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

## <a name="see-also"></a>请参阅

- [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)
- [_endthread、_endthreadex](endthread-endthreadex.md)
- [abort](abort.md)
- [exit、_Exit、_exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
