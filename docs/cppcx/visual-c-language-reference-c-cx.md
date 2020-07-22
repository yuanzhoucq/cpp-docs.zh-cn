---
title: C + +/CX 语言参考
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: 4f3816280630a6a061eb037a33367ef4e9d90375
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403850"
---
# <a name="ccx-language-reference"></a>C + +/CX 语言参考

C + +/CX 是 c + + 语言的一组扩展，使你能够在尽可能接近现代 c + + 的用法中创建 Windows 应用和 Windows 运行时组件。 使用 c + +/CX 编写本机代码中的 Windows 应用和组件，以便与 Visual c #、Visual Basic 和 JavaScript 以及支持 Windows 运行时的其他语言轻松交互。 在那些需要直接访问原始 COM 接口或非异常代码的罕见情况下，可以使用[Windows 运行时 c + + 模板库（WRL）](../windows/windows-runtime-cpp-template-library-wrl.md)。

> [!NOTE]
> **建议使用/WinRT 作为C++/cx 替代方法。 [ C++](/windows/uwp/cpp-and-winrt-apis/index)** 它是新的标准 c + + 17 语言投影，适用于 Windows 运行时 Api，可从版本1803的最新 Windows 10 SDK 获得。 C + +/WinRT 完全在头文件中实现，旨在为您提供对现代 Windows API 的一流访问。
>
> 使用 c + +/WinRT，可以使用任何符合标准的 c + + 17 编译器来使用和创作 Windows 运行时 Api。 与 Windows 运行时的任何其他语言选项相比，c + +/WinRT 的性能更佳，生成的二进制文件更小。 我们将继续支持 C++/CX 和 WRL，但强烈建议新应用程序使用 C++/WinRT。 有关详细信息，请参阅[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/index)。

通过使用 c + +/CX，你可以创建：

- 使用 XAML 定义用户界面和使用本机堆栈的 c + + 通用 Windows 平台（UWP）应用。 有关详细信息，请参阅[使用 c + + （UWP）创建 "hello world" 应用](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

- C + + Windows 运行时可供基于 JavaScript 的 Windows 应用程序使用的组件。 有关详细信息，请参阅 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

- Windows DirectX 游戏和图形密集型应用程序。 有关详细信息，请参阅[使用 DirectX 创建简单的 UWP 游戏](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game)。

## <a name="related-articles"></a>相关文章

| 链接 | 说明 |
|--|--|
| [快速参考](../cppcx/quick-reference-c-cx.md) | C + +/CX 的关键字和运算符表 |
| [类型系统](../cppcx/type-system-c-cx.md) | 介绍基本 c + +/CX 类型和编程构造，以及如何利用 c + +/CX 来使用和创建 Windows 运行时类型。 |
| [生成应用和库](../cppcx/building-apps-and-libraries-c-cx.md) | 讨论如何使用 IDE 生成应用程序并链接到静态库和 Dll。 |
| [与其他语言互操作](../cppcx/interoperating-with-other-languages-c-cx.md) | 讨论使用 c + +/CX 编写的组件如何与用 JavaScript、任何托管语言或 Windows 运行时 c + + 模板库编写的组件一起使用。 |
| [线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md) | 讨论如何为你创建的组件指定线程处理和封送行为。 |
| [命名空间引用](../cppcx/namespaces-reference-c-cx.md) | 默认命名空间、平台命名空间、Platform::Collections 和相关命名空间的参考文档。 |
| [通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) | 列出 Windows 运行时应用中不可用的 CRT 函数。 |
| [Windows 10 应用入门](/windows/uwp/get-started/) | 提供有关 Windows 10 应用的深入指导以及详细信息的链接。 |
| [C + +/CX 第0部分（共 n 部分） \[ \] ：简介](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)<br /><br />[C + +/CX 第1部分（共 n 部分） \[ \] ：简单类](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + +/CX 第2部分（共 n 部分） \[ \] ：磨损头衔的类型](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + +/CX 第3部分（共3部分） \[ \] ：正在建设](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)<br /><br />[C + +/CX 第4部分，共 \[ n 个 \] ：静态成员函数](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)| C + +/CX 上的介绍性博客系列 |
