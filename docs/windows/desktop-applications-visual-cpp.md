---
title: 桌面应用程序 （Visual c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
caps.latest.revision: 17
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61f52dead8ca7ecad52b1cef4f1d87ffc5830386
ms.sourcegitcommit: 78e5e5cdbafd29e2a6ccf68d4cce215136952907
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2018
---
# <a name="desktop-applications-visual-c"></a>桌面应用程序 （Visual c + +）
A*桌面应用程序*c + + 中是可以访问的 Windows Api，并在窗口中或在系统控制台任一运行整套的本机应用程序。 （尽管不再受正式支持 Windows XP，并且有从那时起已引入的许多 Windows Api），在 c + + 桌面应用程序可以通过 Windows 10 的 Windows XP 上运行。   桌面应用程序是不同于通用 Windows 平台 (UWP) 应用程序，可以在运行 Windows 10 的 Pc 上以及在 XBox、 Windows Phone、 Surface Hub 和其他设备上运行。 有关桌面 vs 的详细信息。UWP 应用程序，请参阅[选择您的技术](https://msdn.microsoft.com/en-us/library/windows/desktop/dn614993\(v=vs.85\).aspx)。  
  
 **Terminology**  
  
-   A *Win32*应用程序是一个 Windows 桌面应用程序可以进行的 c + + 中使用的本机[Windows C Api 和/或 COM Api](https://msdn.microsoft.com/en-us/library/windows/desktop/ff818516\(v=vs.85\).aspx) CRT 和标准库 Api，和第三方库。 在窗口中运行的 Win32 应用程序需要开发人员可以显式使用 Windows 消息在窗口过程函数。 不管名称如何，Win32 应用程序可以编译为 32 位 (x86) 或 64 位 (x64) 二进制。 在 Visual Studio IDE 中的条款 x86 和 Win32 是同义词。  
  
-   [组件对象模型 (COM)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms694363\(v=vs.85\).aspx)是一种规范，用来相互通信的不同语言编写的程序。 许多 Windows 组件都作为 COM 对象实现，遵循标准的 COM 规则创建对象，接口发现和对象的析构。  C + + 桌面应用程序中使用 COM 对象是相对比较简单，但更高级编写你自己的 COM 对象。 [活动模板库 (ATL)](../atl/atl-com-desktop-components.md)提供的宏和简化了 COM 开发的帮助器函数。  
  
-   MFC 应用程序是的 Windows 桌面应用程序使用[Microsoft 基础类](../mfc/mfc-desktop-applications.md)创建用户界面。 COM 组件，以及 CRT 和标准库 Api，还可以使用 MFC 应用程序。 MFC 通过窗口消息循环和 Windows Api 提供精简 c + + 面向对象的包装。 MFC 是应用程序的默认选择 — 特别是企业类型应用程序-具有众多用户界面控件或自定义用户控件。 窗口管理、 序列化、 文本操作、 打印和现代用户界面元素，如功能区，MFC 提供便捷的帮助器类。 若要有效使用 MFC 应熟悉 Win32。  
  
-   C + + /cli CLI 应用程序或组件使用扩展到 c + + 语法 （如允许 c + + 规范） 来启用.NET 和本机 C + + 代码之间的交互。  C + + /cli CLI 的应用程序可以运行本机的部件以及具有访问权限在.NET Framework 运行到.NET 基类库的部件。 C + + /cli CLI 是首选的选项，当你有需要使用用 C# 或 Visual Basic 编写的代码的本机 c + + 代码。 它主要用于使用.NET Dll 中而不是中的用户界面代码。 有关详细信息，请参阅[.NET 编程使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。  
  
 C 运行时 (CRT) 和标准库类和函数、 COM 对象和公共 Windows 函数，统称为 Windows API，可以使用 c + + 中的任何桌面应用程序。 有关使用 C++ 的 Windows 桌面应用程序，请参阅 [了解如何使用 C++ 编写适用于 Windows 的程序](http://go.microsoft.com/fwlink/p/?LinkId=262281)。  
  
## <a name="in-this-section"></a>本节内容  
  
|标题|描述|  
|-----------|-----------------|  
|[控制台应用程序](../windows/console-applications-in-visual-cpp.md)|包含有关控制台应用的信息。 Win32（或 Win64）控制台应用程序本身不具有窗口，且不使用消息循环。 它在控制台窗口中运行，并通过命令行处理输入和输出。|  
|[Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)|如何创建在而不是控制台窗口中运行的桌面应用程序。|  
|[有关使用 DirectX （c + +） 创建游戏的资源](../windows/resources-for-creating-a-game-using-directx.md)|在 c + + 中创建游戏的内容的链接。|  
|[演练： 创建和使用静态库](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|如何创建.lib 二进制文件。|  
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含使用 Windows 10 SDK 设置项目以便生成的步骤。|  
  
## <a name="related-articles"></a>相关文章  
  
|标题|描述|  
|-----------|-----------------|  
|[Windows 开发](http://go.microsoft.com/fwlink/p/?LinkId=262282)|包含有关 Windows API 和 COM 的信息。 （某些 Windows API 和第三方 DLL 是作为 COM 对象实现的。）|  
|[Hilo：开发适用于 Windows 7 的 C++ 应用程序](http://go.microsoft.com/fwlink/p/?LinkId=262284)|描述如何创建使用 Windows Animation 和 Direct2D 创建基于传送的用户界面的、客户端丰富的 Windows 桌面应用程序。  本教程尚未更新自 Windows 7，但它仍提供了 Win32 编程中的全面介绍。|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|描述 Visual C++ 在 Visual Studio 中的主要功能，并链接到 Visual C++ 文档的剩余部分。|  
  
## <a name="see-also"></a>另请参阅  
 [Visual C++](../visual-cpp-in-visual-studio.md)
