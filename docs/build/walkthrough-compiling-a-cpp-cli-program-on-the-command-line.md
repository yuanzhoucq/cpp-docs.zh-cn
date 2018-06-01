---
title: 演练： 编译 C + + /cli 程序的程序命令行上 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46e4b8d6341ad659596f7e83ab3cdcb89b18df2d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705301"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>演练：在命令行上编译 C++/CLI 程序

可以创建面向公共语言运行时 (CLR) 并使用 .NET Framework 的 Visual C++ 程序，然后在命令行上生成这些程序。 Visual C++ 支持 C++/CLI 编程语言，它具有要面向 .NET 编程模型的其他类型和运算符。 有关常规 C + + 语言，请参阅[.NET 编程使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

在此演练中，你将使用文本编辑器创建一个基本的 C++/CLI 程序，然后在命令行上对其进行编译。 （可使用你自己的 C++/CLI 程序，而非键入显示的程序，或者也可使用来自另一篇帮助文章中的 C++/CLI 代码示例。 这种技术有助于生成和测试不包含 UI 元素的小模块。）

> [!NOTE]
> 还可使用 Visual Studio IDE 来编译 C++/CLI 程序。 有关详细信息，请参阅[演练： 编译面向 Visual Studio 中的 CLR 的 c + + 程序](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md)。

## <a name="prerequisites"></a>系统必备

你必须了解 C++ 语言的基础知识。

## <a name="compiling-a-ccli-program"></a>编译 C++/CLI 程序

以下步骤显示如何编译使用 .NET Framework 类的 C++/CLI 控制台应用程序。

若要启用编译为 C + + /cli CLI，你必须使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项。 Visual C++ 编译器将生成包含 MSIL 代码（或 混合 MSIL 和本机代码）的 .exe 文件，并链接到所需的 .NET Framework 库。

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>在命令行上编译 C++/CLI 应用程序

1. 打开**开发人员命令提示**窗口。 有关具体的说明，请参阅[打开开发人员命令提示符窗口](../build/building-on-the-command-line.md#developer_command_prompt)。

   可能需要管理员凭据才能成功编译此代码，取决于计算机的操作系统和配置。 若要以管理员身份运行命令提示符窗口，右键单击以打开命令提示符的快捷菜单，然后选择**详细**，**以管理员身份运行**。

1. 在命令提示符处，输入**记事本 basicclr.cpp**。

   选择**是**提示你创建文件时。

1. 在记事本中，输入以下行：

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. 在菜单栏上，选择**文件**，**保存**。

   你已经在 <xref:System.Console> 命名空间中创建了一个使用 .NET Framework 类 (<xref:System>) 的 Visual C++ 源文件。

1. 在命令提示符处，输入**cl /clr basicclr.cpp**。 cl.exe 编译器将源代码编译到包含 MSIL 的 .obj 文件中，然后运行链接器来生成名为 basicclr.exe 的可执行程序。

1. 若要运行 basicclr.exe 程序，请在命令提示符处，输入**basicclr**。

   该程序显示以下文本并退出：

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>请参阅

- [C++ 语言参考](../cpp/cpp-language-reference.md)
- [生成 C/C++ 程序](../build/building-c-cpp-programs.md)
- [编译器选项](../build/reference/compiler-options.md)
