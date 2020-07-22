---
title: 通用 Windows 应用 (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: 25b89d2d9cb99e05145e60f9c9b1a6324fbbeb39
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404595"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 应用 (C++)

通用 Windows 平台（UWP）是适用于 Windows 的新式编程接口。 使用 UWP，你只需要编写一次应用程序或组件，然后将其部署到任何 Windows 10 设备上。 您可以在 c + + 中编写组件，使用任何其他 UWP 兼容的语言编写的应用程序都可以使用该组件。

大多数 UWP 文档都位于[通用 Windows 平台文档](/windows/uwp/)的 Windows 内容树中。 可在其中找到开始教程和参考文档。

对于新的 UWP 应用和组件，我们建议你使用[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/)，这是一个新的标准 c + + 17 语言投影，适用于 Windows 运行时 api。 C++/WinRT 从版本 1803 起在 Windows 10 SDK 中提供。 C++/WinRT 完全在头文件中实现，旨在提供对新式 Windows API 的优先访问权限。 与 c + +/CX 实现不同，c + +/WinRT 不使用非标准语法或 Microsoft 语言扩展，它充分利用 c + + 编译器来创建高度优化的输出。 有关详细信息，请参阅[c + +/WinRT 简介](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

可以使用桌面桥应用转换器打包现有的桌面应用程序，以便通过 Microsoft Store 进行部署。 有关详细信息，请参阅在 Centennial 项目和[桌面桥](/windows/uwp/porting/desktop-to-uwp-root)[中使用 Visual C++ 运行时](https://devblogs.microsoft.com/cppblog/using-visual-c-runtime-in-centennial-project/)。

## <a name="uwp-apps-that-use-ccx"></a>使用 c + +/CX 的 UWP 应用

|||
|-|-|
|[C++/CX 语言参考](visual-c-language-reference-c-cx.md)|描述一组扩展，这些扩展可简化 Windows 运行时 Api 的 c + + 消耗并启用基于异常的错误处理。|
|[生成应用程序和库 (C++/CX)](building-apps-and-libraries-c-cx.md)|描述如何创建可从 C++/CX 应用或组件进行访问的 Dll 和静态库。|
|[教程：在 c + +/CX 中创建 UWP "Hello，World" 应用](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|介绍如何在 c + + 中开发 UWP 应用开发的基本概念的演练/CX |
|[在 c + +/CX 中创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|介绍如何创建其他 UWP 应用和组件可以使用的 Dll。|
|[UWP 游戏编程](/windows/uwp/gaming/)|介绍如何使用 DirectX 和 c + +/CX 创建游戏。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 运行时 c + + 模板库（WRL）的 UWP 应用

Windows 运行时 c + + 模板库提供低级别的 COM 接口，ISO c + + 代码可通过该接口在无异常环境中访问 Windows 运行时。 在大多数情况下，我们建议你使用 c + +/WinRT 或 c + +/CX，而不是使用适用于 UWP 应用开发的 Windows 运行时 c + + 模板库。 有关 Windows 运行时 c + + 模板库的信息，请参阅[Windows 运行时 c + + 模板库（WRL）](wrl/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>另请参阅

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[C + + 中的 Windows 编程概述](../windows/overview-of-windows-programming-in-cpp.md)<br/>
