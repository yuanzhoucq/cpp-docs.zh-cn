---
title: 桌面应用程序 （Visual c + +）
ms.date: 11/04/2016
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.openlocfilehash: 80b85afc52819a742c85512e8e6031b9b2e26e9a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694564"
---
# <a name="desktop-applications-visual-c"></a>桌面应用程序 （Visual c + +）

C++ 桌面应用程序是可以访问完整的 Windows API 集并在窗口或系统控制台中运行的本机应用程序。 C++ 桌面应用程序可以在 Windows XP 到 Windows 10 这一系列平台上运行（虽然 Windows XP 不再受正式支持，并且从那以后引入了许多 Windows API）。

桌面应用程序不同于通用 Windows 平台 (UWP) 应用，后者可以在运行 Windows 10 的电脑上运行，也可以在 XBox、Windows Phone、Surface Hub 和其他设备上运行。 有关桌面 vs 的详细信息。UWP 应用程序，请参阅[选择你的技术](/windows/desktop/choose-your-technology)。

### <a name="desktop-bridge"></a>桌面桥

在 Windows 10 中，可以将现有的桌面应用程序或者 COM 对象打包为 UWP 应用并添加 UWP 功能，如触摸屏输入，或从现代 Windows API 集调用 API。 还可以向 Visual Studio 的桌面解决方案中添加 UWP 应用，然后将其封装在单个包中，使用 Windows API 在其间通信。

在 Visual Studio 2017 版本 15.4 及更高版本中，可以创建一个 Windows 应用程序包项目，大大简化打包现有桌面应用程序的工作。 桌面应用程序使用的注册表调用或 API 存在一些限制，但多数情况下，在应用包中运行时，可以创建替代代码路径来实现类似功能。 有关详细信息，请参阅[桌面桥](/windows-uwp/porting/desktop-to-uwp-root)。

### <a name="terminology"></a>术语

- *Win32* 应用程序是采用 C++ 编写的 Windows 桌面应用程序，它可以使用本机 [Windows C API 和/或 COM API](/windows/desktop/apiindex/windows-api-list) CRT 和标准库 API 以及第三方库。 在窗口中运行的 Win32 应用程序需要开发人员显式使用 Windows 过程函数中的 Windows 消息。 虽然名为 32 位，但 Win32 应用程序可以编译为 32 位 (x86) 或 64 位 (x64) 二进制程序。 在 Visual Studio IDE 中，x86 和 Win32 这两个术语是同义的。

- [组件对象模型 (COM)](/windows/desktop/com/the-component-object-model)是一种规范，用来相互通信的不同语言编写的程序。 许多 Windows 组件作为 COM 对象实现，并且遵循标准 COM 规则对象的创建过程的接口发现和对象的析构。  使用 c + + 桌面应用程序的 COM 对象是相对简单，但更高级编写你自己的 COM 对象。 [活动模板库 (ATL)](../atl/atl-com-desktop-components.md)提供宏和 helper 函数，简化了 COM 开发。

- MFC 应用程序是使用的 Windows 桌面应用程序[Microsoft 基础类](../mfc/mfc-desktop-applications.md)来创建用户界面。 MFC 应用程序还可以使用 COM 组件，以及 CRT 和标准库 Api。 MFC 提供精简的 c + + 面向对象的包装器的窗口消息循环和 Windows Api。 MFC 是应用程序的默认选择，尤其是企业行应用程序 — 具有众多用户界面控件或自定义用户控件。 MFC 提供窗口管理、 序列化、 文本操作、 打印和功能区等现代用户界面元素的便利的帮助器类。 若要有效使用 MFC 应熟悉 Win32。

- C + + /cli CLI 应用程序或组件使用 c + + 语法的扩展 （c + + 规范的允许） 用于实现.NET 和本机 C + + 代码之间的交互。  C + + /cli CLI 的应用程序可以本机运行的部件和访问在.NET Framework 运行与.NET 基类库的部件。 C + + /cli CLI 是首选的选项，有时需要使用以 C# 或 Visual Basic 编写的代码的本机 c + + 代码。 它主要用于使用.NET Dll 中而不是在用户界面代码。 有关详细信息，请参阅[.NET 编程使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

C 运行时 (CRT) 和标准库类和函数、 COM 对象和公共 Windows 函数，统称为 Windows API，可以使用 c + + 中的任何桌面应用程序。 在 c + + Windows 桌面应用程序的简介，请参阅[Win32 和 c + + 入门](/windows/desktop/LearnWin32/learn-to-program-for-windows)。

## <a name="in-this-section"></a>本节内容

|标题|描述|
|-----------|-----------------|
|[C++ 中的 Windows 控制台应用程序](console-applications-in-visual-cpp.md)|包含有关控制台应用的信息。 Win32（或 Win64）控制台应用程序本身不具有窗口，且不使用消息循环。 它在控制台窗口中运行，并通过命令行处理输入和输出。|
|[演练：创建 Windows 桌面应用程序 (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|创建一个简单的 Windows 桌面应用程序。|
|[创建空的 Windows 桌面应用程序](creating-an-empty-windows-desktop-application.md)|如何创建 Windows 桌面项目没有默认文件。|
|[向空的 Win32 应用程序添加文件](adding-files-to-an-empty-win32-applications.md)|如何将文件添加到一个空项目。|
|[使用资源文件](working-with-resource-files.md)|如何将图像、 图标、 字符串表和其他资源添加到桌面应用程序。|
|[有关创建使用 DirectX （c + +） 的游戏的资源](resources-for-creating-a-game-using-directx.md)|在 c + + 中创建游戏的内容的链接。|
|[演练： 创建和使用静态库](walkthrough-creating-and-using-a-static-library-cpp.md)|如何创建一个.lib 二进制文件。|
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含使用 Windows 10 SDK 设置项目以便生成的步骤。|

## <a name="related-articles"></a>相关文章

|标题|描述|
|-----------|-----------------|
|[Windows 开发](/windows/desktop/index)|包含有关 Windows API 和 COM 的信息。 （某些 Windows API 和第三方 DLL 是作为 COM 对象实现的。）|
|[Hilo：开发适用于 Windows 7 的 C++ 应用程序](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)|描述如何创建使用 Windows Animation 和 Direct2D 创建基于传送的用户界面的、客户端丰富的 Windows 桌面应用程序。  本教程尚未更新 Windows 7 以来，但它仍提供了 Win32 编程的全面介绍。|
|[C++ 中 Windows 编程概述](overview-of-windows-programming-in-cpp.md)|介绍 Windows 桌面 c + + 编程主要的功能。|

## <a name="see-also"></a>请参阅

[Visual C++](../visual-cpp-in-visual-studio.md)
