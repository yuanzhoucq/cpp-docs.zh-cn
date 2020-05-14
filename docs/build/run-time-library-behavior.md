---
title: DLL 和 Visual C++ 运行时库行为
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
ms.openlocfilehash: 2f2ffb13e6a80b144298bbf8cd76b5666a10b4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335662"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>DLL 和 Visual C++ 运行时库行为

默认情况下，当使用 Visual Studio 生成动态链接库 (DLL) 时，链接器就会包括 Visual C++ 运行时库 (VCRuntime)。 VCRuntime 包含初始化和终止 C/C++ 可执行文件所需的代码。 当链接到 DLL 时，VCRuntime 代码提供名为 `_DllMainCRTStartup` 的内部 DLL 入口点函数，该函数处理 Windows OS 到 DLL 的消息，以便附加到进程或线程或从进程或线程分离。 `_DllMainCRTStartup` 函数执行基本任务，例如设置堆栈缓冲区安全性，初始化和终止 C 运行时库 (CRT)，以及调用静态和全局对象的构造函数和析构函数。 `_DllMainCRTStartup` 还为其他库（如 WinRT、MFC 和 ATL）调用挂钩函数来执行其自己的初始化和终止操作。 如果没有这种初始化，CRT 和其他库以及静态变量将处于未初始化状态。 无论 DLL 使用静态链接的 CRT 还是动态链接的 CRT DLL，都会调用相同的 VCRuntime 内部初始化和终止例程。

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>默认 DLL 入口点 _DllMainCRTStartup

在 Windows 中，所有 DLL 都可以包含一个可选的入口点函数，通常称为 `DllMain`，该函数用于初始化和终止操作。 这使可以根据需要分配或释放额外的资源。 Windows 会在四种情况下调用入口点函数：进程附加、进程分离、线程附加和线程分离。 将 DLL 加载到进程地址空间中时，或在加载使用它的应用程序时，或当应用程序在运行时请求 DLL 时，操作系统会创建 DLL 数据的单独副本。 这称为“进程附加”  。 加载 DLL 的进程创建新线程时发生“线程附加”  。 线程终止时发生“线程分离”，如果不再需要 DLL 并由应用程序释放 DLL，则称为“进程分离”   。 操作系统为每个事件单独调用 DLL 入口点，并为每个事件类型传递“原因”参数  。 例如，OS 将 `DLL_PROCESS_ATTACH` 作为原因参数发送给信号进程附加  。

VCRuntime 库提供一个名为 `_DllMainCRTStartup` 的入口点函数来处理默认的初始化和终止操作。 在进程附加时，`_DllMainCRTStartup` 函数设置缓冲区安全检查，初始化 CRT 和其他库，初始化运行时类型信息，初始化和调用静态和非本地数据的构造函数，初始化线程本地存储，为每个附加增加内部静态计数器，然后调用提供 `DllMain` 的用户或库。 在进程分离时，函数将反向执行这些步骤。 它会调用 `DllMain`，递减内部计数器，调用析构函数，调用 CRT 终止函数和注册的 `atexit` 函数，并通知任何其他库终止操作。 当附件计数器变为零时，此函数返回 `FALSE` 以指示 Windows 可以卸载 DLL。 `_DllMainCRTStartup` 函数也在线程附加和线程分离期间进行调用。 在这些情况下，VCRuntime 代码本身不进行额外的初始化或终止，只调用 `DllMain` 来传递消息。 如果 `DllMain` 从进程附加返回 `FALSE`并出现信号故障，`_DllMainCRTStartup` 将再次调用 `DllMain`，并将 `DLL_PROCESS_DETACH` 作为“原因”参数传递，然后继续完成终止进程的其余部分  。

在 Visual Studio 中生成 DLL 时，VCRuntime 提供的默认入口点 `_DllMainCRTStartup` 将自动进行链接。 不需要使用 [/ENTRY（入口点符号）](reference/entry-entry-point-symbol.md)链接器选项为 DLL 指定入口点函数。

> [!NOTE]
> 虽然可以使用 /ENTRY: linker 选项为 DLL 指定另一个入口点函数，但我们不建议这样做，因为入口点函数必须按照相同的顺序复制 `_DllMainCRTStartup` 所做的所有操作。 VCRuntime 提供了允许复制其行为的函数。 例如，可以在进程附加时立即调用 [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md)，以支持 [/GS（缓冲区安全检查）](reference/gs-buffer-security-check.md)缓冲区检查选项。 可以调用 `_CRT_INIT` 函数，传递与入口点函数相同的参数，以执行其余的 DLL 初始化或终止函数操作。

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>初始化 DLL

DLL 可能有初始化代码，这些代码必须在加载 DLL 时执行。 为了执行自己的 DLL 初始化和终止函数，`_DllMainCRTStartup` 会调用 `DllMain` 函数，你可提供此函数。 `DllMain` 必须具有 DLL 入口点所需的签名。 默认入口点函数 `_DllMainCRTStartup` 使用 Windows 传递的相同参数调用 `DllMain`。 默认情况下，如果未提供 `DllMain` 函数，Visual Studio 将为你提供一个函数并链接到它，以便 `_DllMainCRTStartup` 始终可以调用某些内容。 这意味着如果你不需要初始化 DLL，那么在生成 DLL 时就不需要执行任何特殊操作。

这是用于 `DllMain` 的签名：

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

某些库会为你包装 `DllMain` 函数。 例如，在规则 MFC DLL 中，实现 `CWinApp` 对象的 `InitInstance` 和 `ExitInstance` 成员函数可以执行 DLL 所需的初始化和终止操作。 有关详细信息，请参阅[初始化规则 MFC DLL](#initializing-regular-dlls) 部分。

> [!WARNING]
> 对于在 DLL 入口点中可以安全地执行的操作，通常存在很大限制。 请参阅[一般最佳做法](/windows/win32/Dlls/dynamic-link-library-best-practices)，了解调用 `DllMain` 时不安全的特定 Windows API。 如果需要进行复杂的初始化，可在 DLL 的初始化函数中完成。 你可以要求应用程序在运行 `DllMain` 之后和调用 DLL 中的任何其他函数之前调用初始化函数。

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>初始化普通（非 MFC）DLL

若要在使用 VCRuntime 提供的 `_DllMainCRTStartup` 入口点的普通（非 MFC）DLL 中执行自己的初始化，DLL 源代码必须包含名为 `DllMain` 的函数。 以下代码提供了一个基本框架，显示 `DllMain` 的定义可能如下所示：

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
> 旧的 Windows SDK 文档说明，DLL 入口点函数的实际名称必须在带有 /ENTRY 选项的链接器命令行中指定。 对于 Visual Studio，如果入口点函数的名称是 `DllMain`，则不需要使用 /ENTRY 选项。 事实上，如果使用 /ENTRY 选项并将入口点函数命名为 `DllMain` 以外的其他名称，则除非入口点函数执行与 `_DllMainCRTStartup` 相同的初始化调用，否则 CRT 不会正确进行初始化。

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>初始化规则 MFC DLL

由于规则 MFC DLL 包含 `CWinApp` 对象，因此它们应该在与 MFC 应用程序相同的位置执行初始化和终止任务：在 DLL 的 `CWinApp` 派生类的 `InitInstance` 和 `ExitInstance` 成员函数中。 MFC 提供了由 `_DllMainCRTStartup` 为 `DLL_PROCESS_ATTACH` 和 `DLL_PROCESS_DETACH` 调用的 `DllMain` 函数，因此不应编写自己的 `DllMain` 函数。 MFC 提供的 `DllMain` 函数会在加载 DLL 时调用 `InitInstance`，在卸载 DLL 之前调用 `ExitInstance`。

规则 MFC DLL 可以通过在其 `InitInstance` 函数中调用 [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) 和 [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) 来跟踪多个线程。 这些函数允许 DLL 跟踪特定于线程的数据。

在动态链接到 MFC 的规则 MFC DLL 中，如果使用任何 MFC OLE、MFC 数据库（或 DAO）或 MFC 套接字支持，则分别会自动链接调试 MFC 扩展 DLL MFCO version D.dll、MFCD version D.dll 和 MFCN version D.dll（其中 version 是版本号）     。 必须为在规则 MFC DLL 的 `CWinApp::InitInstance` 中使用的每个 DLL 调用以下预定义初始化函数之一。

|MFC 支持的类型|要调用的初始化函数|
|-------------------------|-------------------------------------|
|MFC OLE (MFCOversionD.dll) |`AfxOleInitModule`|
|MFC 数据库 (MFCOversionD.dll) |`AfxDbInitModule`|
|MFC 套接字 (MFCOversionD.dll) |`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>初始化 MFC 扩展 DLL

由于 MFC 扩展 DLL 没有 `CWinApp` 派生对象（如规则 MFC DLL），因此应将初始化和终止代码添加到 MFC DLL 向导生成的 `DllMain` 函数中。

向导为 MFC 扩展 DLL 提供以下代码。 在代码中，`PROJNAME` 是项目名称的占位符。

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

在初始化期间创建新的 `CDynLinkLibrary` 对象允许 MFC 扩展 DLL 将 `CRuntimeClass` 对象或资源导出到客户端应用程序。

如果要从一个或多个规则 MFC DLL 使用 MFC 扩展 DLL，则必须导出创建 `CDynLinkLibrary` 对象的初始化函数。 必须从使用 MFC 扩展 DLL 的每个规则 MFC DLL 调用该函数。 在使用任何 MFC 扩展 DLL 导出的类或函数之前，调用此初始化函数的适当位置是规则 MFC DLL 的 `CWinApp` 派生对象的 `InitInstance` 成员函数。

在 MFC DLL 向导生成的 `DllMain` 中，对 `AfxInitExtensionModule` 的调用捕获模块的运行时类（`CRuntimeClass` 结构）及其对象工厂（`COleObjectFactory` 对象），以便在创建 `CDynLinkLibrary` 对象时使用。 应检查 `AfxInitExtensionModule` 的返回值；如果从 `AfxInitExtensionModule` 返回零值，则从 `DllMain` 函数返回零。

如果 MFC 扩展 DLL 将显式链接到可执行文件（即链接到 DLL 的可执行调用 `AfxLoadLibrary`），则应在 `DLL_PROCESS_DETACH` 上添加对 `AfxTermExtensionModule` 的调用。 这个函数允许 MFC 在每个进程从 MFC 扩展 DLL 分离时清理 MFC 扩展 DLL（进程退出时或 DLL 由于 `AfxFreeLibrary` 调用而卸载时发生）。 如果 MFC 扩展 DLL 将隐式链接到应用程序，则不需要调用 `AfxTermExtensionModule`。

显式链接到 MFC 扩展 DLL 的应用程序在释放 DLL 时必须调用 `AfxTermExtensionModule`。 如果应用程序使用多个线程，它们还应使用 `AfxLoadLibrary` 和 `AfxFreeLibrary`（而不是 Win32 函数 `LoadLibrary` 和 `FreeLibrary`）。 使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 可以确保在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

由于 MFCx0.dll 在调用 `DllMain` 时已完全初始化，因此可以在 `DllMain` 内分配内存并调用 MFC 函数（与 16 位版本的 MFC 不同）。

扩展 DLL 可通过处理 `DllMain` 函数中的 `DLL_THREAD_ATTACH` 和 `DLL_THREAD_DETACH` 案例来处理多线程。 当线程附加到 DLL 并从 DLL 分离时，这些案例将传递给 `DllMain`。 在附加 DLL 时调用 [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) 允许 DLL 为附加到 DLL 的每个线程维护线程本地存储 (TLS) 索引。

请注意，头文件 Afxdllx.h 包含 MFC 扩展 DLL 中使用的结构的特殊定义，例如 `AFX_EXTENSION_MODULE` 和 `CDynLinkLibrary` 的定义。 应在 MFC 扩展 DLL 中包含此头文件。

> [!NOTE]
> 在 pch.h（Visual Studio 2017 及更早版本中为 stdafx.h）中，既不定义也不取消定义任何 `_AFX_NO_XXX` 宏，这点很重要   。 这些宏仅用于检查特定目标平台是否支持该功能。 可编写程序来检查这些宏（例如 `#ifndef _AFX_NO_OLE_SUPPORT`），但程序不应定义或取消定义这些宏。

有关处理多线程的函数初始化示例，请参阅“Windows SDK”中的[在动态链接库中使用线程本地存储](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)。 请注意，示例包含一个名为 `LibMain` 的入口点函数，但你应将此函数命名为 `DllMain`，以便它与 MFC 和 C 运行时库一起使用。

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)<br/>
[DllMain 入口点](/windows/win32/Dlls/dllmain)<br/>
[动态链接库最佳做法](/windows/win32/Dlls/dynamic-link-library-best-practices)
