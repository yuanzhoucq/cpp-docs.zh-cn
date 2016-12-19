---
title: "演练：在命令行上编译 C++/CLI 程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
caps.latest.revision: 11
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：在命令行上编译 C++/CLI 程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以创建面向公共语言运行时 \(CLR\) 并使用 .NET Framework 的 Visual C\+\+ 程序，然后在命令行上生成这些程序。  Visual C\+\+ 支持 C\+\+\/CLI 编程语言，它具有要面向 .NET 编程模型的其他类型和运算符。  有关 C\+\+\/CLI 语言的介绍，请参阅[纯 C\+\+：Hello, C\+\+\/CLI](http://msdn.microsoft.com/magazine/cc163681.aspx)。  有关一般信息，请参阅 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。  
  
 在此演练中，你将使用文本编辑器创建一个基本的 C\+\+\/CLI 程序，然后在命令行上对其进行编译。  （可使用你自己的 C\+\+\/CLI 程序，而非键入显示的程序，或者也可使用来自另一篇帮助文章中的 C\+\+\/CLI 代码示例。  这种技术有助于生成和测试不包含 UI 元素的小模块。）  
  
> [!NOTE]
>  还可使用 Visual Studio IDE 来编译 C\+\+\/CLI 程序。  有关详细信息，请参阅[演练：在 Visual Studio 中编译面向 CLR 的 C\+\+ 程序](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md)。  
  
## 系统必备  
 你必须了解 C\+\+ 语言的基础知识。  
  
## 编译 C\+\+\/CLI 程序  
 以下步骤显示如何编译使用 .NET Framework 类的 C\+\+\/CLI 控制台应用程序。  
  
 若要启用 C\+\+\/CLI 的编译，你必须使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 编译器选项。  Visual C\+\+ 编译器将生成包含 MSIL 代码（或 混合 MSIL 和本机代码）的 .exe 文件，并链接到所需的 .NET Framework 库。  
  
#### 在命令行上编译 C\+\+\/CLI 应用程序  
  
1.  打开“开发人员命令提示”窗口。  （在“开始”窗口上，打开“应用程序”。  在你的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本下打开“Visual Studio Tools”文件夹，然后选择“开发人员命令提示”快捷方式。）有关如何打开命令提示符窗口的详细信息，请参阅 [为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
     可能需要管理员凭据才能成功编译此代码，取决于计算机的操作系统和配置。  若要以管理员身份运行“命令提示符”窗口，请打开“开发人员命令提示”的快捷菜单，然后选择“以管理员身份运行”。  
  
2.  在命令提示符处，输入 **notepad basicclr.cpp**。  
  
     在系统提示是否创建文件时，选择“是”。  
  
3.  在记事本中，输入以下行：  
  
    ```  
    int main()  
    {  
        System::Console::WriteLine("This is a C++/CLI program.");  
    }  
    ```  
  
4.  在菜单栏中，依次选择“文件”和“保存”。  
  
     你已经在 <xref:System> 命名空间中创建了一个使用 .NET Framework 类 \(<xref:System.Console>\) 的 Visual C\+\+ 源文件。  
  
5.  在命令提示符处，输入 **cl \/clr basicclr.cpp**。  cl.exe 编译器将源代码编译到包含 MSIL 的 .obj 文件中，然后运行链接器来生成名为 basicclr.exe 的可执行程序。  
  
6.  若要运行 basicclr.exe 程序，请在命令提示符下，输入 **basicclr**。  
  
     该程序显示以下文本并退出：  
  
  **这是 C\+\+\/CLI 程序。**  
  
## 请参阅  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C\/C\+\+ 程序](../build/building-c-cpp-programs.md)   
 [编译器选项](../build/reference/compiler-options.md)