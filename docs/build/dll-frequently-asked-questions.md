---
title: MFC DLL 常见问题
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 33a0c9dd1abbfb9375ce1aef53fd152a521ac97d
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "57821932"
---
# <a name="dll-frequently-asked-questions"></a>DLL 常见问题

以下是一些常见问题 (FAQ) 有关的 Dll。

- [非 MFC DLL 是否可以创建多个线程？](#mfc_multithreaded_1)

- [多线程应用程序可以访问在不同线程中非 MFC DLL？](#mfc_multithreaded_2)

- [是否有任何 MFC 类或函数不能用于非 MFC DLL？](#mfc_prohibited_classes)

- [我应该使用哪些优化技术来提高时加载的客户端应用程序的性能？](#mfc_optimization)

- [在规则 MFC DLL，内存泄漏，但我的代码看起来很正常。如何查找内存泄漏？](#memory_leak)

## <a name="mfc_multithreaded_1"></a> 非 MFC DLL 是否可以创建多个线程？

不同的是在初始化期间，MFC DLL 可以安全地创建多个线程，只要它使用本地存储 (TLS) 之类的函数的 Win32 线程**TlsAlloc**分配线程本地存储区。 但是，如果使用非 MFC DLL **__declspec （thread)** 分配线程本地存储区，客户端应用程序必须隐式链接到 DLL。 如果客户端应用程序显式链接到 DLL 时，调用**LoadLibrary**则无法成功加载 DLL。 有关 Dll 中的线程本地变量的详细信息，请参阅[线程](../cpp/thread.md)。

在启动期间创建一个新的 MFC 线程非 MFC DLL 将停止响应的应用程序加载时。 这包括通过调用创建一个线程只要`AfxBeginThread`或`CWinThread::CreateThread`内：

- `InitInstance`的`CWinApp`-派生的对象的规则 MFC DLL 中。

- 提供`DllMain`或**RawDllMain**函数的规则 MFC DLL 中。

- 提供`DllMain`或**RawDllMain** MFC 扩展 DLL 中的函数。

## <a name="mfc_multithreaded_2"></a> 多线程应用程序可以访问在不同线程中非 MFC DLL？

多线程应用程序可以访问来自不同线程动态链接到 MFC 的规则 MFC Dll 和 MFC 扩展 Dll。 和截至 Visual c + + 4.2 版开始，应用程序可以访问从应用程序中创建的多个线程，静态链接到 MFC 的规则 MFC Dll。

之前的版本 4.2，只有一个外部线程可以将附加到静态链接到 MFC 的规则 MFC DLL。

请注意，术语 USRDLL 不再使用 Visual c + + 文档中。 静态链接到 MFC 的规则 MFC DLL 具有 usrdll 相同的特性。

## <a name="mfc_prohibited_classes"></a> 是否有任何 MFC 类或函数不能用于非 MFC DLL？

扩展 Dll 使用`CWinApp`的派生类的客户端应用程序。 它们不得具有其自己`CWinApp`-派生的类。

规则 MFC Dll 必须具有`CWinApp`-派生的类以及该类应用程序的单个对象的 MFC 应用程序一样。 与不同`CWinApp`对象的应用程序， `CWinApp` DLL 的对象不具有主消息泵。

请注意，由于`CWinApp::Run`机制不适用于 DLL、 应用程序拥有主消息泵。 如果 DLL 打开无模式对话框或有其自己的主框架窗口，应用程序的主消息泵必须调用 DLL，后者又调用导出的例程`CWinApp::PreTranslateMessage`DLL 的应用程序对象的成员函数。

## <a name="mfc_optimization"></a> 哪些优化技术是否应使用来提高客户端应用程序&#39;s 加载时的性能？

如果您的 DLL 是以静态方式链接到 MFC，更改为正则表达式的规则 MFC DLL 动态链接到 MFC 的 MFC DLL 可减小文件大小。

如果 DLL 具有大量导出函数，使用.def 文件导出的函数 (而不是使用 **__declspec （dllexport)**)，并使用.def 文件[NONAME 特性](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)上每个导出的函数。 NONAME 特性会导致只有序号值而不是函数名称存储在 DLL 的导出表中，这会减少文件大小。

应用程序加载时，会加载隐式链接到应用程序的 Dll。 若要在加载时提高性能，请尝试将该 DLL 分割成不同的 Dll。 将放入一个 DLL 加载后立即需要调用应用程序的所有函数，并且具有隐式链接到该 DLL 调用应用程序。 将其他函数的调用应用程序不需要立即放入另一个 DLL 和具有应用程序显式链接到该 DLL。 有关详细信息，请参阅[可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。

## <a name="memory_leak"></a> 存在&#39;s 规则 MFC DLL，但我的代码中的内存泄漏看起来很正常。 如何查找内存泄漏？

内存泄漏的一个可能的原因是 MFC 创建消息处理程序函数内部使用的临时对象。 在 MFC 应用程序，这些临时对象会自动清除在`CWinApp::OnIdle()`之间处理的消息调用的函数。 但是，在 MFC 动态链接库 (Dll)、`OnIdle()`函数不会自动调用。 因此，临时对象不会自动清理。 若要清理临时对象，该 DLL 必须显式调用`OnIdle(1)`定期。

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](dlls-in-visual-cpp.md)
