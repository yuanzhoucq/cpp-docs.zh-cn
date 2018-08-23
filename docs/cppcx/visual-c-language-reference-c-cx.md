---
title: Visual c + + 语言参考 (C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 09/15/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 801a88573133a68beec4855dc499fcba27bb64e8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593864"
---
# <a name="visual-c-language-reference-ccx"></a>Visual C++ 语言参考 (C++/CX)

C + + /cli CX 是一套用于 Windows 应用程序和 Windows 运行时组件中尽可能接近现代 c + + 惯用语法创建 c + + 语言扩展。 使用 C + + /cli CX 与 Visual C#、 Visual Basic 和 JavaScript，轻松地进行交互的本机代码和支持 Windows 运行时的其他语言中编写 Windows 应用程序和组件。 在这些少数情况下需要直接访问原始 COM 接口或非异常代码，你可以使用[Windows 运行时 c + + 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。

> [!NOTE]
> C + + / WinRT 是新的标准 C + + 17 语言投影的 Windows 运行时 Api。 它是从版本 1803年以后最新的 Windows 10 SDK 中提供。 C + + / WinRT 是完全在标头文件中实现，旨在提供对新式 Windows API 的优先访问权限。

> 使用 C + + / WinRT，您可以使用和编写 Windows 运行时 Api 使用任何符合标准的 C + + 17 编译器。 C + + WinRT 通常更好地执行，并生成较小的二进制文件比 Windows 运行时的任何其他语言选项。 我们将继续支持 C + + /cli CX 和 WRL，但强烈建议新的应用程序使用 C + + WinRT。 有关详细信息，请参阅[C + + WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index)。


通过使用 C + + /CX 中，您可以创建：

- C + + 通用 Windows 平台 (UWP) 应用程序使用 XAML 定义用户接口，并使用本机堆栈。 有关详细信息，请参阅[创建 c + + (UWP) 中的"你好 world"应用](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

- 可供基于 JavaScript 的 Windows 应用的 c + + Windows 运行时组件。 有关详细信息，请参阅[c + + 中创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

- Windows DirectX 游戏和图形密集型应用程序。 有关详细信息，请参阅[使用 DirectX 创建简单的 UWP 游戏](/windows/uwp/gaming/tutorial--create-your-first-metro-style-directx-game)。

## <a name="related-articles"></a>相关文章

|||
|-|-|
|[快速参考](../cppcx/quick-reference-c-cx.md)|表的关键字和运算符的 C + + /cli CX。|
|[类型系统](../cppcx/type-system-c-cx.md)|介绍了基本的 C + + /cli CX 类型和编程构造，以及如何利用 C + + /cli CX 来使用和创建 Windows 运行时类型。|
|[构建应用程序和库](../cppcx/building-apps-and-libraries-c-cx.md)|讨论如何使用 IDE 生成应用程序并链接到静态库和 DLL。|
|[与其他语言进行互操作](../cppcx/interoperating-with-other-languages-c-cx.md)|讨论如何组件编写通过使用 C + + /cli CX 可用以 JavaScript 编写的组件，任何托管语言中或 Windows 运行时 c + + 模板库。|
|[线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)|讨论如何为你创建的组件指定线程处理和封送行为。|
|[命名空间参考](../cppcx/namespaces-reference-c-cx.md)|默认命名空间、平台命名空间、Platform::Collections 和相关命名空间的参考文档。|
|[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|列出 Windows 运行时应用中不可用的 CRT 函数。|
|[如何指导使用 Windows 10 应用](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|提供有关 Windows 10 应用的深入指导以及详细信息的链接。|
|[C + + /cli CX 的第 0 部分\[n\]： 简介](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C + + /cli CX 的第 1 部分\[n\]： 一个简单的类](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + + /cli CX 的第 2 部分\[n\]： 带尖角符号的类型](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + + /cli CX 的第 3 部分\[n\]： 正在构造](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C + + /cli CX 的第 4 部分\[n\]： 静态成员函数](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|介绍性 Visual c + + 博客系列上 C + + /cli CX。|
