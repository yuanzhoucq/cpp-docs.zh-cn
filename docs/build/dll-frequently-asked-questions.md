---
title: "MFC DLL 常见问题 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 39c3a36f697527c7e133409f49656e4415f86a7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dll-frequently-asked-questions"></a>DLL 常见问题  
  
以下是一些常见问题 (FAQ) 有关 Dll。  
    
-   [MFC DLL 是否能创建多个线程？](#mfc_multithreaded_1)  

-   [多线程应用程序是否可以访问不同的线程 MFC DLL？](#mfc_multithreaded_2)  
  
-   [是否有任何 MFC 类或函数不能用于在非 MFC DLL？](#mfc_prohibited_classes)  
  
-   [我应使用哪些优化技术来提高客户端应用程序的性能，在加载时？](#mfc_optimization)  
  
-   [在我正则 MFC DLL，内存泄漏，但我的代码看起来很正常。如何查找内存泄露？](#memory_leak)  

## <a name="mfc_multithreaded_1"></a>MFC DLL 是否能创建多个线程？  
  
不同的初始化过程中，MFC DLL 可以安全地创建多个线程，只要它使用 Win32 线程本地存储 (TLS) 函数如**TlsAlloc**分配线程本地存储区。 但是，如果使用 MFC DLL **__declspec （thread)**以将线程本地存储的分配，客户端应用程序必须隐式链接到 DLL。 如果客户端应用程序显式链接到 DLL 调用**LoadLibrary**不会成功加载 DLL。 有关创建 MFC Dll 中的多个线程的详细信息，请参阅知识库文章"PRB:: 调用 LoadLibrary() 到负载 DLL，具有静态 TLS"(Q118816)。 Dll 中的线程本地变量的详细信息，请参阅[线程](../cpp/thread.md)。
  
 在启动过程中创建一个新的 MFC 线程非 MFC DLL 将停止在应用程序加载时进行响应。 这包括每当一个线程通过调用创建`AfxBeginThread`或`CWinThread::CreateThread`内：  
  
-   `InitInstance`的`CWinApp`-派生对象的规则的 MFC DLL 中。  
  
-   提供`DllMain`或**RawDllMain**的规则的 MFC DLL 中的函数。  
  
-   提供`DllMain`或**RawDllMain** MFC 扩展 DLL 中的函数。  
  
 有关在初始化期间创建线程的详细信息，请参阅知识库文章"PRB:: 无法创建 MFC 线程在 DLL 启动"(Q142243)。  
  
## <a name="mfc_multithreaded_2"></a>多线程应用程序是否可以访问不同的线程 MFC DLL？
多线程应用程序可从不同的线程访问 MFC 的规则 Dll，动态链接到 MFC 和 MFC 扩展 Dll。 并且，截至 Visual c + + 4.2 版开始，应用程序可以访问从创建应用程序中的多个线程，静态链接到 MFC 的规则 MFC Dll。  
  
 之前版本 4.2，只有一个外部线程可以将附加到静态链接到 MFC 的规则 MFC DLL。 有关限制访问从 （之前 Visual c + + 4.2 版） 的多个线程，静态链接到 MFC 的规则 MFC Dll 的详细信息，请参阅知识库文章中，"多个线程和 MFC _USRDLLs"(Q122676)。  
  
 请注意，术语 USRDLL 不再使用 Visual c + + 文档中。 静态链接到 MFC 常规 MFC DLL 具有以前的 USRDLL 作为相同的特征。  


## <a name="mfc_prohibited_classes"></a>是否有任何 MFC 类或函数不能用于在非 MFC DLL？
扩展 Dll 使用`CWinApp`-客户端应用程序的派生类。 它们不得具有其自己`CWinApp`-派生类。  
  
常规 MFC Dll 必须有`CWinApp`-派生的类以及该类应用程序的单个对象一样 MFC 应用程序。 与不同`CWinApp`应用程序的对象`CWinApp`的 DLL 的对象不具有主消息泵。  
  
 请注意，因为`CWinApp::Run`机制不适用于 DLL、 应用程序拥有的主消息泵。 如果 DLL 打开无模式对话框或有其自己的主框架窗口时，应用程序的主消息泵必须调用该 DLL，从而又会调用由导出例程`CWinApp::PreTranslateMessage`DLL 的应用程序对象的成员函数。  

## <a name="mfc_optimization"></a>哪些优化技术应使用来提高客户端应用程序 &#39; s 加载时的性能？
如果 DLL 是静态链接到 MFC，将其更改为正则表达式的正则 MFC DLL 动态链接到 MFC 的 MFC DLL 可减少文件大小。  
  
 如果 DLL 具有大量导出函数，使用.def 文件要导出的函数 (而不是使用**__declspec （dllexport)**) 并使用.def 文件[NONAME 特性](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)上每个导出函数。 NONAME 特性会导致仅将序号值而不是函数名称存储在 DLL 的导出表中，这会减少文件大小。  
  
 应用程序加载时，会加载隐式链接到应用程序的 Dll。 若要在加载时提高的性能，请尝试将 DLL 分割成不同的 Dll。 放入一个 dll 的加载后立即调用应用程序需要的所有函数，并且具有隐式链接到该 DLL 的调用应用程序。 将其他函数调用的应用程序无需立即放入另一个 DLL，并具有应用程序显式链接到该 DLL。 有关详细信息，请参阅[确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。  

## <a name="memory_leak"></a>存在 &#39; s 我正则 MFC DLL，但我的代码中的内存泄漏，看起来不错。 如何查找内存泄露？  
  
内存泄漏的一个可能的原因是 MFC 创建在消息处理程序函数内使用的临时对象。 在 MFC 应用程序，这些临时对象会自动清除中`CWinApp::OnIdle()`之间处理的消息调用的函数。 但是，在 MFC 动态链接库 (Dll)、`OnIdle()`将不会自动调用函数。 因此，临时对象不会自动清理。 若要清理临时对象，该 DLL 必须显式调用`OnIdle(1)`定期。  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)