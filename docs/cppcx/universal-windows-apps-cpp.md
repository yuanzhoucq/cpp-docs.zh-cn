---
title: 通用 Windows 应用 (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: cd90f76cf2ee9b4ca9cb2ceea970cd24b0bf24cf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079916"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 应用 (C++)

通用 Windows 平台（UWP）是适用于 Windows 的新式编程接口。 使用 UWP，你只需要编写一次应用程序或组件，然后将其部署到任何 Windows 10 设备上。 你可以在中C++编写一个组件，并且用任何其他 UWP 兼容的语言编写的应用程序都可以使用该组件。

大多数 UWP 文档都位于[通用 Windows 平台文档](/windows/uwp/)的 Windows 内容树中。 可在其中找到开始教程和参考文档。

对于新的 UWP 应用和组件，我们建议使用[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)，这是一个新的标准 c + + 17 语言投影，适用于 Windows 运行时 api。 C++/WinRT 从版本1803开始，在 Windows 10 SDK 中提供。 C++/WinRT 完全在标头文件中实现，旨在向您提供对新式 Windows API 的第一类访问。 与C++/cx 实现不同。 C++/WinRT 不使用非标准语法或 Microsoft 语言扩展，它充分利用C++编译器来创建高度优化的输出。 有关详细信息，请参阅[ C++/WinRT 简介](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

可以使用桌面桥应用转换器打包现有的桌面应用程序，以便通过 Microsoft Store 进行部署。 有关详细信息，请参阅在 Centennial 项目和[桌面桥](/windows/uwp/porting/desktop-to-uwp-root)[中C++使用 Visual Runtime](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) 。

## <a name="uwp-apps-that-use-ccx"></a>使用C++/CX 的 UWP 应用

|||
|-|-|
|[C++/CX 语言参考](visual-c-language-reference-c-cx.md)|描述一组扩展，这些扩展C++可简化 Windows 运行时 api 的消耗，并启用基于异常的错误处理。|
|[生成应用和库 (C++/CX)](building-apps-and-libraries-c-cx.md)|描述如何创建可从 C++/CX 应用或组件进行访问的 Dll 和静态库。|
|[教程：在/Cx 中C++创建 UWP "Hello，World" 应用](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|本演练介绍了/Cx 中C++UWP 应用开发的基本概念 |
|[在/Cx 中C++创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|介绍如何创建其他 UWP 应用和组件可以使用的 Dll。|
|[UWP 游戏编程](/windows/uwp/gaming/)|介绍如何使用 DirectX 和C++/cx 创建游戏。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 运行时C++模板库（WRL）的 UWP 应用

Windows 运行时 C++ 模板库提供低级别的 COM 接口，让 ISO C++ 代码可以在无异常的环境中访问 Windows 运行时。 在大多数情况下，建议使用 C++/CX 而不是Windows 运行时 C++ 模板库来开发通用 Windows 平台应用程序。 有关 Windows 运行时C++模板库的信息，请参阅[Windows 运行时C++模板库（WRL）](wrl/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>另请参阅

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[C++ 中 Windows 编程概述](../windows/overview-of-windows-programming-in-cpp.md)<br/>