---
title: 桌面应用程序（ C++视觉对象）
ms.date: 07/28/2019
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.topic: overview
ms.openlocfilehash: 91fcc596a4c30e3fa74043c846eda6f06b666f2c
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274727"
---
# <a name="desktop-applications-visual-c"></a>桌面应用程序（ C++视觉对象）

C++桌面应用程序是可以访问完整的 Windows API 集并在窗口或系统控制台中运行的本机应用程序。 C++ 桌面应用程序可以在 Windows XP 到 Windows 10 这一系列平台上运行（虽然 Windows XP 不再受正式支持，并且从那以后引入了许多 Windows API）。 

桌面应用程序不同于通用 Windows 平台 (UWP) 应用，后者可以在运行 Windows 10 的电脑上运行，也可以在 XBox、Windows Phone、Surface Hub 和其他设备上运行。 有关桌面应用程序与 UWP 应用程序的详细比较，请参阅[Choose Your Platform](/windows/win32/choose-your-technology)（选择平台）。

### <a name="desktop-bridge"></a>桌面桥接

在 Windows 10 中，可以将现有的桌面应用程序或者 COM 对象打包为 UWP 应用并添加 UWP 功能，如触摸屏输入，或从现代 Windows API 集调用 API。 还可以向 Visual Studio 的桌面解决方案中添加 UWP 应用，然后将其封装在单个包中，使用 Windows API 在其间通信。

在 Visual Studio 2017 版本 15.4 及更高版本中，可以创建一个 Windows 应用程序包项目，大大简化打包现有桌面应用程序的工作。 桌面应用程序使用的注册表调用或 API 存在一些限制，但多数情况下，在应用包中运行时，可以创建替代代码路径来实现类似功能。 有关详细信息，请参阅[桌面桥](/windows/uwp/porting/desktop-to-uwp-root)。

### <a name="terminology"></a>术语

- *Win32* 应用程序是采用 C++ 编写的 Windows 桌面应用程序，它可以使用本机 [Windows C API 和/或 COM API](/windows/win32/apiindex/windows-api-list) CRT 和标准库 API 以及第三方库。 在窗口中运行的 Win32 应用程序需要开发人员显式使用 Windows 过程函数中的 Windows 消息。 虽然名为 32 位，但 Win32 应用程序可以编译为 32 位 (x86) 或 64 位 (x64) 二进制程序。 在 Visual Studio IDE 中，x86 和 Win32 这两个术语是同义的。

- [组件对象模型（COM）](/windows/win32/com/the-component-object-model)是一种规范，用不同语言编写的程序可以相互通信。 许多 Windows 组件是作为 COM 对象实现的，并遵循用于对象创建、接口发现和对象析构的标准 COM 规则。  使用桌面应用程序C++中的 com 对象相对简单，但编写自己的 com 对象更高级。 [活动模板库（ATL）](../atl/atl-com-desktop-components.md)提供了可简化 COM 开发的宏和帮助程序函数。

- MFC 应用程序是一个 Windows 桌面应用程序，它使用[Microsoft 基础类](../mfc/mfc-desktop-applications.md)来创建用户界面。 MFC 应用程序还可以使用 COM 组件以及 CRT 和标准库 Api。 MFC 通过窗口消息C++循环和 Windows api 提供面向对象的精简包装器。 MFC 是具有许多用户界面控件或自定义用户控件的应用程序（尤其是企业类型应用程序）的默认选择。 MFC 为窗口管理、序列化、文本操作、打印和新式用户界面元素（如功能区）提供了便利的帮助器类。 为了有效地处理 MFC，你应该熟悉 Win32。

- C++/Cli 应用程序或组件使用C++语法扩展（如C++标准允许）来实现 .net 和本机 C + + 代码之间的交互。  C++/Cli 应用程序可以具有以本机方式运行的部分，以及在 .NET Framework 上运行的部件，并可访问 .Net 基类库。 C++如果有需要使用C++ C#或 Visual Basic 编写的代码的本机代码，则/cli 是首选选项。 它旨在在 .NET Dll 中使用，而不是在用户界面代码中使用。 有关详细信息，请参阅[使用 C++/CLI 进行 .NET 编程 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

中的C++任何桌面应用程序都可以使用 C 运行时（CRT）和标准库类和函数、COM 对象和公共 Windows 函数，它们统称为 Windows API。 有关中C++的 Windows 桌面应用程序的简介，请参阅[Win32 和C++入门](/windows/win32/LearnWin32/learn-to-program-for-windows)。

## <a name="in-this-section"></a>本节内容

|Title|描述|
|-----------|-----------------|
|[C++ 中的 Windows 控制台应用程序](console-applications-in-visual-cpp.md)|包含有关控制台应用的信息。 Win32（或 Win64）控制台应用程序本身不具有窗口，且不使用消息循环。 它在控制台窗口中运行，并通过命令行处理输入和输出。|
|[演练：创建 Windows 桌面应用程序 (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|创建一个简单的 Windows 桌面应用程序。|
|[创建空的 Windows 桌面应用程序](creating-an-empty-windows-desktop-application.md)|如何创建没有默认文件的 Windows 桌面项目。|
|[向空的 Win32 应用程序添加文件](adding-files-to-an-empty-win32-applications.md)|如何将文件添加到空项目。|
|[使用资源文件](working-with-resource-files.md)|如何向桌面应用程序添加图像、图标、字符串表以及其他资源。|
|[使用 DirectX 创建游戏的资源（C++）](resources-for-creating-a-game-using-directx.md)|用于在中C++创建游戏的内容的链接。|
|[演练：创建和使用静态库](walkthrough-creating-and-using-a-static-library-cpp.md)|如何创建 .lib 二进制文件。|
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含使用 Windows 10 SDK 设置项目以便生成的步骤。|

## <a name="related-articles"></a>相关文章

|Title|描述|
|-----------|-----------------|
|[Windows 开发](/windows/win32/index)|包含有关 Windows API 和 COM 的信息。 （某些 Windows API 和第三方 DLL 是作为 COM 对象实现的。）|
|[Hilo开发C++适用于 Windows 7 的应用程序](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)|描述如何创建使用 Windows Animation 和 Direct2D 创建基于传送的用户界面的、客户端丰富的 Windows 桌面应用程序。  此教程自 Windows 7 以来尚未更新，但它仍提供了 Win32 编程的全面介绍。|
|[C++ 中 Windows 编程概述](overview-of-windows-programming-in-cpp.md)|描述中C++Windows 桌面编程的主要功能。|

## <a name="see-also"></a>请参阅

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)