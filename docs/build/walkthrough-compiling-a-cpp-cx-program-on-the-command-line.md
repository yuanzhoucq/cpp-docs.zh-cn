---
title: "演练：在命令行上编译 C++/CX 程序 | Microsoft Docs"
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
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：在命令行上编译 C++/CX 程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以创建面向 Windows 运行时的 Visual C\+\+ 程序，并在命令行上生成这些程序。  Visual C\+\+ 支持 Visual C\+\+ 组件扩展 \(C\+\+\/CX\)，其中具有面向 Windows 运行时编程模型的其他类型和运算符。  可使用 C\+\+\/CX 生成 Windows Phone 8.1、Windows 应用商店和 Windows 桌面的应用程序。  有关详细信息，请参阅 [C\+\+\/CX 教程](http://msdn.microsoft.com/magazine/dn166929.aspx)和[适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)。  
  
 在此演练中，你将使用文本编辑器创建一个基本的 C\+\+\/CX 程序，然后在命令行上对其进行编译。  （可使用你自己的 C\+\+\/CX 程序，而非键入显示的程序，或者也可使用来自另一篇帮助文章中的 C\+\+\/CX 代码示例。  这种技术有助于生成和测试不包含 UI 元素的小模块。）  
  
> [!NOTE]
>  还可使用 Visual Studio IDE 来编译 C\+\+\/CX 程序。  由于 IDE 包含设计、调试、仿真和命令行上不可用的部署支持，因此我们建议使用 IDE 来生成 Windows 应用商店应用程序。  有关详细信息，请参阅 [Create a basic C\+\+ Store app](http://msdn.microsoft.com/library/windows/apps/dn263168)。  
  
## 系统必备  
 你必须了解 C\+\+ 语言的基础知识。  
  
## 编译 C\+\+\/CX 程序  
 若要启用 C\+\+\/CX 的编译，你必须使用 [\/ZW](../build/reference/zw-windows-runtime-compilation.md) 编译器选项。  Visual C\+\+ 编译器将生成一个面向 Windows 运行时的 .exe 文件，并链接到所需的库。  
  
#### 在命令行上编译 C\+\+\/CX 应用程序  
  
1.  打开“开发人员命令提示”窗口。  （在“开始”窗口上，打开“应用程序”。  在你的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本下打开“Visual Studio Tools”文件夹，然后选择“开发人员命令提示”快捷方式。）有关如何打开命令提示符窗口的详细信息，请参阅 [为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
     可能需要管理员凭据才能成功编译此代码，取决于计算机的操作系统和配置。  若要以管理员身份运行“命令提示符”窗口，请打开“开发人员命令提示”的快捷菜单，然后选择“以管理员身份运行”。  
  
2.  在命令提示符处，输入 **notepad basiccx.cpp**。  
  
     在系统提示是否创建文件时，选择“是”。  
  
3.  在记事本中，输入以下行：  
  
    ```cpp  
    using namespace Platform;  
  
    int main(Platform::Array<Platform::String^>^ args)  
    {  
        Platform::Details::Console::WriteLine("This is a C++/CX program.");  
    }  
  
    ```  
  
4.  在菜单栏中，依次选择“文件”和“保存”。  
  
     你已创建使用 Windows 运行时 [Platform 命名空间](../Topic/Platform%20namespace%20\(C++-CX\).md) 命名空间的 Visual C\+\+ 源文件。  
  
5.  在命令提示符处，输入 **cl \/EHsc \/ZW basiccx.cpp \/link \/SUBSYSTEM:CONSOLE**。  cl.exe 编译器将源代码编译到 .obj 文件中，然后运行链接器以生成名为 basiccx.exe 的可执行程序。  （[\/EHsc](../build/reference/eh-exception-handling-model.md) 编译器选项指定 C\+\+ 异常处理模型，而 [\/link](../build/reference/link-pass-options-to-linker.md) 标志指定控制台应用程序。）  
  
6.  若要运行 basiccx.exe 程序，请在命令提示符处，输入 **basiccx**。  
  
     该程序显示以下文本并退出：  
  
  **这是 C\+\+\/CX 程序。**  
  
## 请参阅  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C\/C\+\+ 程序](../build/building-c-cpp-programs.md)   
 [编译器选项](../build/reference/compiler-options.md)