---
title: "演练：创建和使用静态库 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "库 [C++]，静态"
  - "静态库 [C++]"
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
caps.latest.revision: 38
caps.handback.revision: 38
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：创建和使用静态库 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此分步演练演示如何创建用于 C\+\+ 应用的静态库（.lib 文件）。 使用静态库是重用代码的一种绝佳方式。 你不必在要求功能的每个应用中重新实现同一例程，而只需将其写入静态数据库一次，然后从应用引用它们即可。 从静态库链接的代码成为了应用的一部分，这样你就不必安装另一个文件来使用代码。  
  
 本演练涵盖以下任务：  
  
-   [创建静态库项目](#BKMK_CreateLibProject)  
  
-   [向静态库添加类](#BKMK_AddClassToLib)  
  
-   [创建引用静态库的 C++ 控制台应用](#BKMK_CreateAppToRefTheLib)  
  
-   [在应用中使用静态库的功能](#BKMK_UseLibInApp)  
  
-   [运行应用程序](#BKMK_RunApp)  
  
## 系统必备  
 你需要了解 C\+\+ 语言的基础知识。  
  
##  <a name="BKMK_CreateLibProject"></a> 创建静态库项目  
  
#### 创建静态库项目  
  
1.  在菜单栏上，依次选择“文件”、“新建”、“项目”。  
  
2.  在**“新建项目”**对话框的左窗格中，依次展开**“已安装”**、**“模板”**、**“Visual C\+\+”**，然后选择**“Win32”**。  
  
3.  在中间窗格中，选择**“Win32 控制台应用程序”**。  
  
4.  在**“名称”**框中为项目指定名称，例如 **MathFuncsLib**。 在**“解决方案名称”**框中为解决方案指定名称，例如 **StaticLibrary**。 选择“确定”按钮。  
  
5.  在**“Win32 应用程序向导”**对话框的**“概述”**页上，选择**“下一步”**按钮。  
  
6.  在**“应用程序设置”**页的**“应用程序类型”**下，选择**“静态库”**。  
  
7.  在**“应用程序设置”**页的**“附加选项”**下，清除**“预编译头”**复选框。  
  
8.  选择**“完成”**按钮创建项目。  
  
##  <a name="BKMK_AddClassToLib"></a> 向静态库添加类  
  
#### 向静态库添加类  
  
1.  若要为新类创建头文件，请在**“解决方案资源管理器”**中打开 **MathFuncsLib** 项目的快捷菜单，然后依次选择**“添加”**、**“新建项”**。 在**“添加新项”**对话框的左窗格中，在**“Visual C\+\+”**下选择**“代码”**。 在中间窗格中，选择**“头文件\(.h\)”**。 为头文件指定名称（例如 **MathFuncsLib.h**），然后选择**“添加”**按钮。 将显示一个空白头文件。  
  
2.  添加一个名为 **MyMathFuncs** 的类以执行常见的算术运算（例如加、减、乘和除）。 代码应类似如下:  
  
     [!CODE [NVC_Walkthrough_Create_Static_Lib#100](../CodeSnippet/VS_Snippets_Cpp/nvc_walkthrough_create_static_lib#100)]  
  
3.  若要为新类创建源文件，请在**“解决方案资源管理器”**中打开 **MathFuncsLib** 项目的快捷菜单，然后依次选择**“添加”**、**“新建项”**。 在**“添加新项”**对话框的左窗格中，在**“Visual C\+\+”**下选择**“代码”**。 在中间窗格中，选择**“C\+\+ 文件\(.cpp\)”**。 为源文件指定名称（例如 **MathFuncsLib.cpp**），然后选择**“添加”**按钮。 将显示一个空白源文件。  
  
4.  请使用此源文件实现 **MyMathFuncs** 的功能。 代码应类似如下:  
  
     [!CODE [NVC_Walkthrough_Create_Static_Lib#110](../CodeSnippet/VS_Snippets_Cpp/nvc_walkthrough_create_static_lib#110)]  
  
5.  编译此静态库，在菜单栏上依次选择**“生成”**、**“生成解决方案”**。 这将创建一个可供其他程序使用的静态库。  
  
    > [!NOTE]
    >  如果使用 Visual Studio 命令行生成，必须分两个步骤来生成程序。 首先，运行 **cl \/c \/EHsc MathFuncsLib.cpp** 以编译代码并创建名为 **MathFuncsLib.obj** 的对象文件。 （**cl** 命令可调用编译器 Cl.exe，并且 **\/c** 选项可指定编译而无需链接。 有关详细信息，请参阅 [\/c（在不链接的情况下进行编译）](../build/reference/c-compile-without-linking.md)。） 接下来，运行 **lib MathFuncsLib.obj** 以链接代码并创建静态库 **MathFuncsLib.lib**。 （**lib** 命令可调用库管理器 Lib.exe。 有关详细信息，请参阅 [LIB 引用](../build/reference/lib-reference.md)。）  
  
##  <a name="BKMK_CreateAppToRefTheLib"></a> 创建引用静态库的 C\+\+ 控制台应用  
  
#### 创建引用静态库的 C\+\+ 控制台应用  
  
1.  在菜单栏上，依次选择“文件”、“新建”、“项目”。  
  
2.  在左窗格中的**“Visual C\+\+”**下，选择**“Win32”**。  
  
3.  在中间窗格中，选择**“Win32 控制台应用程序”**。  
  
4.  在**“名称”**框中为项目指定名称，例如 **MyExecRefsLib**。 在**“解决方案”**旁的下拉列表中选择**“添加到解决方案”**。 这会将新项目添加到包含此静态库的解决方案。 选择“确定”按钮。  
  
5.  在**“Win32 应用程序向导”**对话框的**“概述”**页上，选择**“下一步”**按钮。  
  
6.  在**“应用程序设置”**页的**“应用程序类型”**下，选择**“控制台应用程序”**。  
  
7.  在**“应用程序设置”**页的**“附加选项”**下，清除**“预编译头”**复选框。  
  
8.  选择**“完成”**按钮创建项目。  
  
##  <a name="BKMK_UseLibInApp"></a> 在应用中使用静态库的功能  
  
#### 在应用中使用静态库的功能  
  
1.  创建控制台应用后，将为你创建一个空程序。 源文件的名称与你之前选择的名称相同。 在此示例中，源文件名为 **MyExecRefsLib.cpp**。  
  
2.  必须引用静态库才能使用其中的算术例程。 为此，请在**“解决方案资源管理器”**中打开 **MyExecRefsLib** 项目的快捷菜单，然后选择**“引用”**。 在 **MyExecRefsLib“属性页”**对话框中，展开**“通用属性”**节点，选择**“框架和引用”**，然后选择**“添加新引用”**按钮。 有关**“引用”**对话框的更多信息，请参见 [添加引用](../ide/adding-references-in-visual-cpp-projects.md)。  
  
3.  **“添加引用”**对话框列出了可以引用的库。**“项目”**选项卡列出了当前解决方案中的所有项目以及它们包含的所有库。 在**“项目”**选项卡上，选中**“MathFuncsLib”**复选框，然后选择**“确定”**按钮。  
  
4.  若要引用 **MathFuncsLib.h** 头文件，必须修改包含的目录路径。 在 **MyExecRefsLib“属性页”**对话框中，依次展开**“配置属性”**节点和**“C\/C\+\+”**节点，然后选择**“常规”**。 在**“附加包含目录”**旁，指定 **MathFuncsLib** 目录的路径或浏览至该目录。  
  
     若要浏览至目录路径，请打开属性值下拉列表框，然后选择**“编辑”**。 在**“附加包含目录”**对话框中，在文本框中选择一个空行，然后选择行尾的省略号按钮 \(**…**\)。 在**“选择目录”**对话框中，选择 **MathFuncsLib** 目录，然后选择**“选择文件夹”**按钮以保存所做选择并关闭对话框。 在**“附加包含目录”**对话框中，选择**“确定”**按钮，然后在**“属性页”**对话框中，选择**“确定”**按钮以保存对该项目进行的更改。  
  
5.  现在即可在此应用中使用 **MyMathFuncs** 类。 为此，请将 **MyExecRefsLib.cpp** 的内容替换为以下代码：  
  
     [!CODE [NVC_Walkthrough_Create_Static_Lib#120](../CodeSnippet/VS_Snippets_Cpp/nvc_walkthrough_create_static_lib#120)]  
  
6.  通过在菜单栏上依次选择**“生成”**、**“生成解决方案”**来生成可执行文件。  
  
##  <a name="BKMK_RunApp"></a> 运行应用程序  
  
#### 运行应用  
  
1.  在**“解决方案资源管理器”**中打开 **MyExecRefsLib** 的快捷菜单，然后选择**“设为启动项目”**，确保选择 **MyExecRefsLib** 作为默认项目。  
  
2.  若要运行项目，请在菜单栏上依次选择**“调试”**、**“开始执行\(不调试\)”**。 输出应该与下面的内容类似：  
  
    ```Output  
    a + b = 106.4 a - b = -91.6 a * b = 732.6 a / b = 0.0747475  
    ```  
  
## 请参阅  
 [Visual C\+\+ 指导教程](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [演练：创建和使用动态链接库 \(C\+\+\)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)   
 [Windows 桌面应用程序 \(Visual C\+\+\)](../windows/desktop-applications-visual-cpp.md)