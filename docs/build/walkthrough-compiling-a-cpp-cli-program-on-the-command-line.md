---
title: 演练：编译C++命令行上的 /CLI 程序
ms.date: 09/24/2018
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: c90d2c915db7264dc1b4e4807803e063c2a24fc7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314164"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>演练：编译C++命令行上的 /CLI 程序

可以创建面向公共语言运行时 (CLR) 并使用 .NET Framework 的 Visual C++ 程序，然后在命令行上生成这些程序。 Visual C++ 支持 C++/CLI 编程语言，它具有要面向 .NET 编程模型的其他类型和运算符。 有关一般信息C++/CLI 语言，请参阅[使用.NET 编程C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

在此演练中，你将使用文本编辑器创建一个基本的 C++/CLI 程序，然后在命令行上对其进行编译。 （可使用你自己的 C++/CLI 程序，而非键入显示的程序，或者也可使用来自另一篇帮助文章中的 C++/CLI 代码示例。 此方法可用于构建和测试不含 UI 元素的小模块连接）。

## <a name="prerequisites"></a>系统必备

了解的基础知识C++语言。

## <a name="compiling-a-ccli-program"></a>编译 C++/CLI 程序

以下步骤显示如何编译使用 .NET Framework 类的 C++/CLI 控制台应用程序。

若要启用用于编译C++/CLI，必须使用[/clr](reference/clr-common-language-runtime-compilation.md)编译器选项。 MSVC 编译器生成包含 MSIL 代码的.exe 文件，或混合 MSIL 和本机代码，并链接到所需的.NET Framework 库。

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>在命令行上编译 C++/CLI 应用程序

1. 打开**开发人员命令提示**窗口。 有关具体说明，请参阅[以打开开发人员命令提示窗口](building-on-the-command-line.md#developer_command_prompt)。

   可能需要管理员凭据才能成功编译此代码，取决于计算机的操作系统和配置。 若要以管理员身份运行命令提示符窗口中，右键单击以打开命令提示符的快捷菜单，然后选择**更多** > **以管理员身份运行**。

1. 在命令提示符处，输入 `notepad basicclr.cpp`。

   选择**是**时系统会提示创建一个文件。

1. 在记事本中，输入以下行：

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. 在菜单栏上依次选择**文件** > **保存**。

   你已创建视觉对象C++使用.NET Framework 类的源文件 (<xref:System.Console>) 中<xref:System>命名空间。

1. 在命令提示符处，输入 `cl /clr basicclr.cpp`。 cl.exe 编译器将源代码编译到包含 MSIL 的 .obj 文件中，然后运行链接器来生成名为 basicclr.exe 的可执行程序。

1. 若要运行 basicclr.exe 程序，请在命令提示符下，输入 `basicclr`。

   该程序显示以下文本并退出：

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[项目和生成系统](projects-and-build-systems-cpp.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)
