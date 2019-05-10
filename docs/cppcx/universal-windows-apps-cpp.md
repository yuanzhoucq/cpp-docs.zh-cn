---
title: 通用 Windows 应用 (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.openlocfilehash: fbd5366ee52dfe32baef9458a82c16914666699e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392058"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 应用 (C++)

通用 Windows 平台 (UWP) 是 Windows 的新式编程接口。 使用 UWP 编写应用程序或组件的一次并将其部署任何 Windows 10 设备上。 可以编写的组件C++和任何其他 UWP 兼容语言编写的应用程序可以使用它。

UWP 文档大部分都是在 Windows 内容树中[通用 Windows 平台文档](/windows/uwp/)。 可以在其中找到开始教程也作为参考文档。 

对于新的 UWP 应用和组件，我们建议你使用[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)，新标准 C + + 17 的语言投影的 Windows 运行时 Api。 C++/ WinRT 是 Windows 10 SDK 版本 1803年以后从中可用。 C++/ WinRT 完全在标头文件中实现，它旨在提供对新式 Windows API 的优先访问权限。 不同于C++/CX 实现。 C++/ WinRT 不使用非标准语法或 Microsoft 语言扩展，并利用完整的C++编译器创建高度优化输出。 有关详细信息，请参阅[简介C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

可以使用桌面桥应用转换器打包现有桌面应用程序，通过 Microsoft Store 进行部署。 有关详细信息，请参阅 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) （在 Centennial 项目中使用 VC 运行时）和 [Bring your desktop app to the Universal Windows Platform (UWP) with the Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root)（使用桌面桥将桌面应用引入通用 Windows 平台 (UWP)）。

## <a name="uwp-apps-that-use-ccx"></a>使用的 UWP 应用C++/CX

|||
|-|-|
|[Visual C++ 语言参考 (C++/CX)](visual-c-language-reference-c-cx.md)|描述简化的扩展集C++Windows 运行时 Api 和启用错误处理基于异常的消耗。|
|[生成应用程序和库 (C++/CX)](building-apps-and-libraries-c-cx.md)|描述如何创建可从 C++/CX 应用或组件进行访问的 Dll 和静态库。|
|[教程：创建的 UWP 中的"Hello，World"应用C++/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|一个演练，介绍中的 UWP 应用开发的基本概念C++/CX。 |
|[创建 Windows 运行时组件中的C++/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|介绍如何创建其他 UWP 应用和组件可以使用的 Dll。|
|[UWP 游戏编程](/windows/uwp/gaming/)|介绍如何使用 DirectX 和C++/CX 创建游戏。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 运行时的 UWP 应用C++模板库 (WRL)

Windows 运行时 C++ 模板库提供低级别的 COM 接口，让 ISO C++ 代码可以在无异常的环境中访问 Windows 运行时。 在大多数情况下，建议使用 C++/CX 而不是Windows 运行时 C++ 模板库来开发通用 Windows 平台应用程序。 有关 Windows 运行时 C++ 模板库的信息，请参阅 [Windows 运行时 C++ 模板库 (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>请参阅

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[C++ 中 Windows 编程概述](../windows/overview-of-windows-programming-in-cpp.md)<br/>