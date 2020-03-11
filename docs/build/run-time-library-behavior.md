---
title: Dll 和 Visual C++运行时库行为
ms.date: 08/19/2019
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
ms.openlocfilehash: 572a0ba70c1ba2d46d2d9fd6d8ac543a77bbbc01
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856769"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Dll 和 Visual C++运行时库行为

使用 Visual Studio 生成动态链接库（DLL）时，默认情况下，链接器会包括 Visual C++运行时库（VCRuntime）。 VCRuntime 包含初始化和终止 C/C++可执行文件所需的代码。 当链接到 DLL 时，VCRuntime 代码将提供名为 `_DllMainCRTStartup` 的内部 DLL 入口点函数，该函数将向 DLL 处理 Windows OS 消息以附加到进程或线程或从进程或线程分离。 `_DllMainCRTStartup` 函数执行如下所述的基本任务：设置堆栈缓冲区安全、C 运行时库（CRT）初始化和终止，并为静态对象和全局对象调用构造函数和析构函数。 `_DllMainCRTStartup` 还会调用其他库（如 WinRT、MFC 和 ATL）的挂钩函数，以执行其自己的初始化和终止。 如果没有此初始化，CRT 和其他库以及静态变量将处于未初始化状态。 无论 DLL 使用静态链接的 CRT 还是动态链接的 CRT DLL，都将调用相同的 VCRuntime 内部初始化和终止例程。

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>默认 DLL 入口点 _DllMainCRTStartup

在 Windows 中，所有 Dll 都可以包含一个可选入口点函数（通常称为 `DllMain`），该函数将调用初始化和终止。 这为你提供了根据需要分配或释放其他资源的机会。 Windows 在四种情况下调用入口点函数：进程附加、进程分离、线程附加和线程分离。 当 DLL 加载到进程地址空间时，在加载使用它的应用程序时，或者当应用程序在运行时请求 DLL 时，操作系统将创建 DLL 数据的单独副本。 这称为 "*进程附加*"。 当在中加载 DLL 的进程创建新的线程时，*将发生线程附加*。 当线程终止时，*线程分离*发生，并且在不再需要 DLL 并由应用程序发布时，*处理分离*操作。 操作系统对每个事件的每个事件都单独调用 DLL 入口点，并为每个事件类型传递*原因*参数。 例如，OS 将 `DLL_PROCESS_ATTACH` 作为 "*原因*" 参数发送到 "连接到信号"。

VCRuntime 库提供了一个入口点函数，称为 `_DllMainCRTStartup` 处理默认的初始化和终止操作。 在 "进程附加" 上，`_DllMainCRTStartup` 函数将设置缓冲区安全检查，初始化 CRT 和其他库，初始化运行时类型信息，为静态和非本地数据初始化和调用构造函数，初始化线程本地存储，递增每个连接的内部静态计数器，然后调用用户提供的 `DllMain`。 处理分离时，函数将按相反的顺序执行这些步骤。 它调用 `DllMain`、递减内部计数器、调用析构函数、调用 CRT 终止函数和注册的 `atexit` 函数，并通知任何其他终止库。 当附件计数器变为零时，函数将返回 `FALSE` 以向 Windows 指示 DLL 可以卸载。 线程附加和线程分离期间也会调用 `_DllMainCRTStartup` 函数。 在这些情况下，VCRuntime 代码不会自行进行额外的初始化或终止，只调用 `DllMain` 来传递消息。 如果 `DllMain` 从进程附加 `FALSE` 返回，则信号失败，`_DllMainCRTStartup` 再次调用 `DllMain` 并将 `DLL_PROCESS_DETACH` 作为*reason*参数传递，然后将经历终止过程的其余部分。

在 Visual Studio 中生成 Dll 时，VCRuntime 提供的默认入口点 `_DllMainCRTStartup` 会自动链接。 无需使用[/ENTRY （入口点符号）](reference/entry-entry-point-symbol.md)链接器选项为 DLL 指定入口点函数。

> [!NOTE]
> 尽管可以使用/ENTRY：链接器选项为 DLL 指定另一个入口点函数，但我们不建议这样做，因为入口点函数必须以相同的顺序复制 `_DllMainCRTStartup` 的所有内容。 VCRuntime 提供了一些函数，使你可以复制其行为。 例如，可以在进程附加上立即调用[__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md)以支持[/gs （缓冲区安全检查）](reference/gs-buffer-security-check.md)缓冲区检查选项。 可以调用 `_CRT_INIT` 函数，同时传递与入口点函数相同的参数，以执行 DLL 初始化或终止函数的其余部分。

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>初始化 DLL

您的 DLL 可能具有在您的 DLL 加载时必须执行的初始化代码。 为了你执行自己的 DLL 初始化和终止功能，`_DllMainCRTStartup` 会调用一个名为 `DllMain` 的函数，你可以提供此函数。 `DllMain` 必须具有 DLL 入口点所需的签名。 默认入口点函数 `_DllMainCRTStartup` 使用 Windows 传递的相同参数调用 `DllMain`。 默认情况下，如果未提供 `DllMain` 函数，Visual Studio 会为你提供一个，并将其链接在中，以便 `_DllMainCRTStartup` 始终有要调用的内容。 这意味着，如果不需要初始化 DLL，则在生成 DLL 时不需要执行任何特殊操作。

这是用于 `DllMain`的签名：

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

某些库会为你包装 `DllMain` 函数。 例如，在常规 MFC DLL 中，实现 `CWinApp` 对象的 `InitInstance` 并 `ExitInstance` 成员函数来执行 DLL 所需的初始化和终止。 有关更多详细信息，请参阅[初始化常规 MFC dll](#initializing-regular-dlls)部分。

> [!WARNING]
> 可以在 DLL 入口点中安全地执行的操作有很大的限制。 请参阅 `DllMain`中调用不安全的特定 Windows Api 的[一般最佳实践](/windows/win32/Dlls/dynamic-link-library-best-practices)。 如果需要但最简单的初始化，请在 DLL 的初始化函数中执行此操作。 您可以要求应用程序在 `DllMain` 运行之后以及在调用 DLL 中的任何其他函数之前调用初始化函数。

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>初始化普通（非 MFC） Dll

若要在使用 VCRuntime 提供的 `_DllMainCRTStartup` 入口点的普通（非 MFC） Dll 中执行自己的初始化，DLL 源代码必须包含名为 `DllMain`的函数。 以下代码显示了一个基本主干，其中显示了 `DllMain` 的定义可能如下所示：

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
> 较旧的 Windows SDK 文档指出，必须在链接器命令行上通过/ENTRY 选项指定 DLL 入口点函数的实际名称。 对于 Visual Studio，如果 `DllMain`入口点函数的名称，则无需使用/ENTRY 选项。 事实上，如果您使用/ENTRY 选项并将入口点函数命名为 `DllMain`以外的其他内容，则 CRT 不会正确初始化，除非您的入口点函数执行 `_DllMainCRTStartup` 所做的相同初始化调用。

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>初始化常规 MFC Dll

因为常规 MFC Dll 有 `CWinApp` 对象，所以它们应在 MFC 应用程序所在的同一位置执行其初始化和终止任务：在 DLL 的 `CWinApp`派生类的 `InitInstance` 和 `ExitInstance` 成员函数中。 由于 MFC 提供了一个由 `DLL_PROCESS_ATTACH` 和 `DLL_PROCESS_DETACH`的 `_DllMainCRTStartup` 调用的 `DllMain` 函数，因此不应编写您自己的 `DllMain` 函数。 在加载 DLL 时，MFC 提供的 `DllMain` 函数会调用 `InitInstance`，并在卸载 DLL 之前调用 `ExitInstance`。

常规 MFC DLL 可以通过在其 `InitInstance` 函数中调用[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)和[TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)来跟踪多个线程。 这些函数允许 DLL 跟踪线程特定的数据。

在动态链接到 MFC 的常规 MFC DLL 中，如果你使用的是任何 MFC OLE、MFC 数据库（或 DAO）或 MFC 套接字支持，则会在 MFCO 中自动链接调试 MFC 扩展 Dll*版本*d. MFCD*版本*d. 和 MFCN*版本*d.。 必须为在常规 MFC DLL 的 `CWinApp::InitInstance`中使用的每个 Dll 调用以下预定义的初始化函数之一。

|MFC 支持的类型|要调用的初始化函数|
|-------------------------|-------------------------------------|
|MFC OLE （MFCO*版本*d. .dll）|`AfxOleInitModule`|
|MFC 数据库（MFCD*版本*d. .dll）|`AfxDbInitModule`|
|MFC 套接字（MFCN*版本*d. .dll）|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>初始化 MFC 扩展 Dll

由于 MFC 扩展 Dll 没有 `CWinApp`派生的对象（如常规 MFC Dll），因此应将您的初始化代码和终止代码添加到 MFC DLL 向导生成的 `DllMain` 函数中。

向导为 MFC 扩展 Dll 提供了以下代码。 在代码中，`PROJNAME` 是项目名称的占位符。

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
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

在初始化过程中创建新的 `CDynLinkLibrary` 对象允许 MFC 扩展 DLL 将 `CRuntimeClass` 对象或资源导出到客户端应用程序。

如果要从一个或多个常规 MFC Dll 使用 MFC 扩展 DLL，则必须导出创建 `CDynLinkLibrary` 对象的初始化函数。 必须从使用 MFC 扩展 DLL 的每个常规 MFC Dll 调用该函数。 调用此初始化函数的适当位置是在使用任何 MFC 扩展 DLL 的已导出类或函数之前，在常规 MFC DLL 的 `CWinApp`派生对象的 `InitInstance` 成员函数中。

在 MFC DLL 向导生成的 `DllMain` 中，对 `AfxInitExtensionModule` 的调用将捕获模块的运行时类（`CRuntimeClass` 结构）以及在创建 `CDynLinkLibrary` 对象时要使用的对象工厂（`COleObjectFactory` 对象）。 你应检查 `AfxInitExtensionModule`的返回值;如果从 `AfxInitExtensionModule`返回零值，则从 `DllMain` 函数返回零。

如果 MFC 扩展 DLL 将显式链接到可执行文件（表示可执行文件调用 `AfxLoadLibrary` 链接到 DLL），则应在 `DLL_PROCESS_DETACH`上添加对 `AfxTermExtensionModule` 的调用。 当每个进程从 MFC 扩展 DLL 分离时，此函数允许 MFC 清除 MFC 扩展 DLL （这会在进程退出时发生，或者当 DLL 作为 `AfxFreeLibrary` 调用的结果而卸载时）。 如果 MFC 扩展 DLL 将隐式链接到应用程序，则不需要调用 `AfxTermExtensionModule`。

在释放 DLL 时，显式链接到 MFC 扩展 Dll 的应用程序必须调用 `AfxTermExtensionModule`。 如果应用程序使用多个线程，还应使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` （而不是 Win32 函数 `LoadLibrary` 和 `FreeLibrary`）。 使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 可确保加载并卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

由于 MFCx0 是在调用 `DllMain` 时完全初始化的，因此您可以在 `DllMain` 中分配内存和调用 MFC 函数（不同于16位版本的 MFC）。

扩展 Dll 可通过处理 `DllMain` 函数中的 `DLL_THREAD_ATTACH` 和 `DLL_THREAD_DETACH` 事例来处理多线程处理。 当线程附加到 DLL 或从 DLL 分离时，这些事例会传递到 `DllMain`。 如果在 DLL 附加时调用[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) ，则允许 DLL 维护附加到 dll 的每个线程的线程本地存储（TLS）索引。

请注意，头文件 Afxdllx 包含 MFC 扩展 Dll 中使用的结构的特殊定义，例如 `AFX_EXTENSION_MODULE` 和 `CDynLinkLibrary`的定义。 应将此标头文件包含在 MFC 扩展 DLL 中。

> [!NOTE]
>  务必在*pch* （Visual Studio 2017 及更早版本 *）中定义*或取消定义任何 `_AFX_NO_XXX` 宏，这一点很重要。 这些宏仅用于检查特定目标平台是否支持该功能。 您可以编写程序来检查这些宏（例如 `#ifndef _AFX_NO_OLE_SUPPORT`），但您的程序不应定义或取消定义这些宏。

用于处理多线程处理的示例初始化函数包含在 Windows SDK 的[动态链接库中的线程本地存储](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)中。 请注意，该示例包含一个名为 `LibMain`的入口点函数，但您应将此函数命名为 `DllMain` 以便它适用于 MFC 和 C 运行时库。

## <a name="see-also"></a>另请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)<br/>
[DllMain 入口点](/windows/win32/Dlls/dllmain)<br/>
[动态链接库最佳做法](/windows/win32/Dlls/dynamic-link-library-best-practices)
