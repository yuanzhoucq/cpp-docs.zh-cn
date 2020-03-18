---
title: MFC DLL 常见问题
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422822"
---
# <a name="dll-frequently-asked-questions"></a>DLL 常见问题

下面是有关 Dll 的一些常见问题（FAQ）。

- [MFC DLL 是否可以创建多个线程？](#mfc_multithreaded_1)

- [多线程应用程序是否可以在不同的线程中访问 MFC DLL？](#mfc_multithreaded_2)

- [MFC DLL 中是否有不能使用的 MFC 类或函数？](#mfc_prohibited_classes)

- [在加载时，应该使用哪种优化方法来改善客户端应用程序的性能？](#mfc_optimization)

- [我的常规 MFC DLL 中存在内存泄漏，但我的代码看起来很正常。如何查找内存泄漏？](#memory_leak)

## <a name="mfc_multithreaded_1"></a>MFC DLL 是否可以创建多个线程？

在初始化期间，MFC DLL 可以安全地创建多个线程，只要它使用 Win32 线程本地存储（TLS）函数（例如**TlsAlloc** ）分配线程本地存储。 但是，如果 MFC DLL 使用 **__declspec （线程）** 来分配线程本地存储，则必须将客户端应用程序隐式链接到 DLL。 如果客户端应用程序显式链接到 DLL，则对**LoadLibrary**的调用将无法成功加载 dll。 有关 Dll 中的线程本地变量的详细信息，请参阅[线程](../cpp/thread.md)。

在启动过程中创建新 MFC 线程的 MFC DLL 将在应用程序加载时停止响应。 这包括在创建线程时，只要调用 `AfxBeginThread` 或内部 `CWinThread::CreateThread`：

- 常规 MFC DLL 中 `CWinApp`派生对象的 `InitInstance`。

- 在常规 MFC DLL 中提供的 `DllMain` 或**RawDllMain**函数。

- MFC 扩展 DLL 中提供的 `DllMain` 或**RawDllMain**函数。

## <a name="mfc_multithreaded_2"></a>多线程应用程序是否可以在不同的线程中访问 MFC DLL？

多线程应用程序可以访问动态链接到不同线程中 MFC 和 MFC 扩展 Dll 的常规 MFC Dll。 应用程序可以从应用程序中创建的多个线程访问静态链接到 MFC 的规则 MFC Dll。

## <a name="mfc_prohibited_classes"></a>MFC DLL 中是否有不能使用的 MFC 类或函数？

扩展 Dll 使用客户端应用程序的 `CWinApp`派生类。 它们不能有其自己的 `CWinApp`派生类。

与 MFC 应用程序一样，普通 MFC Dll 必须具有 `CWinApp`派生的类和该应用程序类的单个对象。 与应用程序的 `CWinApp` 对象不同，DLL 的 `CWinApp` 对象没有主消息泵。

请注意，由于 `CWinApp::Run` 机制不适用于 DLL，因此该应用程序拥有主消息泵。 如果 DLL 打开无模式对话框或具有其自己的主框架窗口，则应用程序的主消息泵必须调用 DLL 导出的例程，后者又会调用 DLL 的应用程序对象的 `CWinApp::PreTranslateMessage` 成员函数。

## <a name="mfc_optimization"></a>在加载时，我应该使用什么优化方法来&#39;改善客户端应用程序的性能？

如果 DLL 是静态链接到 MFC 的常规 MFC DLL，则将其更改为动态链接到 MFC 的常规 MFC DLL 可减少文件大小。

如果 DLL 具有大量导出函数，请使用 .def 文件导出函数（而不是使用 **__declspec （dllexport）** ），并对每个导出的函数使用 .Def 文件[NONAME 属性](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。 NONAME 特性仅导致序号值而不是在 DLL 的导出表中存储的函数名称，这将减小文件大小。

在应用程序加载时，将加载隐式链接到应用程序的 Dll。 若要在加载时提高性能，请尝试将 DLL 分成不同的 Dll。 将调用应用程序加载到一个 DLL 中后立即需要的所有函数都放入，并将调用应用程序隐式链接到该 DLL。 将调用应用程序不需要的其他函数直接放入另一个 DLL，并使应用程序显式链接到该 DLL。 有关详细信息，请参阅将[可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。

## <a name="memory_leak"></a>我&#39;的常规 MFC DLL 中存在内存泄漏，但我的代码看起来很正常。 如何查找内存泄漏？

内存泄漏的一个可能原因是 MFC 创建在消息处理程序函数内使用的临时对象。 在 MFC 应用程序中，这些临时对象会自动在处理消息之间调用的 `CWinApp::OnIdle()` 函数中清除。 但在 MFC 动态链接库（Dll）中，不会自动调用 `OnIdle()` 函数。 因此，不会自动清理临时对象。 若要清理临时对象，DLL 必须定期显式调用 `OnIdle(1)`。

## <a name="see-also"></a>另请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)
