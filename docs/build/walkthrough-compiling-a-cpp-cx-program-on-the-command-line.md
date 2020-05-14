---
title: 演练：在命令行上编译 C++/CX 程序
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 83369fc7b458463ea1f44a347bbcd0ca4eb32224
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078211"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>演练：在命令行上编译 C++/CX 程序

> [!NOTE]
> 对于新 UWP 应用和组件，建议使用 [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)，这是 Windows 运行时 API 的 标准 C++17 语言投影。 C++/WinRT 从版本 1803 起在 Windows 10 SDK 中提供。 C++/WinRT 完全在头文件中实现，旨在提供对新式 Windows API 的优先访问权限。

Microsoft C++ 编译器 (MSVC) 支持 C++ 组件扩展 (C++/CX)，其中具有面向 Windows 运行时编程模型的其他类型和运算符。 可使用 C++/CX 为通用 Windows 平台 (UWP) 和 Windows 桌面生成应用。 有关详细信息，请参阅 [C++/CX 教程](https://msdn.microsoft.com/magazine/dn166929.aspx)和[运行时平台的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)。

在此演练中，你将使用文本编辑器创建一个基本的 C++/CX 程序，然后在命令行上对其进行编译。 （可使用你自己的 C++/CX 程序，而非键入显示的程序，或者也可使用来自另一篇帮助文章中的 C++/CX 代码示例。 这种技术有助于生成和测试不包含 UI 元素的小模块。）

> [!NOTE]
> 还可使用 Visual Studio IDE 来编译 C++/CX 程序。 由于 IDE 包含命令行上不可用的设计、调试、仿真和部署支持，因此建议使用 IDE 来生成通用 Windows 平台 (UWP) 应用。 有关详细信息，请参阅[在 C++ 中创建 UWP 应用](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

## <a name="prerequisites"></a>先决条件

了解 C++ 语言的基础知识。

## <a name="compiling-a-ccx-program"></a>编译 C++/CX 程序

若要启用 C++/CX 的编译，你必须使用 [/ZW](reference/zw-windows-runtime-compilation.md) 编译器选项。 MSVC 编译器将生成一个面向 Windows 运行时的 .exe 文件，并链接到所需的库。

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>在命令行上编译 C++/CX 应用程序

1. 打开“开发人员命令提示”  窗口。 （在“开始”  窗口上，打开“应用”  。 在你的 Visual Studio 版本下打开“Visual Studio Tools”  文件夹，然后选择“开发人员命令提示”  快捷方式。）有关如何打开“开发人员命令提示”窗口的详细信息，请参阅[通过命令行使用 MSVC 工具集](building-on-the-command-line.md)。

   可能需要管理员凭据才能成功编译此代码，取决于计算机的操作系统和配置。 若要以管理员身份运行命令提示窗口，请打开“开发人员命令提示”  的快捷菜单，然后选择“以管理员身份运行”  。

1. 在命令提示符下，输入 notepad basiccx.cpp  。

   在系统提示是否创建文件时，选择“是”  。

1. 在记事本中，输入以下行：

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. 在菜单栏上，选择“文件”   > “保存”  。

   你已创建使用 Windows 运行时 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)命名空间的 C++ 源文件。

1. 在命令提示符下，输入 cl /EHsc /ZW basiccx.cpp /link /SUBSYSTEM:CONSOLE  。 cl.exe 编译器将源代码编译到 .obj 文件中，然后运行链接器以生成名为 basiccx.exe 的可执行程序。 （[/EHsc](reference/eh-exception-handling-model.md) 编译器选项指定 C++ 异常处理模型，而 [/link](reference/link-pass-options-to-linker.md) 标志指定控制台应用程序。）

1. 若要运行 basiccx.exe 程序，请在命令提示符下，输入 basiccx  。

   该程序显示以下文本并退出：

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>请参阅

[项目和生成系统](projects-and-build-systems-cpp.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)
