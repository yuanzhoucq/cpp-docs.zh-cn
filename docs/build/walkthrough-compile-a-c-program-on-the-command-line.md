---
title: "演练：在命令行上编译 C 程序 | Microsoft Docs"
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
  - "C 程序编译 [C++]"
  - "命令行应用程序 [C++], C 程序"
  - "编译程序 [C++]"
  - "Visual C, 编译"
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
caps.latest.revision: 46
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：在命令行上编译 C 程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中包括一个 C 编译器，可用来创建从基本的控制台程序到 Windows 桌面应用程序的各种程序。  
  
 此演练演示如何使用文本编辑器创建一个基本的 C 程序，然后在命令行上对其进行编译。  
  
 你可以使用自己的 C 程序，而不是键入此演练中所示的示例程序。  也可以使用帮助主题中包含的任何 C 代码示例程序。  
  
 默认情况下，Visual C\+\+ 编译器将以 .c 结尾的所有文件视为 C 源代码，将以 .cpp 结尾的所有文件视为 C\+\+ 源代码。  若要强制编译器将所有文件视为 C（而不管文件扩展名如何），请使用 [\/Tc](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 编译器选项。  
  
## 系统必备  
 你必须了解 C 语言的基础知识。  
  
### 创建 C 源文件并在命令行上对其进行编译  
  
1.  打开“开发人员命令提示”。  在 Windows 8 中的**“开始”**屏幕上，打开**“Visual Studio Tools”**文件夹，然后选择**“开发人员命令提示”**快捷方式。  在 Windows 的早期版本中，选择**“开始”**按钮，依次展开**“所有程序”**、**Microsoft Visual Studio** 和 **Visual Studio Tools**，然后选择**“开发人员命令提示”**。  
  
     根据计算机上的 Windows 版本和系统安全配置，可能必须打开**“开发人员命令提示”**的快捷菜单，然后选择**“以管理员身份运行”**，才能成功生成和运行按下列步骤创建的应用程序。  
  
    > [!NOTE]
    >  **“开发人员命令提示”**会自动设置 C 编译器和所需的任何库的正确路径。  应使用它而不是使用普通的“命令提示符”窗口。  有关详细信息，请参阅[为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
2.  在命令提示符下，创建源文件的目录并使其成为当前工作目录。  例如，键入 **md c:\\simple** 并按 Enter 以创建名为 Simple 的目录，然后键入 **cd c:\\simple** 并按 Enter 以更改到此目录。  
  
3.  在命令提示符下，键入 **notepad** 并按 Enter。  
  
4.  在记事本中，输入下列各行。  
  
     [!code-cpp[NVC_Walkthrough_Compile_C#100](../build/codesnippet/CPP/walkthrough-compile-a-c-program-on-the-command-line_1.c)]  
  
5.  在菜单栏上，依次选择**“文件”**、**“保存”**以打开**“另存为”**对话框。  导航至已创建的目录。  在**“文件名”**框中，输入源文件的名称（例如 simple.c），然后在**“保存类型”**下拉列表中，选择**“所有文件\(\*.\*\)”**。  选择**“保存”**按钮以在工作目录中创建 C 源文件。  
  
6.  在命令提示符下，输入 **dir** 并按 Enter。  你应该看到所创建的源文件：  
  
  **C:\\simple\>dir**  
 **Volume in drive C has no label.  Volume Serial Number is CC62\-6545**  
 **Directory of C:\\simple**  
**10\/02\/2012  03:46 PM    \<DIR\>          .  10\/02\/2012  03:46 PM    \<DIR\>          ..  10\/02\/2012  03:36 PM               102 simple.c**  
 **1 File\(s\)            102 bytes**  
 **2 Dir\(s\)  514,900,566,016 bytes free**      在您的计算机上的详细信息将有所不同。  如果看不到源代码文件，请确保你已更改为所创建的目录，并确保以 .c 的文件扩展名将源文件保存在其中。  
  
7.  在命令提示符下，指定 **cl** 命令和源文件的名称（例如 **cl simple.c**），然后按 Enter 编译此程序。  cl.exe 编译器将生成一个包含已编译代码的 .obj 文件，然后运行链接器以生成具有源文件名称的可执行程序，但会具有 .exe 文件名扩展（例如 simple.exe）。  
  
     你可以在编译器显示的多行输出信息中看到可执行程序的名称。  
  
     **输出**  
  
  **适用于 x86 的 Microsoft\(R\) C\/C\+\+ 优化编译器版本 17.00.50727.1**  
**版权所有 \(C\) Microsoft Corporation。  保留所有权利。  simple.c**  
**Microsoft\(R\) 增量链接器版本 11.00.50727.1**  
**版权所有 \(C\) Microsoft Corporation。  保留所有权利。  \/out:simple.exe**  
**simple.obj**      这些工具的版本号取决于 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的版本以及已安装的任何更新。  
  
    > [!NOTE]
    >  如果遇到错误，如“'cl' 无法识别为内部或外部命令、可操作程序或批处理文件”、错误 C1034或错误 LNK1104，则必须设置编译器和工具的环境。  有关详细信息，请查看步骤 1。  
    >   
    >  如果您收到编译器错误或警告，请查看您有错误的源代码，然后将其保存并再次运行编译器。  有关特定错误的详细信息，请在此页上使用搜索框。  
  
8.  若要运行程序，请键入不带文件扩展名的名称（例如 **simple**），然后按 Enter。  
  
     程序将在显示以下文本后退出：  
  
     `This is a native C program.`  
  
## 请参阅  
 [演练：创建 Win32 控制台程序 \(C\+\+\)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)   
 [C 语言参考](../c-language/c-language-reference.md)   
 [生成 C\/C\+\+ 程序](../build/building-c-cpp-programs.md)   
 [兼容性](../c-runtime-library/compatibility.md)