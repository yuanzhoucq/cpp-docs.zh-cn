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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335662"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>DLL 和 Visual C++ 运行时库行为

默认情况下，使用 Visual Studio 构建动态链接库 （DLL） 时，链接器包括可视C++运行时库 （VCRuntime）。 VCRuntime 包含初始化和终止 C/C++可执行文件所需的代码。 当链接到 DLL 时，VCRuntime 代码提供一个内部 DLL 入口`_DllMainCRTStartup`点函数，该函数调用该函数处理 Windows OS 消息到 DLL 以附加到进程或线程或从进程或线程分离。 该`_DllMainCRTStartup`函数执行基本任务，如堆栈缓冲区安全设置、C 运行时库 （CRT） 初始化和终止，以及对静态和全局对象的构造函数和析构函数的调用。 `_DllMainCRTStartup`还调用其他库（如 WinRT、MFC 和 ATL）的挂钩函数来执行自己的初始化和终止。 如果没有此初始化，CRT 和其他库以及静态变量将处于未初始化状态。 无论您的 DLL 使用静态链接的 CRT 还是动态链接的 CRT DLL，都调用相同的 VCRuntime 内部初始化和终止例程。

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>默认 DLL 入口点_DllMainCRTStartup

在 Windows 中，所有 DLL 都可以包含一个可选的入口`DllMain`点函数，通常称为 ，该函数同时调用初始化和终止。 这使您有机会根据需要分配或释放其他资源。 Windows 在四种情况下调用入口点功能：进程附加、进程分离、线程连接和线程分离。 当 DLL 加载到进程地址空间时，或者在加载使用它的应用程序时，或者当应用程序在运行时请求 DLL 时，操作系统将创建 DLL 数据的单独副本。 这称为*进程附加*。 当 DLL 加载的过程创建新线程时，将发生*线程附加*。 *线程分离*在线程终止时发生，*进程分离*是不再需要 DLL 并由应用程序释放时发生的。 操作系统对每个事件分别调用 DLL 入口点，传递每个事件类型的*推理*参数。 例如，操作系统作为*原因*参数`DLL_PROCESS_ATTACH`发送到信号进程附加。

VCRuntime 库提供一个入口点函数，`_DllMainCRTStartup`用于处理默认初始化和终止操作。 在进程附加时，`_DllMainCRTStartup`函数设置缓冲区安全检查，初始化 CRT 和其他库，初始化运行时类型信息，初始化和调用静态和非本地数据的构造函数，初始化线程本地存储，为每个附加增加内部静态计数器，然后调用用户或库提供的`DllMain`。 在进程分离时，函数将反向执行这些步骤。 它调用`DllMain`，递减内部计数器，调用析构函数，调用CRT终止函数和注册`atexit`函数，并通知任何其他库的终止。 当附件计数器为零时，函数将返回`FALSE`以向 Windows 指示可以卸载 DLL。 在`_DllMainCRTStartup`线程连接和线程分离期间，还会调用该函数。 在这些情况下，VCRuntime 代码本身不会执行额外的初始化或终止，只是调用`DllMain`传递消息。 如果`DllMain`从`FALSE`进程附加返回、发出信号失败、`_DllMainCRTStartup`再次`DllMain`调用并作为`DLL_PROCESS_DETACH`*原因*参数传递，则通过终止过程的其余部分。

在 Visual Studio 中构建 DLL`_DllMainCRTStartup`时，VCRuntime 提供的默认入口点将自动链接在其中。 无需使用[/ENTRY（入口点符号）](reference/entry-entry-point-symbol.md)链接器选项为 DLL 指定入口点函数。

> [!NOTE]
> 虽然可以使用 /ENTRY： 链接器选项为 DLL 指定另一个入口点函数，但我们不推荐它，因为入口点函数必须按相同的顺序复制所有`_DllMainCRTStartup`执行该功能的功能。 VCRuntime 提供允许您复制其行为的函数。 例如，您可以在进程附加时立即调用[__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md)以支持[/GS（缓冲区安全检查）](reference/gs-buffer-security-check.md)缓冲区检查选项。 您可以调用`_CRT_INIT`函数，传递与入口点函数相同的参数，以执行 DLL 初始化或终止函数的其余部分。

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>初始化 DLL

您的 DLL 可能具有初始化代码，这些代码必须在加载 DLL 时执行。 为了执行自己的 DLL 初始化和终止函数，`_DllMainCRTStartup`调用一个可以提供的函数。 `DllMain` 您必须`DllMain`具有 DLL 入口点所需的签名。 默认入口点函数`_DllMainCRTStartup`使用`DllMain`Windows 传递的相同参数调用。 默认情况下，如果您不提供函数，Visual `DllMain` Studio 会为您提供一个函数并将其链接在其中，`_DllMainCRTStartup`以便始终具有可调用的内容。 这意味着，如果您不需要初始化 DLL，则构建 DLL 时无需执行任何特别操作。

这是用于 的签名`DllMain`：

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

某些库为您包装函数`DllMain`。 例如，在常规 MFC DLL 中，`CWinApp`实现对象的`InitInstance`和`ExitInstance`成员函数，以执行 DLL 所需的初始化和终止。 有关详细信息，请参阅[初始化常规 MFC DLL](#initializing-regular-dlls)部分。

> [!WARNING]
> 在 DLL 入口点中可以安全地执行哪些操作有显著限制。 有关不安全的特定 Windows API，`DllMain`请参阅[常规最佳做法](/windows/win32/Dlls/dynamic-link-library-best-practices)。 如果您需要任何内容，但最简单的初始化，然后在 DLL 的初始化函数中执行此操作。 您可以要求应用程序在运行后`DllMain`和在 DLL 中调用任何其他函数之前调用初始化函数。

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>初始化普通（非 MFC） DLL

要在使用 VCRuntime 提供`_DllMainCRTStartup`的入口点的普通（非 MFC） DLL 中执行自己的初始化，DLL 源代码必须包含名为 的`DllMain`函数。 以下代码提供了一个基本骨架，显示其`DllMain`定义可能是什么样子：

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
> 较旧的 Windows SDK 文档指出，必须在带有 /ENTRY 选项的链接器命令行上指定 DLL 入口点函数的实际名称。 使用 Visual Studio，如果入口点函数的名称为`DllMain`，则无需使用 /ENTRY 选项。 事实上，如果您使用 /ENTRY 选项并命名入口点函数，则`DllMain`CRT 不会正确初始化，除非您的入口点函数`_DllMainCRTStartup`发出相同的初始化调用。

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>初始化常规 MFC DLL

由于常规 MFC DLL`CWinApp`具有对象，因此它们应在与 MFC 应用程序相同的位置执行初始化和终止任务：在`InitInstance`DLL`ExitInstance``CWinApp`派生类的 和 成员函数中。 因为 MFC`DllMain`提供`_DllMainCRTStartup`由`DLL_PROCESS_ATTACH`和`DLL_PROCESS_DETACH`调用的函数，因此不应编写自己的`DllMain`函数。 在加载 DLL`DllMain`并在`InitInstance`卸载 DLL 之前调用`ExitInstance`MFC 提供的函数调用。

常规 MFC DLL 可以通过在其`InitInstance`函数中调用[TlsAlloc 和 TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)来跟踪多个线程。 [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) 这些函数允许 DLL 跟踪特定于线程的数据。

在动态链接到 MFC 的常规 MFC DLL 中，如果您分别使用任何 MFC OLE、MFC 数据库（或 DAO）或 MFC 插槽支持，则调试 MFC 扩展 DL MFCO*版本*D.dll、MFCD*版本*D.dll 和 MFCN*版本*D.dll（*其中版本*是版本号）将自动链接。 您必须为常规 MFC DLL 中正在使用的每个 DLL 调用以下预定义的初始化函数之一`CWinApp::InitInstance`。

|MFC 支持的类型|要调用的初始化函数|
|-------------------------|-------------------------------------|
|MFC OLE（MFCO*版本*D.dll）|`AfxOleInitModule`|
|MFC 数据库（MFCD*版本*D.dll）|`AfxDbInitModule`|
|MFC 插座（MFCN*版本*D.dll）|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>初始化 MFC 扩展 DLL

由于 MFC 扩展 DLL`CWinApp`没有派生对象（常规 MFC DLL 也相同），因此应将初始化和终止码添加到`DllMain`MFC DLL 向导生成的函数中。

该向导为 MFC 扩展 DLL 提供以下代码。 在代码中，`PROJNAME`是项目名称的占位符。

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

在初始化`CDynLinkLibrary`期间创建新对象允许 MFC 扩展 DLL`CRuntimeClass`将对象或资源导出到客户端应用程序。

如果要使用来自一个或多个常规 MFC DLL 的 MFC 扩展 DLL，则必须导出创建`CDynLinkLibrary`对象的初始化函数。 该函数必须从使用 MFC 扩展 DLL 的每个常规 MFC DLL 中调用。 在使用任何 MFC 扩展 DLL`InitInstance`导出的类或函数之前，常规 MFC `CWinApp`DLL 派生对象的成员函数中可以调用此初始化函数的适当位置。

在`DllMain`MFC DLL 向导生成的 中，用于`AfxInitExtensionModule`捕获模块的运行时类（`CRuntimeClass`结构）及其对象工厂（`COleObjectFactory`对象）的调用，用于创建`CDynLinkLibrary`对象时。 应检查 的`AfxInitExtensionModule`返回值 。如果从`AfxInitExtensionModule`返回零值，则从`DllMain`返回函数返回零。

如果您的 MFC 分机 DLL 将显式链接到可执行文件（表示可执行调用`AfxLoadLibrary`链接到 DLL），则应向`AfxTermExtensionModule`上`DLL_PROCESS_DETACH`添加调用。 此功能允许 MFC 在每个进程从 MFC 分机 DLL 分离时清理 MFC 分机 DLL（当进程退出或由于`AfxFreeLibrary`调用而卸载 DLL 时发生）。 如果您的 MFC 分机 DLL 将隐式链接到应用程序，则`AfxTermExtensionModule`不需要调用 。

显式链接到 MFC 扩展 DLL 的应用程序在`AfxTermExtensionModule`释放 DLL 时必须调用。 如果应用程序使用多个`AfxLoadLibrary`线程`AfxFreeLibrary`，它们还应使用 和 （`LoadLibrary`而不是`FreeLibrary`Win32 函数 和 ）。 使用`AfxLoadLibrary``AfxFreeLibrary`并确保在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

由于 MFCx0.dll 在调用时`DllMain`已完全初始化，因此您可以在其中`DllMain`分配内存并调用 MFC 函数（与 16 位版本的 MFC 不同）。

扩展 DLL 可以通过处理`DLL_THREAD_ATTACH``DLL_THREAD_DETACH``DllMain`函数中的 和 案例来处理多线程。 `DllMain`当线程从 DLL 连接和分离时，这些情况将传递到。 在附加 DLL 时调用[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)允许 DLL 维护附加到 DLL 的每个线程的线程本地存储 （TLS） 索引。

请注意，标头文件 Afxdllx.h 包含 MFC 扩展 DLL 中使用的结构的特殊定义，例如 和`AFX_EXTENSION_MODULE``CDynLinkLibrary`的定义。 您应该在 MFC 扩展名 DLL 中包括此标头文件。

> [!NOTE]
> 重要的是，您既不定义也不定义`_AFX_NO_XXX`*pch.h（Visual* Studio 2017 和更早版本中的*stdafx.h）* 中的任何宏。 这些宏的存在仅用于检查特定目标平台是否支持该功能。 可以编写程序来检查这些宏（例如`#ifndef _AFX_NO_OLE_SUPPORT`），但程序绝不应定义或取消定义这些宏。

处理多线程的示例初始化功能包含在 Windows SDK[中的动态链接库中使用线程本地存储](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)中。 请注意，该示例包含一个称为 的`LibMain`切入点函数，但应命名此函数`DllMain`，以便它适用于 MFC 和 C 运行时库。

## <a name="see-also"></a>另请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)<br/>
[Dll主入口点](/windows/win32/Dlls/dllmain)<br/>
[动态链接库最佳实践](/windows/win32/Dlls/dynamic-link-library-best-practices)
