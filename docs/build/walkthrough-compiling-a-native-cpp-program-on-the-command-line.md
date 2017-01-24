---
title: "演练：在命令行上编译本机 C++ 程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令行应用程序 [C++], 本机"
  - "编译程序 [C++]"
  - "本机代码 [C++]"
  - "Visual C++, 本机代码"
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
caps.latest.revision: 63
caps.handback.revision: 57
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：在命令行上编译本机 C++ 程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 包括一个命令行 C\+\+ 编译器，可用来创建基本控制台应用、通用 Windows 应用、Windows 应用商店应用和 .NET 组件等的各种程序。  
  
 在此演练中，你将使用文本编辑器创建一个基本的 Visual C\+\+ 控制台程序，然后在命令行上对其进行编译。  
  
> [!NOTE]
>  还可以使用 Visual Studio 集成开发环境 \(IDE\) 来编译 Visual C\+\+ 程序。 有关更多信息，请参见[演练：使用项目和解决方案 \(C\+\+\)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)。  
  
 在此演练中，可使用你自己的 Visual C\+\+ 程序（而非键入显示的程序），也可使用另一个帮助文章中的 Visual C\+\+ 代码示例。  
  
## 系统必备  
 若要完成本演练中，必须具有包括 Visual C\+\+ 组件的 Visual Studio 版本。 了解 C\+\+ 语言的基础知识对你很有帮助。 这些说明的前提是你在使用 Windows 10 和 Visual Studio 2015，不过，适用于其他环境和版本的说明相似。  
  
### 创建 Visual C\+\+ 源文件并在命令行上对其进行编译  
  
1.  首先，打开“开发人员命令提示”。 Visual C\+\+ 编译器需要特殊的命令环境来运行，因此，不能在本演练中使用常规的命令提示。  
  
     在 Windows“启动”菜单上，打开“所有应用”。 滚动以查找并打开你的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本的“Visual Studio”文件夹，然后选择“开发人员命令提示”快捷方式。  
  
2.  创建一个新目录来保存你的程序。 在“开发人员命令提示”窗口中，输入 `cd \` 命令，以将目录更改为驱动器根目录。 输入 `md examples` 命令，以创建示例代码的目录。 然后输入 `cd examples` 命令，以使其成为当前工作目录。 这就是第一个程序运行的位置。  
  
3.  在命令提示处，输入 **notepad hello.cpp**。  
  
     在系统提示是否创建文件时，选择“是”。 这将打开一个空白的记事本窗口，可供你输入代码。  
  
4.  在记事本中，输入以下行：  
  
    ```cpp  
    #include <iostream> using namespace std; void main() { cout << "Hello, world, from Visual C++!" << endl; }  
    ```  
  
     这是一个非常简单的程序，会在屏幕上写入一行文本，然后退出。 为了尽量减少错误，请将此代码复制并粘贴到记事本中。  
  
5.  保存所有内容！ 在记事本中，在“文件”菜单上选择“保存”。  
  
     这样就创建了一个 Visual C\+\+ 源文件。  
  
6.  在命令提示处，输入 `cl /EHsc hello.cpp` 来编译你的程序。  
  
     cl.exe 编译器会生成包含已编译代码的 .obj 文件，然后运行链接器来创建名为 basic.exe 的可执行程序。 此名称会显示在编译器显示的多行输出信息中。 编译器的输出应如下所示：  
  
    ```Output  
    Microsoft (R) C/C++ 优化编译器版本 19.00.23504 适用于 x86 版权所有 (C) Microsoft Corporation。  保留所有权利。 hello.cpp Microsoft (R) 增量链接器版本 14.00.23504.0 版权所有 (C) Microsoft Corporation。  保留所有权利。 /out:hello.exe hello.obj  
    ```  
  
     如果有错误，请在记事本中检查代码，以确保它与示例匹配。 保存更改后再次运行编译器命令。  如果未找到 cl 命令，请验证你是否正在使用“开发人员命令提示”窗口，而不是常规的命令窗口。 如果尚未安装，则可能还需要在 Visual Studio 安装程序中安装 Visual C\+\+ 组件。  
  
7.  若要运行 hello.exe 程序，请在命令提示处输入 `hello`。  
  
     该程序显示以下文本并退出：  
  
    ```Output  
    Hello, world, from Visual C++!  
    ```  
  
     祝贺你，你已经创建并编译使用命令行工具的程序。  
  
## 后续步骤  
 有关如何打开“开发人员命令提示”窗口来使用命令行工具的详细信息，请参阅 [为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
 可能需要管理员凭据才能成功编译此演练中的代码，具体取决于计算机的操作系统和配置。 若要以管理员身份运行“开发人员命令提示”窗口，请右键单击以打开“开发人员命令提示”的快捷菜单，然后选择“以管理员身份运行”。  
  
 **\/EHsc** 命令行选项指示编译器启用 C\+\+ 异常处理。 有关详细信息，请参阅[\/EH（异常处理模型）](../build/reference/eh-exception-handling-model.md)。  
  
## 请参阅  
 [Visual C\+\+ 指导教程](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C\/C\+\+ 程序](../build/building-c-cpp-programs.md)   
 [编译器选项](../build/reference/compiler-options.md)