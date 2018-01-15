---
title: "_beginthread、_beginthreadex | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
caps.latest.revision: "36"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71d47e67d56da59093db99b5da28daa6f1c18db2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="beginthread-beginthreadex"></a>_beginthread、_beginthreadex
创建线程。  
  
## <a name="syntax"></a>语法  
  
```  
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
  
#### <a name="parameters"></a>参数  
 `start_address`  
 启动开始执行新线程的例程的地址。 对于 `_beginthread`，调用约定是 [__cdecl](../../cpp/cdecl.md) （针对本机代码）或 [__clrcall](../../cpp/clrcall.md) （针对托管代码）；对于 `_beginthreadex`，它是 [__stdcall](../../cpp/stdcall.md) （针对本机代码）或 [__clrcall](../../cpp/clrcall.md) （针对托管代码）。  
  
 `stack_size`  
 新线程的堆栈大小或 0。  
  
 `arglist`  
 要传递到新线程的参数列表或 NULL。  
  
 `Security`  
 指向 [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) 结构的指针，此结构确定返回的句柄是否由子进程继承。 如果 `Security` 为 NULL，则不能继承句柄。 对于 Windows 95 应用程序，必须为 NULL。  
  
 `initflag`  
 控制新线程的初始状态的标志。 将 `initflag` 设置为 `0` 以立即运行，或设置为 `CREATE_SUSPENDED` 以在挂起状态下创建线程；使用 [ResumeThread](http://msdn.microsoft.com/library/windows/desktop/ms685086.aspx) 来执行此线程。 将 `initflag` 设置为 `STACK_SIZE_PARAM_IS_A_RESERVATION` 标志以将 `stack_size` 用作堆栈的初始保留大小（以字节计）；如果未指定此标志， `stack_size` 将指定提交大小。  
  
 `thrdaddr`  
 指向接收线程标识符的 32 位变量。 如果此变量为 NULL，则不可用。  
  
## <a name="return-value"></a>返回值  
 如果成功，则这些函数中的每一个都会返回一个句柄到新创建的线程；但是，如果新创建的线程退出过快，则 `_beginthread` 可能不会返回有效句柄。 （请参见“备注”节中的讨论。）发生错误时，`_beginthread` 返回 -1L，并在线程过多的情况下将 `errno` 设置为 `EAGAIN`；如果参数无效或堆栈大小错误，则设置为 `EINVAL`；如果资源（如内存）不足，则设置为 `EACCES`。 发生错误时， `_beginthreadex` 返回 0 并设置 `errno` 和 `_doserrno` 。  
  
 如果 `startaddress` 为 NULL，则会调用无效的参数处理程序，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 -1。  
  
 有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 有关 `uintptr_t` 的详细信息，请参阅[标准类型](../../c-runtime-library/standard-types.md)。  
  
## <a name="remarks"></a>备注  
 `_beginthread` 函数创建一个在 `start_address`处开始执行例程的线程。 `start_address` 处的例程必须使用 `__cdecl` （对于本机代码）或 `__clrcall` （对于托管代码）调用约定，且应没有任何返回值。 当线程从该例程返回时，就会自动终止。 有关线程的详细信息，请参阅[针对旧代码的多线程支持 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 `_beginthreadex` 比 `_beginthread` 更类似于 Win32 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453.aspx) API。 `_beginthreadex` 和 `_beginthread` 存在以下不同：  
  
-   `_beginthreadex` 有三个其他参数： `initflag`、 `security`和 `threadaddr`。 新线程可通过指定的 security 创建为挂起状态，并且可使用线程标识符 `thrdaddr`进行访问。  
  
-   `start_address` 处传递给 `_beginthreadex` 的例程必须使用 `__stdcall` （对于本机代码）或 `__clrcall` （对于托管代码）调用约定，并且必须返回线程退出代码。  
  
-   如果失败，`_beginthreadex` 会返回 0，而不是 -1L。  
  
-   使用 `_beginthreadex` 创建的线程已通过对 [_endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md)的调用终止。  
  
 与 `_beginthreadex` 相比， `_beginthread` 让你可以在更大程度上控制如何创建线程。 `_endthreadex` 函数也更为灵活。 例如，通过 `_beginthreadex`，你可以使用安全信息、设置线程的初始状态（运行或挂起）并获取新创建线程的线程标识符。 你还可以将 `_beginthreadex` 返回的线程句柄与同步 API 结合使用，但无法通过 `_beginthread`完成此操作。  
  
 使用 `_beginthreadex` 比 `_beginthread`更为安全。 如果由 `_beginthread` 生成的线程很快退出，则返回到 `_beginthread` 调用方的句柄可能无效或指向另一个线程。 但是，由 `_beginthreadex` 返回的句柄必须由 `_beginthreadex`的调用方关闭，因此如果 `_beginthreadex` 未返回任何错误，则可以保证其为有效句柄。  
  
 你可以显式调用 [_endthread](../../c-runtime-library/reference/endthread-endthreadex.md) 或 `_endthreadex` 以终止线程；但是，如果线程从作为参数传递的例程中返回，则自动调用 `_endthread` 或 `_endthreadex` 。 通过对 `_endthread` 或 `_endthreadex` 的调用来终止线程有助于确保正确恢复为线程分配的资源。  
  
 `_endthread` 自动关系线程句柄，但 `_endthreadex` 不会关闭。 因此，当你使用 `_beginthread` 和 `_endthread`时，不要通过调用 Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) API 来显式关闭线程句柄。 该行为与 Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) API 不同。  
  
> [!NOTE]
>  对于与 Libcmt.lib 链接的可执行文件，请不要调用 Win32 `ExitThread` API，这样就不会阻止运行时系统回收已分配的资源。 `_endthread` 和 `_endthreadex` 回收分配的线程资源，然后调用 `ExitThread`。  
  
 当调用了 `_beginthread` 或 `_beginthreadex` 中的任一个时，操作系统将处理堆栈的分配；你不必将该线程堆栈的地址传递给这两个函数中的任何一个。 此外， `stack_size` 参数还可为 0，在这种情况下，操作系统使用的值与为主线程指定的堆栈相同。  
  
 `arglist` 是传递到新创建的线程的参数。 通常这是数据项的地址，例如字符串。 `arglist` 在不需要时可以为 NULL，但必须对 `_beginthread` 和 `_beginthreadex` 赋值才能传递到新线程。 如果任何线程调用 `abort`、 `exit`、 `_exit`或 `ExitProcess`，所有线程都会终止。  
  
 新线程的区域设置继承自起父线程。 如果通过对 [_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md) 的调用（全局或仅针对新线程）启用了每个线程区域设置，则线程可以通过调用 `setlocale` 或 `_wsetlocale`独立从其父级更改区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 对于混合代码和纯代码， `_beginthread` 和 `_beginthreadex` 都具有两种重载，一种采用本机调用约定函数指针，另一种采用 `__clrcall` 函数指针。 第一个重载不是应用程序安全域且永远不会是。 如果你要编写混合代码或纯代码，则必须确保新线程在访问托管资源之前进入正确的应用程序域。 例如，可以使用 [call_in_appdomain 函数](../../dotnet/call-in-appdomain-function.md)来完成该操作。 第二个重载是应用程序安全域；新创建的线程总是在 `_beginthread` 或 `_beginthreadex`调用方的应用程序域中结束。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_beginthread`|\<process.h>|  
|`_beginthreadex`|\<process.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md) 的多线程版本。  
  
 若要使用 `_beginthread` 或 `_beginthreadex`，应用程序必须与一个多线程 C 运行库链接。  
  
## <a name="example"></a>示例  
 下面的示例使用 `_beginthread` 和 `_endthread`。  
  
```  
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
  
// Bounce - Thread to create and and control a colored letter that moves  
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
 下面的代码示例演示如何使用由具有同步 API `_beginthreadex` WaitForSingleObject [的](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx)返回的线程句柄。 主线程需等待第二个线程终止才能继续。 在第二个线程调用 `_endthreadex`时，会使其线程对象进入终止状态。 这将允许主线程继续运行。 这不能通过 `_beginthread` 和 `_endthread`完成，因为 `_endthread` 调用 `CloseHandle`，这会使线程对象在设为终止状态之前被销毁。  
  
```  
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
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_endthread、_endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)