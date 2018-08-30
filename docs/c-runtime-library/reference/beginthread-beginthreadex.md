---
title: _beginthread、_beginthreadex | Microsoft 文档
ms.custom: ''
ms.date: 02/27/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4bdae31c3a2f84dd959baf49fae7e43a6cc9eb0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206392"
---
# <a name="beginthread-beginthreadex"></a>_beginthread、_beginthreadex

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
启动开始执行新线程的例程的地址。 有关 **_beginthread**，调用约定是[__cdecl](../../cpp/cdecl.md) （对于本机代码） 或[__clrcall](../../cpp/clrcall.md) （适用于托管代码）; 对于 **_beginthreadex**，它是[__stdcall](../../cpp/stdcall.md) （适用于本机代码） 或[__clrcall](../../cpp/clrcall.md) （适用于托管代码）。

*stack_size*<br/>
新线程的堆栈大小或 0。

*arglist*<br/>
要传递给一个新线程，参数列表或**NULL**。

*安全性*<br/>
指向 [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) 结构的指针，此结构确定返回的句柄是否由子进程继承。 如果*安全*是**NULL**，不能继承句柄。 必须是**NULL** Windows 95 应用程序。

*initflag*<br/>
控制新线程的初始状态的标志。 设置*initflag*为 0 以立即运行，或**CREATE_SUSPENDED**创建的线程处于挂起状态; 使用[ResumeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-resumethread)来执行此线程。 设置*initflag*到**STACK_SIZE_PARAM_IS_A_RESERVATION**若要使用的标志*stack_size*如初始保留以字节为单位的堆栈大小; 如果此标志为未指定， *stack_size*指定提交大小。

*thrdaddr*<br/>
指向接收线程标识符的 32 位变量。 如果它是**NULL**，不使用它。

## <a name="return-value"></a>返回值

如果成功，每个函数返回的句柄的新创建的线程;但是，如果新创建的线程退出过快 **_beginthread**可能不会返回有效句柄。 （请参见“备注”节中的讨论。）发生错误时， **_beginthread**返回-1l，并**errno**设置为**EAGAIN**如果到太多线程**EINVAL**如果参数为无效或堆栈大小不正确，或设置为**EACCES**是否存在资源 （例如内存） 不足。 发生错误时， **_beginthreadex**返回 0，并且**errno**并 **_doserrno**设置。

如果*start_address*是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，这些函数将设置**errno**到**EINVAL**并返回-1。

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关详细信息**uintptr_t**，请参阅[标准类型](../../c-runtime-library/standard-types.md)。

## <a name="remarks"></a>备注

**_Beginthread**函数创建开始处的例程执行一个线程*start_address*。 处的例程*start_address*必须使用 **__cdecl** （对于本机代码） 或 **__clrcall** （适用于托管代码） 调用约定，并且应具有任何返回值。 当线程从该例程返回时，就会自动终止。 有关线程的详细信息，请参阅[针对旧代码的多线程支持 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

**_beginthreadex**类似于 Win32 [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread)更多的 API 比 **_beginthread** does。 **_beginthreadex**不同于 **_beginthread**以下方面：

- **_beginthreadex**有三个其他参数： *initflag*，*安全*，并且**threadaddr**。 新线程处于挂起状态，通过指定的 security，可以创建和使用可以访问*thrdaddr*，即线程标识符。

- 处的例程*start_address*传递给 **_beginthreadex**必须使用 **__stdcall** （对于本机代码） 或 **__clrcall** （适用于托管代码） 调用约定，并且必须返回线程退出代码。

- **_beginthreadex**失败，而不是-1l 会返回 0。

- 通过使用创建的线程 **_beginthreadex**通过调用终止[_endthreadex](endthread-endthreadex.md)。

**_Beginthreadex**函数提供更好地控制如何在线程创建比 **_beginthread** does。 **_Endthreadex**函数也是更加灵活。 例如，对于 **_beginthreadex**，可以使用安全信息、 线程 （运行或暂停），将初始状态设置和获取新创建的线程的线程标识符。 此外可以使用返回的线程句柄 **_beginthreadex**与同步 Api，您不能执行此操作与 **_beginthread**。

使用更安全 **_beginthreadex**比 **_beginthread**。 如果生成的线程 **_beginthread**很快退出，返回给调用方的句柄 **_beginthread**可能无效或指向另一个线程。 但是，返回的句柄 **_beginthreadex**的调用方必须关闭 **_beginthreadex**，因此它保证是有效的句柄，如果 **_beginthreadex**未返回错误。

可以调用[_endthread](endthread-endthreadex.md)或 **_endthreadex**显式以终止线程; 但是， **_endthread**或者 **_endthreadex**称为将自动当线程返回从作为参数传递的例程。 终止线程通过调用 **_endthread**或 **_endthreadex**有助于确保正确恢复为线程分配的资源。

**_endthread**会自动关闭线程句柄，而 **_endthreadex**却没有。 因此，当你使用 **_beginthread**并 **_endthread**，不要显式关闭线程句柄通过调用 Win32 [CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) API。 该行为与 Win32 [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) API 不同。

> [!NOTE]
> 对于与 Libcmt.lib 链接的可执行文件，不要调用 Win32 **ExitThread** API，以便您不会阻止运行时系统回收已分配资源。 **_endthread**并 **_endthreadex**回收分配的线程资源，然后调用**ExitThread**。

操作系统处理堆栈的分配时任一 **_beginthread**或 **_beginthreadex**称为; 无需将该线程堆栈的地址传递给这些函数之一。 此外， *stack_size*参数可以是的 0，在其中用例操作系统使用相同的值作为指定的堆栈的主线程。

*arglist*是传递给新创建的线程的参数。 通常这是数据项的地址，例如字符串。 *arglist*可以是**NULL**如果不需要但 **_beginthread**并 **_beginthreadex**必须指定一些值来传递到新线程。 如果任何线程调用，所有线程都会都终止[中止](abort.md)，**退出**， **_exit**，或者**ExitProcess**。

使用每个进程全局当前区域设置信息初始化新线程的区域设置。 如果通过调用启用了每个线程区域设置[_configthreadlocale](configthreadlocale.md) （全局范围内或针对新线程仅限），线程可以更改区域设置独立地从其他线程通过调用**setlocale**或 **_wsetlocale**。 没有设置了每个线程区域设置标记的线程可能会影响在还没有设置，每个线程区域设置标记的所有其他线程，以及所有新创建的线程的区域设置信息。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

有关 **/clr**代码中， **_beginthread**并 **_beginthreadex**每个具有两个重载。 一种采用本机调用约定函数指针，另一个采用 **__clrcall**函数指针。 第一个重载不是应用程序安全域且永远不会是。 如果你正在编写 **/clr**代码必须确保新线程进入正确的应用程序域，然后才能访问托管资源。 例如，可以使用 [call_in_appdomain 函数](../../dotnet/call-in-appdomain-function.md)来完成该操作。 第二个重载是应用程序安全域;新创建的线程将始终最终的应用程序域中的调用方 **_beginthread**或 **_beginthreadex**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行库](../../c-runtime-library/crt-library-features.md) 的多线程版本。

若要使用 **_beginthread**或 **_beginthreadex**，应用程序必须与其中一个多线程 C 运行时库链接。

## <a name="example"></a>示例

下面的示例使用 **_beginthread**并 **_endthread**。

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

下面的示例代码演示如何使用返回的线程句柄 **_beginthreadex**具有同步 API [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject)。 主线程需等待第二个线程终止才能继续。 当第二个线程调用 **_endthreadex**，它会导致其线程对象进入终止状态。 这将允许主线程继续运行。 这不能通过 **_beginthread**并 **_endthread**，这是因为 **_endthread**调用**CloseHandle**，其中销毁线程它可以设置为终止状态之前的对象。

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
- [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
