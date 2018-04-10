---
title: Dll 和 Visual c + + 运行库行为 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], entry point function
- process detach [C++]
- process attach [C++]
- DLLs [C++], run-time library behavior
- DllMain function
- _CRT_INIT macro
- _DllMainCRTStartup method
- run-time [C++], DLL startup sequence
- DLLs [C++], startup sequence
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 75bf84eeaf9277c5cf037c4fa59c28d109d95856
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Dll 和 Visual c + + 运行库行为  
  
通过使用 Visual c + +，默认情况下生成动态链接库 (DLL) 时，链接器包括 Visual c + + 运行时库 (VCRuntime)。 VCRuntime 包含初始化和终止 C/c + + 可执行文件所需的代码。 VCRuntime 代码时链接到 DLL，提供一个内部调用的 DLL 入口点函数`_DllMainCRTStartup`用于处理 Windows OS 消息到要将附加到进程或与进程或线程分离的 DLL。 `_DllMainCRTStartup`函数执行重要任务，如堆栈缓冲区安全设置，C 运行时库 (CRT) 初始化和终止，并对静态和全局对象调用构造函数和析构函数。 `_DllMainCRTStartup`此外调用挂钩函数执行其自己的初始化和终止的 WinRT、 MFC 和 ATL 等其他库。 如果没有此初始化、 CRT 和其他库，以及静态变量，将保持处于未初始化状态。 无论是否 DLL 使用静态链接的 CRT 或动态链接的 CRT DLL 称为相同 VCRuntime 内部初始化和终止例程。  
  
## <a name="default-dll-entry-point-dllmaincrtstartup"></a>默认 DLL 入口点 _DllMainCRTStartup  
  
在 Windows 中，所有 Dll 可以都包含一个可选的入口点函数，通常称为`DllMain`，即为初始化和终止调用。 这使你能够分配或释放更多资源，根据需要。 在四个情况下则 Windows 会调用入口点函数： 进程附加、 分离进程、 线程附加，和线程分离。 当 DLL 加载到进程地址空间中，使用它的应用程序加载时，或应用程序请求在运行时 DLL 时，系统将创建 DLL 数据的单独副本。 这称为*进程附加*。 *线程附加*中加载该 DLL 的过程创建一个新线程时发生。 *分离线程*线程终止，时发生和*进程分离*时不再需要的 DLL，并发布应用程序。 操作系统使这些事件，传递的每个单独的 DLL 入口点调用*原因*每个事件类型的自变量。 例如，操作系统将发送`DLL_PROCESS_ATTACH`作为*原因*附加参数，以指示过程。  
  
VCRuntime 库提供调用入口点函数`_DllMainCRTStartup`以处理默认初始化和终止操作。 在过程上附加，`_DllMainCRTStartup`函数将设置缓冲区安全检查，初始化 CRT 和其他库、 初始化运行时类型信息、 初始化和调用静态和非本地数据的构造函数，初始化线程本地存储区递增每个附加的内部静态计数器，然后调用用户或库-提供`DllMain`。 进程分离，该函数将经历这些步骤按相反的顺序。 它调用`DllMain`、 递减内部计数器，会调用析构函数，调用 CRT 终止函数并注册`atexit`函数和通知的终止的任何其他库。 在附件计数器变为零时，该函数将返回`FALSE`以指示 Windows 可以卸载 DLL。 `_DllMainCRTStartup`函数也称为期间线程附加和分离线程。 在这些情况下，VCRuntime 代码不任何附加初始化和终止它自己，并只调用`DllMain`若要将沿消息传递。 如果`DllMain`返回`FALSE`从进程附加，正在故障时，发出信号`_DllMainCRTStartup`调用`DllMain`再次并将传递`DLL_PROCESS_DETACH`作为*原因*自变量，然后经历的其余部分终止进程。  
  
生成 Visual c + + 中的默认入口点的 Dll 时`_DllMainCRTStartup`提供 VCRuntime 自动链接中。 不需要指定适合您的 DLL 的入口点函数，通过使用[/ENTRY （入口点符号）](../build/reference/entry-entry-point-symbol.md)链接器选项。  
  
> [!NOTE]
> 尽管可以使用来指定另一个入口点函数的 DLL /ENTRY： 链接器选项，我们不建议这样做，因为入口点函数必须对要复制的所有内容，`_DllMainCRTStartup`中相同的顺序执行。 Vcruntime 一起提供了函数，您可以复制其行为。 例如，你可以调用[__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md)立即过程附加以支持[/GS （缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)检查选项的缓冲区。 你可以调用`_CRT_INIT`函数，将相同的参数作为入口点函数，若要执行的 DLL 初始化和终止函数的其余部分传递。  
  
<a name="initializing-a-dll"></a>  
  
## <a name="initialize-a-dll"></a>初始化 DLL  
  
DLL 可能拥有当 DLL 加载时必须执行的初始化代码。 为了使你可以执行你自己的 DLL 初始化和终止功能，`_DllMainCRTStartup`调用时调用的函数`DllMain`可提供。 你`DllMain`必须具有所需的 DLL 入口点的签名。 默认入口点函数`_DllMainCRTStartup`调用`DllMain`使用相同的参数传递的 Windows。 默认情况下，如果未提供`DllMain`函数，Visual c + + 为您提供并将其链接中，以便`_DllMainCRTStartup`始终具有一些内容来调用。 这意味着，如果不需要初始化您的 DLL，则没有任何特殊你所要做时生成您的 DLL。  
  
这是用于签名`DllMain`:  
  
```cpp  
#include <windows.h>  
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```  
  
某些库自动换行`DllMain`为你的函数。 例如，在正则 MFC DLL，实现`CWinApp`对象的`InitInstance`和`ExitInstance`成员函数来执行初始化和终止所需的 DLL。 有关更多详细信息，请参阅[regular 初始化 MFC Dll](#initializing-regular-dlls)部分。  
  
> [!WARNING]
> 你可以安全地做什么中的 DLL 入口点上没有重要限制。 请参阅[的常规最佳做法](https://msdn.microsoft.com/library/windows/desktop/dn633971#general_best_practices)是不安全调用中的特定 Windows api `DllMain`。 如果需要任何东西但最简单的初始化然后执行该操作在初始化函数的 dll。 你可以要求应用程序调用之后的初始化函数`DllMain`已运行和前调用任何其他函数 DLL 中。  
  
<a name="initializing-non-mfc-dlls"></a>  
  
### <a name="initialize-ordinary-non-mfc-dlls"></a>初始化普通 (非 MFC) Dll  
  
若要使用 vcruntime 一起提供的普通 (非 MFC) Dll 中执行你自己的初始化`_DllMainCRTStartup`入口点 DLL 源代码必须包含一个名为函数`DllMain`。 下面的代码提供一个基本的主干，显示的定义`DllMain`可能如下所示：  
  
```cpp  
#include <windows.h>
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved)  // reserved
{
    // Perform actions based on the reason for calling.
    switch (reason) 
    { 
    case DLL_PROCESS_ATTACH:
        // Initialize once for each new process.
        // Return FALSE to fail DLL load.
        break;

    case DLL_THREAD_ATTACH:
        // Do thread-specific initialization.
        break;

    case DLL_THREAD_DETACH:
        // Do thread-specific cleanup.
        break;

    case DLL_PROCESS_DETACH:
        // Perform any necessary cleanup.
        break;
    }
    return TRUE;  // Successful DLL_PROCESS_ATTACH.
}
```  
  
> [!NOTE]
> 较旧的 Windows SDK 文档指出，必须在链接器 /ENTRY 选项与命令行上指定的 DLL 入口点函数的实际名称。 不需要使用 Visual c + + 中，如果入口点函数的名称使用 /ENTRY 选项`DllMain`。 事实上，如果你使用的 /ENTRY 选项和名称将入口点以外的函数的内容`DllMain`，除非你入口点函数进行的相同的初始化调用 CRT 不获取初始化不正确`_DllMainCRTStartup`使。  
  
<a name="initializing-regular-dlls"></a>  
  
### <a name="initialize-regular-mfc-dlls"></a>初始化 MFC 的规则 Dll  
  
由于 MFC 的规则 Dll 有`CWinApp`对象时，他们应在与 MFC 应用程序相同的位置中执行初始化和终止任务： 在`InitInstance`和`ExitInstance`成员函数的 DLL 的`CWinApp`-派生类。 由于 MFC 提供了`DllMain`由调用的函数`_DllMainCRTStartup`为`DLL_PROCESS_ATTACH`和`DLL_PROCESS_DETACH`，不应编写你自己`DllMain`函数。 MFC 提供`DllMain`函数调用`InitInstance`在加载 DLL 和其调用时`ExitInstance`将在卸载 DLL 之前。  
  
常规 MFC DLL 可以跟踪的多个线程通过调用[TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801)和[TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812)中其`InitInstance`函数。 这些函数允许 DLL 以跟踪线程特定的数据。  
  
在常规 MFC DLL 动态链接到 MFC，如果你使用的任何 MFC OLE、 MFC 数据库 （或 DAO），或 MFC 套接字支持，分别调试 MFC 扩展 Dll MFCO*版本*D.dll、 MFCD*版本*D.dll 和 MFCN*版本*D.dll (其中*版本*是的版本号) 自动链接中。 你必须为每个你在常规 MFC DLL 中使用这些 Dll 调用以下预定义的初始化函数之一`CWinApp::InitInstance`。  
  
|MFC 支持的类型|初始化函数可以调用|  
|-------------------------|-------------------------------------|  
|MFC OLE (MFCO*版本*D.dll)|`AfxOleInitModule`|  
|MFC 数据库 (MFCD*版本*D.dll)|`AfxDbInitModule`|  
|MFC 套接字 (MFCN*版本*D.dll)|`AfxNetInitModule`|  
  
<a name="initializing-extension-dlls"></a>  
  
### <a name="initialize-mfc-extension-dlls"></a>初始化 MFC 扩展 Dll  
  
因为 MFC 扩展 Dll 不具有`CWinApp`-派生对象 （和 MFC 的规则 Dll 相同），你应添加到你初始化和终止代码`DllMain`MFC DLL 向导生成的函数。  
  
 该向导为 MFC 扩展 Dll 提供下面的代码。 在代码中，`PROJNAME`是你的项目的名称的占位符。  
  
```cpp  
#include "stdafx.h"  
#include <afxdllx.h>  
  
#ifdef _DEBUG  
#define new DEBUG_NEW  
#undef THIS_FILE  
static char THIS_FILE[] = __FILE__;  
#endif  
static AFX_EXTENSION_MODULE PROJNAMEDLL = { NULL, NULL };  
  
extern "C" int APIENTRY  
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)  
{  
   if (dwReason == DLL_PROCESS_ATTACH)  
   {  
      TRACE0("PROJNAME.DLL Initializing!\n");  
  
      // MFC extension DLL one-time initialization  
      AfxInitExtensionModule(PROJNAMEDLL,   
                                 hInstance);  
  
      // Insert this DLL into the resource chain  
      new CDynLinkLibrary(Dll3DLL);  
   }  
   else if (dwReason == DLL_PROCESS_DETACH)  
   {  
      TRACE0("PROJNAME.DLL Terminating!\n");  
   }  
   return 1;   // ok  
}  
```  
  
创建一个新`CDynLinkLibrary`对象在初始化期间允许 MFC 扩展 DLL 导出`CRuntimeClass`对象或客户端应用程序的资源。  
  
如果想要使用 MFC 扩展 DLL 从一个或多个规则的 MFC Dll，你必须导出创建一个初始化函数`CDynLinkLibrary`对象。 必须从每个正则使用 MFC 扩展 DLL 的 MFC Dll 中调用该函数。 调用此初始化函数的适当位置位于`InitInstance`常规 MFC dll 的成员函数`CWinApp`-派生对象，然后才能使用任一 MFC 扩展 DLL 导出的类或函数。  
  
在`DllMain`，MFC DLL 向导生成，调用`AfxInitExtensionModule`捕获模块的运行时类 (`CRuntimeClass`结构) 以及其对象工厂 (`COleObjectFactory`对象) 时使用`CDynLinkLibrary`创建对象。 应检查的返回值`AfxInitExtensionModule`; 如果从返回零值`AfxInitExtensionModule`，返回从零你`DllMain`函数。  
  
如果你的 MFC 扩展 DLL 将显式链接到可执行文件 (这意味着可执行文件调用`AfxLoadLibrary`以链接到 DLL)，你应添加到一个调用`AfxTermExtensionModule`上`DLL_PROCESS_DETACH`。 使用此功能，MFC 以进行每个进程从 MFC 扩展 DLL 中分离时清除 MFC 扩展 DLL (该优化发生在进程退出时或在卸载 DLL 时的结果时`AfxFreeLibrary`调用)。 如果应用程序，对的调用将隐式链接 MFC 扩展 DLL`AfxTermExtensionModule`不需要。  
  
应用程序显式链接到 MFC 扩展 Dll 必须调用`AfxTermExtensionModule`时释放 DLL。 它们还应使用`AfxLoadLibrary`和`AfxFreeLibrary`(而不是 Win32 函数`LoadLibrary`和`FreeLibrary`) 在应用程序使用多个线程。 使用`AfxLoadLibrary`和`AfxFreeLibrary`确保在 MFC 扩展 DLL 加载和卸载不会损坏全局 MFC 状态时执行的启动和关闭代码。  
  
因为 MFCx0.dll 完全初始化时`DllMain`是调用，你可以分配内存并调用中的 MFC 函数`DllMain`（而不像 MFC 的 16 位版本）。  
  
扩展 Dll 可以负责通过处理多线程处理`DLL_THREAD_ATTACH`和`DLL_THREAD_DETACH`情况下，在`DllMain`函数。 这种情况下传递给`DllMain`线程时附加和分离的 dll。 调用[TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801)时附加 DLL 使 DLL 以维护的线程本地存储 (TLS) 对该 DLL 附加每个线程进行索引。  
  
请注意，头文件 Afxdllx.h 包含在 MFC 扩展 Dll，如的定义中使用的结构的特殊定义`AFX_EXTENSION_MODULE`和`CDynLinkLibrary`。 MFC 扩展 DLL 中，应包括此标头文件。  
  
> [!NOTE]
>  很重要，你既不定义也不取消定义的任何`_AFX_NO_XXX`Stdafx.h 中的宏。 这些宏仅用于检查特定的目标平台是否支持该功能，或不存在。 你可以编写你检查这些宏的程序 (例如， `#ifndef _AFX_NO_OLE_SUPPORT`)，但你的程序应永远不会定义或取消定义这些宏。  
  
中包含多线程处理的句柄的示例初始化函数[使用线程本地存储在动态链接库](http://msdn.microsoft.com/library/windows/desktop/ms686997)Windows SDK 中。 请注意此示例包含调用的入口点函数`LibMain`，但你应将此函数的命名`DllMain`，以便它适用于 MFC 和 C 运行时库。  
  
## <a name="see-also"></a>请参阅  
  
[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)  
[DllMain 入口点](https://msdn.microsoft.com/library/windows/desktop/ms682583.aspx)  
[动态链接库最佳做法](https://msdn.microsoft.com/library/windows/desktop/dn633971.aspx)  