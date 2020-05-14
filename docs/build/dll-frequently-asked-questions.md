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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422822"
---
# <a name="dll-frequently-asked-questions"></a>DLL 常见问题

以下是一些有关 DLL 的常见问题解答 (FAQ)。

- [MFC DLL 是否可以创建多线程？](#mfc_multithreaded_1)

- [多线程应用程序是否可以通过不同的线程访问 MFC DLL？](#mfc_multithreaded_2)

- [是否存在无法用于 MFC DLL 的 MFC 类或函数？](#mfc_prohibited_classes)

- [加载时应使用哪些优化技术来提高客户端应用程序的性能？](#mfc_optimization)

- [规则 MFC DLL 中有内存泄漏，但代码看起来很正常。如何找到内存泄漏？](#memory_leak)

## <a name="can-an-mfc-dll-create-multiple-threads"></a><a name="mfc_multithreaded_1"></a> MFC DLL 是否可以创建多线程？

除了在初始化过程中，只要 MFC DLL 使用 TlsAlloc 这样的 Win32 线程本地存储 (TLS) 函数来分配线程本地存储，就可以安全地创建多线程  。 但是，如果 MFC DLL 使用 __declspec(thread) 分配线程本地存储，客户端应用程序必须隐式链接到 DLL  。 如果客户端应用程序显式链接到 DLL，对 LoadLibrary 的调用将不会成功加载此 DLL。  。 有关 DLL 中的线程局部变量的详细信息，请参阅[线程](../cpp/thread.md)。

启动期间创建新的 MFC 线程的 MFC DLL 在由应用程序加载时将停止响应。 每当在下列对象内部通过调用 `AfxBeginThread` 和 `CWinThread::CreateThread` 创建线程时，就会发生这种情况：

- 规则 MFC DLL 中的 `CWinApp` 派生对象的 `InitInstance`。

- 规则 MFC DLL 中提供的 `DllMain` 或 RawDllMain 函数  。

- MFC 扩展 DLL 中提供的 `DllMain` 或 RawDllMain 函数  。

## <a name="can-a-multithreaded-application-access-an-mfc-dll-in-different-threads"></a><a name="mfc_multithreaded_2"></a> 多线程应用程序是否可以通过不同的线程访问 MFC DLL？

多线程应用程序可从不同线程访问动态链接到 MFC 和 MFC 扩展 DLL 的规则 MFC DLL。 单个应用程序可从该应用程序中创建的多线程访问静态链接到 MFC 的 MFC DLL。

## <a name="are-there-any-mfc-classes-or-functions-that-cannot-be-used-in-an-mfc-dll"></a><a name="mfc_prohibited_classes"></a> 是否存在无法用于 MFC DLL 的 MFC 类或函数？

扩展 DLL 使用客户端应用程序的 `CWinApp` 派生类。 它们不能有其自己的 `CWinApp` 派生类。

与 MFC 应用程序一样，规则 MFC DLL 必须具有 `CWinApp` 派生类和该应用程序类的单个对象。 与应用程序的 `CWinApp` 对象不同，DLL 的 `CWinApp` 对象没有主消息泵。

请注意，`CWinApp::Run` 机制不适用于 DLL，因为应用程序拥有主消息泵。 如果 DLL 打开无模式对话框或具有其自己的主框架窗口，则应用程序的主消息泵必须调用由 DLL 导出的例程，该例程又会调用 DLL 的应用程序对象的 `CWinApp::PreTranslateMessage` 成员函数。

## <a name="what-optimization-techniques-should-i-use-to-improve-the-client-application39s-performance-when-loading"></a><a name="mfc_optimization"></a> 加载时应使用哪些优化技术来提高客户端应用程序的性能？

如果 DLL 是静态链接到 MFC 的规则 MFC DLL，则将其更改为动态链接到 MFC 的规则 MFC DLL 可减小文件大小。

如果 DLL 具有大量导出的函数，请使用 .def 文件导出函数（而不是使用 __declspec(dllexport)），并在每个导出的函数上使用 .def 文件 [NONAME 属性](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  。 NONAME 属性仅将序号值而不是函数名存储在 DLL 的导出表中，这将减小文件大小。

加载应用程序时，同时将加载隐式链接到应用程序的 DLL。 为了提高加载时的性能，可尝试将 DLL 划分为不同的 DLL。 在加载到一个 DLL 后立即将调用应用程序需要的所有函数放入其中，并使调用应用程序隐式链接到该 DLL。 将调用应用程序不需要的其他函数直接放入另一个 DLL 中，并使应用程序显式链接到该 DLL。 有关详细信息，请参阅[将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。

## <a name="there39s-a-memory-leak-in-my-regular-mfc-dll-but-my-code-looks-fine-how-can-i-find-the-memory-leak"></a><a name="memory_leak"></a> 规则 MFC DLL 中有内存泄漏，但代码看起来很正常。 如何找到内存泄漏？

内存泄漏的一个可能原因是 MFC 创建了在消息处理程序函数中使用的临时对象。 在 MFC 应用程序中，这些临时对象会在处理消息期间调用的 `CWinApp::OnIdle()` 函数中自动进行清理。 但在 MFC 动态链接库 (DLL) 中，不会调用 `OnIdle()` 函数。 因此，临时对象不会自动进行清理。 要清理临时对象，DLL 必须定期显式调用 `OnIdle(1)`。

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)
