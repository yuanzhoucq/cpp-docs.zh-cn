---
title: "演练： 编译 C + + /cli CX 程序命令行上的 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 13e1b220123d3215e1c9150d00ee092ea4200ca8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>演练：在命令行上编译 C++/CX 程序
可以创建面向 Windows 运行时的 Visual C++ 程序，并在命令行上生成这些程序。 Visual C++ 支持 Visual C++ 组件扩展 (C++/CX)，其中具有面向 Windows 运行时编程模型的其他类型和运算符。 你可以使用 C + + /cli CX 生成适用于通用 Windows 平台 (UWP)、 Windows Phone 8.1 和 Windows 桌面应用。 有关详细信息，请参阅[教程的使用 + /cli CX](http://msdn.microsoft.com/magazine/dn166929.aspx)和[运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)。  
  
 在此演练中，你将使用文本编辑器创建一个基本的 C++/CX 程序，然后在命令行上对其进行编译。 （可使用你自己的 C++/CX 程序，而非键入显示的程序，或者也可使用来自另一篇帮助文章中的 C++/CX 代码示例。 这种技术有助于生成和测试不包含 UI 元素的小模块。）  
  
> [!NOTE]
>  还可使用 Visual Studio IDE 来编译 C++/CX 程序。 由于 IDE 包含设计、 调试、 仿真和在命令行不可用的部署支持，我们建议你使用 IDE 来生成通用 Windows 平台 (UWP) 应用。 有关详细信息，请参阅[在 c + + 中创建的 UWP 应用](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。  
  
## <a name="prerequisites"></a>系统必备  
 你必须了解 C++ 语言的基础知识。  
  
## <a name="compiling-a-ccx-program"></a>编译 C++/CX 程序  
 若要启用编译为 C + + /CX 中，你必须使用[/ZW](../build/reference/zw-windows-runtime-compilation.md)编译器选项。 Visual C++ 编译器将生成一个面向 Windows 运行时的 .exe 文件，并链接到所需的库。  
  
#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>在命令行上编译 C++/CX 应用程序  
  
1.  打开**开发人员命令提示**窗口。 (在**启动**窗口中，打开**应用**。 打开**Visual Studio Tools**文件夹在你的版本[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，然后选择**开发人员命令提示**快捷方式。)有关如何打开开发人员命令提示窗口的详细信息，请参阅[命令行上的生成 C/c + + 代码](../build/building-on-the-command-line.md)。  
  
     可能需要管理员凭据才能成功编译此代码，取决于计算机的操作系统和配置。 若要以管理员身份运行命令提示符窗口，打开快捷菜单**开发人员命令提示**，然后选择**以管理员身份运行**。  
  
2.  在命令提示符处，输入**notepad basiccx.cpp**。  
  
     选择**是**提示你创建文件时。  
  
3.  在记事本中，输入以下行：  
  
    ```cpp  
    using namespace Platform;  
  
    int main(Platform::Array<Platform::String^>^ args)  
    {  
        Platform::Details::Console::WriteLine("This is a C++/CX program.");  
    }  
  
    ```  
  
4.  在菜单栏上，选择**文件**，**保存**。  
  
     创建使用 Windows 运行时的 Visual c + + 源文件[平台命名空间](../cppcx/platform-namespace-c-cx.md)命名空间。  
  
5.  在命令提示符处，输入**cl /EHsc /ZW basiccx.cpp /link /SUBSYSTEM:CONSOLE**。 cl.exe 编译器将源代码编译到 .obj 文件中，然后运行链接器以生成名为 basiccx.exe 的可执行程序。 ( [/EHsc](../build/reference/eh-exception-handling-model.md)编译器选项指定 c + + 异常处理模型和[/链接](../build/reference/link-pass-options-to-linker.md)标志指定控制台应用程序。)  
  
6.  若要运行 basiccx.exe 程序，在命令提示符处，输入**basiccx**。  
  
     该程序显示以下文本并退出：  
  
    ```Output  
    This is a C++/CX program.  
    ```  
  
## <a name="see-also"></a>请参阅  
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)   
 [编译器选项](../build/reference/compiler-options.md)