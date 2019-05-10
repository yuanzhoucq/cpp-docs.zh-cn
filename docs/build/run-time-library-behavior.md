---
title: Dll 和视觉对象C++运行时库行为
ms.date: 05/06/2019
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
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
ms.openlocfilehash: d3f3197b6b7b01e7f69767b72286d6d21470cb0e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217751"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Dll 和视觉对象C++运行时库行为

链接器时使用 Visual Studio 中，默认情况下生成动态链接库 (DLL)，包括视觉对象C++运行时库 (VCRuntime)。 VCRuntime 包含初始化和终止 C 所需的代码 /C++可执行文件。 链接到 DLL，VCRuntime 代码提供了一个内部调用的 DLL 入口点函数`_DllMainCRTStartup`用于处理 Windows OS 消息到 DLL 以将附加到或从进程或线程分离。 `_DllMainCRTStartup`函数执行重要任务，例如堆栈缓冲区安全性设置，C 运行时库 (CRT) 初始化和终止，并对构造函数和析构函数中调用静态和全局对象的。 `_DllMainCRTStartup` 此外调用挂钩函数的其他库，如 WinRT、 MFC 和 ATL 来执行其自己的初始化和终止。 如果没有此初始化、 CRT 和其他库，以及静态变量，将保持处于未初始化状态。 无论您的 DLL 使用静态链接的 CRT 还是动态链接的 CRT DLL 调用的相同 VCRuntime 内部初始化和终止例程。

## <a name="default-dll-entry-point-dllmaincrtstartup"></a>默认 DLL 入口点 _DllMainCRTStartup

在 Windows 中，所有 Dll 可都包含一个可选入口点函数，通常称为`DllMain`，即为初始化和终止调用。 这样，您可以分配或根据需要释放其他资源。 Windows 在四种情况下调用入口点函数： 进程附加、 进程分离、 线程附加和线程分离。 当 DLL 加载到进程地址空间，使用它的应用程序加载时，或应用程序请求在运行时 DLL 时，操作系统会创建 DLL 数据的单独副本。 这称为*进程附加*。 *线程附加*的进程中加载了 DLL 创建一个新线程时发生。 *线程分离*时发生的线程终止，并*进程分离*时不再需要的 DLL，并发布应用程序。 此操作系统会单独调用的 DLL 入口点的每个事件，并传递*原因*每个事件类型的参数。 例如，OS 会发送`DLL_PROCESS_ATTACH`作为*原因*参数发出信号进程附加。

VCRuntime 库提供了名为入口点函数`_DllMainCRTStartup`处理默认值初始化和终止操作。 在过程上附加，`_DllMainCRTStartup`函数设置了缓冲区安全检查，初始化 CRT 和其他库、 初始化运行时类型信息，初始化并调用构造函数的静态和非本地数据，初始化线程本地存储递增每个附加的内部静态计数器，然后调用用户或库-提供`DllMain`。 在进程分离，该函数将完成这些步骤按相反的顺序。 它将调用`DllMain`递减内部计数器，调用析构函数、 调用 CRT 终止函数并注册`atexit`函数，并通知的终止的任何其他库。 当附件计数器回到零时，该函数返回`FALSE`以指示 Windows 可以卸载 DLL。 `_DllMainCRTStartup`函数还调用期间线程附加和线程分离。 在这些情况下，VCRuntime 代码任何附加的初始化和终止其自身的、 不会，只需调用`DllMain`来传递沿该消息。 如果`DllMain`返回`FALSE`进程中附加，信令故障时，`_DllMainCRTStartup`调用`DllMain`试，并将传递`DLL_PROCESS_DETACH`作为*原因*参数，然后将经历的其余部分终止进程。

构建在 Visual Studio 中的默认入口点的 Dll 时`_DllMainCRTStartup`提供 VCRuntime 自动链接中。 不需要使用您的 DLL 指定入口点函数[/ENTRY （入口点符号）](reference/entry-entry-point-symbol.md)链接器选项。

> [!NOTE]
> 虽然可以使用 /ENTRY dll 指定另一个入口点函数： 链接器选项，我们不建议这样做，因为入口点函数必须重复的所有内容的`_DllMainCRTStartup`中相同的顺序执行。 VCRuntime 提供允许您可以复制其行为的函数。 例如，可以调用[__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md)立即在过程上附加以支持[/GS （缓冲区安全检查）](reference/gs-buffer-security-check.md)缓冲区检查选项。 您可以调用`_CRT_INIT`函数，将作为入口点函数，来执行 DLL 初始化和终止函数的其余部分传递相同的参数。

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>初始化 DLL

您的 DLL 可能具有在 DLL 加载时必须执行的初始化代码。 为了使您可以执行您自己的 DLL 初始化和终止函数，`_DllMainCRTStartup`调用一个名为函数`DllMain`，可以提供。 你`DllMain`必须具有所需的 DLL 入口点的签名。 默认入口点函数`_DllMainCRTStartup`调用`DllMain`Windows 使用相同的参数传递。 默认情况下，如果未提供`DllMain`函数，Visual Studio 提供了一个并将其链接中，以便`_DllMainCRTStartup`始终具有要调用的内容。 这意味着，如果不需要初始化 DLL，并没有什么特别您只需生成 DLL 时。

这是用于签名`DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

某些库包装`DllMain`为你的函数。 例如，在规则 MFC DLL，实现`CWinApp`对象的`InitInstance`和`ExitInstance`成员函数来执行初始化和终止所需的 DLL。 有关更多详细信息，请参阅[regular 初始化 MFC Dll](#initializing-regular-dlls)部分。

> [!WARNING]
> 您可以安全地执行的操作中的 DLL 入口点有明显的限制。 请参阅[的常规最佳做法](/windows/desktop/Dlls/dynamic-link-library-best-practices)不安全调用中的特定 Windows api `DllMain`。 如果需要任何内容，但是最简单的初始化然后执行该操作初始化函数中的 dll。 你可以要求应用程序调用初始化函数之后，`DllMain`具有运行和前调用任何其他函数在 DLL 中。

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>初始化 Dll 普通 (非 MFC)

若要执行你自己的初始化中使用的 vcruntime 一起提供的普通 (非 MFC) Dll`_DllMainCRTStartup`入口点 DLL 源代码必须包含一个名为函数`DllMain`。 下面的代码提供一个基本的主干，显示的定义`DllMain`可能如下所示：

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
> 较旧的 Windows SDK 文档中指出，必须在链接器 /ENTRY 选项的命令行上指定的 DLL 入口点函数的实际名称。 不需要使用 Visual Studio 中，如果入口点函数的名称是使用 /ENTRY 选项`DllMain`。 事实上，如果您使用 /ENTRY 选项和名称将入口点运行内容以外`DllMain`，除非您的入口点函数进行的相同的初始化调用 CRT 不获取初始化不正确`_DllMainCRTStartup`使。

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>初始化规则 MFC Dll

因为规则 MFC Dll`CWinApp`对象，它们应在与 MFC 应用程序相同的位置执行初始化和终止任务： 在`InitInstance`并`ExitInstance`成员函数的 DLL 的`CWinApp`-派生类。 由于 MFC 提供了`DllMain`由调用的函数`_DllMainCRTStartup`有关`DLL_PROCESS_ATTACH`并`DLL_PROCESS_DETACH`，不应编写你自己`DllMain`函数。 提供 MFC`DllMain`函数调用`InitInstance`时加载 DLL 和它调用`ExitInstance`卸载 DLL 之前。

规则 MFC DLL 可以跟踪的多个线程通过调用[TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)并[TlsGetValue](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)中其`InitInstance`函数。 这些函数使跟踪特定于线程的数据的 DLL。

在规则 MFC DLL 动态链接到 MFC，如果使用的任何 MFC OLE，MFC 数据库 （或 DAO），或 MFC 套接字支持，分别调试 MFC 扩展 Dll MFCO*版本*D.dll，MFCD*版本*D.dll 和 MFCN*版本*D.dll (其中*版本*是版本号) 中自动链接。 必须为每个规则 MFC DLL 的中使用这些 Dll 调用以下预定义的初始化函数之一`CWinApp::InitInstance`。

|MFC 支持的类型|要调用的初始化函数|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*版本*D.dll)|`AfxOleInitModule`|
|MFC 数据库 (MFCD*版本*D.dll)|`AfxDbInitModule`|
|MFC 套接字 (MFCN*版本*D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>初始化 MFC 扩展 Dll

因为 MFC 扩展 Dll 不具有`CWinApp`-派生对象 （如执行规则 MFC Dll），应添加到在初始化和终止代码`DllMain`MFC DLL 向导生成的函数。

该向导的 MFC 扩展 Dll 提供下面的代码。 在代码中，`PROJNAME`是项目的名称的占位符。

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

创建一个新`CDynLinkLibrary`对象在初始化期间，MFC 扩展 DLL 导出`CRuntimeClass`对象或客户端应用程序的资源。

如果要使用 MFC 扩展 DLL 从一个或多个规则 MFC Dll，则必须导出创建的初始化函数`CDynLinkLibrary`对象。 必须从每个使用 MFC 扩展 DLL 规则 MFC Dll 调用该函数。 更好地调用此初始化函数处于`InitInstance`成员函数的规则 MFC DLL 的`CWinApp`-然后再使用 MFC 扩展 DLL 导出的类或函数的任何派生的对象。

在中`DllMain`，MFC DLL 向导生成，调用`AfxInitExtensionModule`捕获模块的运行时类 (`CRuntimeClass`结构) 以及其对象工厂 (`COleObjectFactory`对象) 时使用`CDynLinkLibrary`创建对象。 应检查的返回值`AfxInitExtensionModule`; 如果返回值为零`AfxInitExtensionModule`，返回零从你`DllMain`函数。

如果您的 MFC 扩展 DLL 将显式链接到可执行文件 (这意味着可执行文件调用`AfxLoadLibrary`若要链接到 DLL)，您应添加到一个调用`AfxTermExtensionModule`上`DLL_PROCESS_DETACH`。 此函数使 MFC 从 MFC 扩展 DLL 中的每个进程分离时清理 MFC 扩展 DLL (正好在进程退出时或当卸载 DLL 时为`AfxFreeLibrary`调用)。 如果您的 MFC 扩展 DLL 将隐式链接到应用程序调用`AfxTermExtensionModule`不是必需的。

应用程序显式链接到 MFC 扩展 Dll 必须调用`AfxTermExtensionModule`时释放该 DLL。 它们还应使用`AfxLoadLibrary`并`AfxFreeLibrary`(而不是 Win32 函数`LoadLibrary`和`FreeLibrary`) 在应用程序使用多个线程。 使用`AfxLoadLibrary`和`AfxFreeLibrary`确保 MFC 扩展 DLL 加载和卸载不会损坏全局 MFC 状态时执行的启动和关闭代码。

因为时完全初始化 MFCx0.dll`DllMain`是调用，可以分配内存，并调用中的 MFC 函数`DllMain`（不同于 MFC 的 16 位版本）。

扩展 Dll 可以负责通过处理多线程处理`DLL_THREAD_ATTACH`并`DLL_THREAD_DETACH`情况下，在`DllMain`函数。 这种情况下传递给`DllMain`时线程附加和分离从 DLL。 调用[TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)时附加一个 DLL 可确保 DLL 可以维护的线程本地存储 (TLS) 索引为每个线程附加到 DLL。

请注意，头文件 Afxdllx.h 包含特殊的定义，MFC 扩展 Dll，如的定义中使用结构`AFX_EXTENSION_MODULE`和`CDynLinkLibrary`。 MFC 扩展 DLL 中，应包括此标头文件。

> [!NOTE]
>  非常重要，就既不定义也不能取消定义的任何`_AFX_NO_XXX`Stdafx.h 中的宏。 这些宏仅用于检查特定的目标平台是否支持该功能，或不存在。 可以编写应用程序来检查这些宏 (例如， `#ifndef _AFX_NO_OLE_SUPPORT`)，但您的程序应永远不会定义或取消定义这些宏。

中包含的多线程处理的句柄的示例初始化函数[使用线程本地存储在动态链接库](/windows/desktop/Dlls/using-thread-local-storage-in-a-dynamic-link-library)Windows SDK 中。 请注意，该示例包含名为入口点函数`LibMain`，但您应将此函数命名`DllMain`，使其可以使用 MFC 和 C 运行时库。

## <a name="see-also"></a>请参阅

[创建 C /C++ Visual Studio 中的 Dll](dlls-in-visual-cpp.md)<br/>
[DllMain 入口点](/windows/desktop/Dlls/dllmain)<br/>
[动态链接库的最佳做法](/windows/desktop/Dlls/dynamic-link-library-best-practices)
