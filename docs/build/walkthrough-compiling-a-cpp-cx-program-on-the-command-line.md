---
title: 演练：编译C++命令行上的 /CX 程序
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: cbf5a48de3c029e36fc6daabe2b3f0db55dc173c
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877168"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>演练：编译C++命令行上的 /CX 程序

> [!NOTE] 
> 对于新的 UWP 应用和组件，我们建议你使用[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)，为 Windows 运行时 Api 的标准 C + + 17 语言投影。 C++/ WinRT 是 Windows 10 SDK 版本 1803年以后从中可用。 C++/ WinRT 完全在标头文件中实现，它旨在提供对新式 Windows API 的优先访问权限。

MicrosoftC++编译器 (MSVC) 支持C++组件扩展 (C++/CX)，其中具有面向 Windows 运行时编程模型的其他类型和运算符。 可以使用C++/CX 来生成适用于通用 Windows 平台 (UWP) 和 Windows 桌面应用。 有关详细信息，请参阅[的 c + 教程 + /cli CX](https://msdn.microsoft.com/magazine/dn166929.aspx)并[运行时平台的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)。

在此演练中，你将使用文本编辑器创建一个基本的 C++/CX 程序，然后在命令行上对其进行编译。 （可使用你自己的 C++/CX 程序，而非键入显示的程序，或者也可使用来自另一篇帮助文章中的 C++/CX 代码示例。 此方法可用于构建和测试不含 UI 元素的小模块连接）。

> [!NOTE]
> 还可使用 Visual Studio IDE 来编译 C++/CX 程序。 由于 IDE 包含设计、 调试、 仿真和部署支持的命令行上不可用，因此我们建议使用 IDE 来生成通用 Windows 平台 (UWP) 应用。 有关详细信息，请参阅[创建的 UWP 应用中C++ ](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

## <a name="prerequisites"></a>系统必备

了解的基础知识C++语言。

## <a name="compiling-a-ccx-program"></a>编译 C++/CX 程序

若要启用用于编译C++/CX，必须使用[/ZW](reference/zw-windows-runtime-compilation.md)编译器选项。 MSVC 编译器将生成面向 Windows 运行时，并链接到所需的库的.exe 文件。

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>在命令行上编译 C++/CX 应用程序

1. 打开**开发人员命令提示**窗口。 (在**启动**窗口中，打开**应用**。 打开**Visual Studio Tools**下你的 Visual Studio 版本的文件夹，然后选择**开发人员命令提示**快捷方式。)有关如何打开开发人员命令提示窗口的详细信息，请参阅[使用命令行中的 MSVC 工具集](building-on-the-command-line.md)。

   可能需要管理员凭据才能成功编译此代码，取决于计算机的操作系统和配置。 若要以管理员身份运行命令提示符窗口中，打开快捷菜单**开发人员命令提示**，然后选择**以管理员身份运行**。

1. 在命令提示符处，输入**notepad basiccx.cpp**。

   选择**是**时系统会提示创建一个文件。

1. 在记事本中，输入以下行：

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. 在菜单栏上依次选择**文件** > **保存**。

   已创建C++使用 Windows 运行时的源文件[平台命名空间](../cppcx/platform-namespace-c-cx.md)命名空间。

1. 在命令提示符处，输入**cl /EHsc /ZW basiccx.cpp /link /subsystem: console**。 cl.exe 编译器将源代码编译到 .obj 文件中，然后运行链接器以生成名为 basiccx.exe 的可执行程序。 ( [/EHsc](reference/eh-exception-handling-model.md)编译器选项指定C++异常处理模型，并[/link](reference/link-pass-options-to-linker.md)标志指定控制台应用程序。)

1. 若要运行 basiccx.exe 程序，在命令提示符处，输入**basiccx**。

   该程序显示以下文本并退出：

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>请参阅

[项目和生成系统](projects-and-build-systems-cpp.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)
