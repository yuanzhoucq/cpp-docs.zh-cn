---
title: 桌面应用程序 （Visual c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22f90be7d89a006ccbfdfde2f4c2580a7b2a13de
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643840"
---
# <a name="desktop-applications-visual-c"></a>桌面应用程序 （Visual c + +）
一个*桌面应用程序*c + + 中是可以访问 Windows Api 和是运行在窗口中或在系统控制台中的完整集的本机应用程序。 （尽管不再受正式支持 Windows XP，并且从那以后引入了许多 Windows api），在 c + + 的桌面应用程序可以在 Windows XP 到 Windows 10 上运行。

桌面应用程序与来自通用 Windows 平台 (UWP) 应用于运行 Windows 10 电脑以及 XBox、 Windows Phone、 Surface Hub 和其他设备上可以运行不同。 有关桌面 vs 的详细信息。UWP 应用程序，请参阅[选择你的技术](https://msdn.microsoft.com/library/windows/desktop/dn614993\(v=vs.85\).aspx)。  


### <a name="desktop-bridge"></a>桌面桥
在 Windows 10 可以打包你的现有桌面应用程序或作为 UWP 应用的 COM 对象和添加 UWP 功能，如触摸屏输入，或从现代 Windows API 集调用 Api。 您还可以向 Visual Studio 中，以及它们在单个包，并使用 Windows Api 它们之间通信的程序包的桌面解决方案添加 UWP 应用。  
   
在 Visual Studio 2017 版本 15.4 和更高版本中，可以创建一个 Windows 应用程序程序包项目，从而大大简化了打包现有的桌面应用程序的工作。 有一些限制方面的注册表调用或桌面应用程序的 Api 使用，但在许多情况下，您可以创建替代代码路径来在应用包运行时实现类似功能。 有关详细信息，请参阅[桌面桥](/windows-uwp/porting/desktop-to-uwp-root)。  
  
### <a name="terminology"></a>术语  
  
-   一个*Win32*应用程序是在可以进行的 c + + 的桌面应用程序使用的本机 Windows [Windows C Api 和/或 COM Api](https://msdn.microsoft.com/library/windows/desktop/ff818516\(v=vs.85\).aspx) CRT 和标准库 Api 和第三方库。 在窗口中运行的 Win32 应用程序需要开发人员可以显式使用内部 Windows 过程函数的 Windows 消息。 不管名称如何，Win32 应用程序可以编译为 32 位 (x86) 或 64 位 (x64) 二进制。 在 Visual Studio IDE 中的条款 x86 和 Win32 是同义的。  
  
-   [组件对象模型 (COM)](https://msdn.microsoft.com/library/windows/desktop/ms694363\(v=vs.85\).aspx)是一种规范，用来相互通信的不同语言编写的程序。 许多 Windows 组件作为 COM 对象实现，并且遵循标准 COM 规则对象的创建过程的接口发现和对象的析构。  使用 c + + 桌面应用程序的 COM 对象是相对简单，但更高级编写你自己的 COM 对象。 [活动模板库 (ATL)](../atl/atl-com-desktop-components.md)提供宏和 helper 函数，简化了 COM 开发。  
  
-   MFC 应用程序是使用的 Windows 桌面应用程序[Microsoft 基础类](../mfc/mfc-desktop-applications.md)来创建用户界面。 MFC 应用程序还可以使用 COM 组件，以及 CRT 和标准库 Api。 MFC 提供精简的 c + + 面向对象的包装器的窗口消息循环和 Windows Api。 MFC 是应用程序的默认选择，尤其是企业行应用程序 — 具有众多用户界面控件或自定义用户控件。 MFC 提供窗口管理、 序列化、 文本操作、 打印和功能区等现代用户界面元素的便利的帮助器类。 若要有效使用 MFC 应熟悉 Win32。  
  
-   C + + /cli CLI 应用程序或组件使用 c + + 语法的扩展 （c + + 规范的允许） 用于实现.NET 和本机 C + + 代码之间的交互。  C + + /cli CLI 的应用程序可以本机运行的部件和访问在.NET Framework 运行与.NET 基类库的部件。 C + + /cli CLI 是首选的选项，有时需要使用以 C# 或 Visual Basic 编写的代码的本机 c + + 代码。 它主要用于使用.NET Dll 中而不是在用户界面代码。 有关详细信息，请参阅[.NET 编程使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。  
  
 C 运行时 (CRT) 和标准库类和函数、 COM 对象和公共 Windows 函数，统称为 Windows API，可以使用 c + + 中的任何桌面应用程序。 有关使用 C++ 的 Windows 桌面应用程序，请参阅 [了解如何使用 C++ 编写适用于 Windows 的程序](http://go.microsoft.com/fwlink/p/?LinkId=262281)。  
  
## <a name="in-this-section"></a>本节内容  
  
|标题|描述|  
|-----------|-----------------|  
|[控制台应用程序](../windows/console-applications-in-visual-cpp.md)|包含有关控制台应用的信息。 Win32（或 Win64）控制台应用程序本身不具有窗口，且不使用消息循环。 它在控制台窗口中运行，并通过命令行处理输入和输出。|  
|[Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)|如何创建在而不是在控制台窗口中运行的桌面应用程序。|  
|[有关创建使用 DirectX （c + +） 的游戏的资源](../windows/resources-for-creating-a-game-using-directx.md)|在 c + + 中创建游戏的内容的链接。|  
|[演练： 创建和使用静态库](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|如何创建一个.lib 二进制文件。|  
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含使用 Windows 10 SDK 设置项目以便生成的步骤。|  
  
## <a name="related-articles"></a>相关文章  
  
|标题|描述|  
|-----------|-----------------|  
|[Windows 开发](http://go.microsoft.com/fwlink/p/?LinkId=262282)|包含有关 Windows API 和 COM 的信息。 （某些 Windows API 和第三方 DLL 是作为 COM 对象实现的。）|  
|[Hilo：开发适用于 Windows 7 的 C++ 应用程序](http://go.microsoft.com/fwlink/p/?LinkId=262284)|描述如何创建使用 Windows Animation 和 Direct2D 创建基于传送的用户界面的、客户端丰富的 Windows 桌面应用程序。  本教程尚未更新 Windows 7 以来，但它仍提供了 Win32 编程的全面介绍。|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|描述 Visual C++ 在 Visual Studio 中的主要功能，以及指向其他 Visual C++ 文档的链接。|  
  
## <a name="see-also"></a>请参阅  
 [Visual C++](../visual-cpp-in-visual-studio.md)