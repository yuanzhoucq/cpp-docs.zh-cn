---
title: "演练：使用项目和解决方案 (C++) | Microsoft Docs"
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
helpviewer_keywords: 
  - "项目 [C++]"
  - "项目 [C++], 关于项目"
  - "解决方案 [C++]"
  - "解决方案 [C++], 关于解决方案"
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：使用项目和解决方案 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此处介绍如何在 Visual Studio 中创建 C\+\+ 项目，添加代码，然后生成并运行该项目。  本演练中的项目是一个程序，该程序跟踪正在玩各种纸牌游戏的玩家数量。  
  
 在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中，可以将工作组织为项目和解决方案。  一个解决方案可以包含多个项目，例如，一个 DLL 和一个引用该 DLL 的可执行文件。  有关详细信息，请参阅[解决方案和项目](../Topic/Solutions%20and%20Projects%20in%20Visual%20Studio.md)。  
  
## 系统必备  
  
-   若要完成本演练，你必须了解 C\+\+ 语言的基础知识。  
  
## 创建项目  
 若要创建项目，请先选择项目类型模板。  对于各种项目类型，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 会根据类型设置编译器设置，生成起始代码，稍后你可以进行修改。  
  
#### 创建项目  
  
1.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**。  
  
2.  在**“新建项目”**对话框的左侧窗格中，依次展开**“已安装的模板”**节点、**“Visual C\+\+”节**点，然后选择**“Win32”**。  
  
3.  在已安装模板列表的中间窗格中，选择**“Win32 控制台应用程序”**。  
  
4.  在**“名称”**框中输入项目的名称。  对于此示例，请输入“游戏”。  
  
     你可以接受**“位置”**下拉列表中的默认位置，输入其他位置，或者选择**“浏览”**按钮，浏览要保存项目的目录。  
  
     当你创建项目时，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 会将该项目放入一个解决方案。  默认情况下，解决方案的名称与项目名称相同。  你可以更改**“解决方案名称”**框中的名称，但是对于此示例，请保留默认名称。  
  
     选择**“确定”**按钮，启动**“Win32 应用程序向导”**。  
  
5.  在**“Win32 应用程序向导”**的**“概述”**页面上，选择**“下一步”**按钮。  
  
6.  在**“应用程序设置”**页的**“应用程序类型”**下，选择**“控制台应用程序”**。  在**“其他选项”**下，清除**“预编译头”**设置，然后选择**“空项目”**设置。  选择**“完成”**按钮创建项目。  
  
     现在有了项目，但项目还没有源代码文件。  
  
## 组织解决方案中的项目和文件  
 你可以使用**“解决方案资源管理器”**来组织和管理解决方案中的项目、文件及其他资源。  
  
 本部分演练演示如何将类添加到项目中。  当你添加类时，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 将添加相应的 .h 和 .cpp 文件。  下面，为测试类的主程序添加一个源代码文件。  
  
#### 向项目添加类  
  
1.  如果未显示**“解决方案资源管理器”**，请在菜单栏上依次选择**“视图”**、**“解决方案资源管理器”**。  
  
2.  在**“解决方案资源管理器”**中，打开**“头文件”**文件夹的快捷菜单，然后依次选择**“添加”**、**“类”**。  
  
     在**“添加类”**对话框的左侧窗格中，展开**“Visual C\+\+”**节点，选择**“C\+\+”**，然后在已安装模板列表的中间窗格中选择**“C\+\+ 类”**。  选择**“添加”**按钮。  
  
3.  在**“通用 C\+\+ 类向导”**中，在**“类名称”**框中输入“Cardgame”。  请勿修改默认的文件名和设置。  选择**“完成”**按钮。  
  
4.  Cardgame.h 文件将在编辑器中打开。  进行以下更改：  
  
    -   在类定义的左大括号之后添加两个私有数据成员。  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)]  
  
    -   修改 Visual Studio 生成的默认构造函数。  在 `public:` 访问说明符之后，将发现如下所示的行：  
  
         `Cardgame(void);`  
  
         对其进行修改，使其带有一个类型为 `int`、以玩家命名的参数。  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]  
  
    -   在默认析构函数之后，为名为 GetParticipants 的静态 int 成员函数添加内联声明，该成员函数没有参数且返回 totalParticipants 值。  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]  
  
5.  在你对 Cardgame.h 文件进行更改之后，该文件应类似于：  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]  
  
     `#pragma once` 行通知编译器要包括文件，仅有一次。  有关详细信息，请参阅 [once](../preprocessor/once.md)。  
  
     有关此头文件中的其他 C\+\+ 关键字的信息，请参阅[类](../cpp/class-cpp.md)、[int](../cpp/fundamental-types-cpp.md)、[静态](../misc/static-cpp.md)和[公共](../cpp/public-cpp.md)。  
  
6.  在编辑窗格中选择**“Cardgame.cpp”**选项卡，打开进行编辑。  
  
7.  删除文件中的所有内容，并用此代码替换：  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]  
  
    > [!NOTE]
    >  输入代码时，可以使用自动完成功能。  例如，如果你正在输入此代码，可以输入 pl 或 tot，然后按 Ctrl\+Spacebar，这样自动完成功能就会帮你输入 `players` 或 `totalParticipants`。  
  
     有关 `#include` 的详细信息，请参阅 [\#include 指令](../preprocessor/hash-include-directive-c-cpp.md)。  
  
## 添加源文件  
 现在，为测试类的主程序添加一个源代码文件。  
  
#### 添加新源文件  
  
1.  在**“解决方案资源管理器”**中，打开**“源文件”**文件夹的快捷菜单，然后依次选择**“添加”**、**“新建项”**。  
  
     在**“添加新项”**对话框的左侧窗格中，依次展开**“已安装”**节点、**“Visual C\+\+”**节点，然后选择**“代码”**。  在中间窗格中，选择**“C\+\+ 文件\(.cpp\)”**。  
  
2.  在**“名称”**框中输入“TestGames.cpp”，然后选择**“添加”**按钮。  
  
3.  在 TestGames.cpp 编辑窗口中，键入以下代码。  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]  
  
## 生成并运行项目  
 现在，生成项目并运行应用程序。  
  
#### 生成并运行此项目  
  
1.  在菜单栏上，依次选择**“生成”**、**“生成解决方案”**。  
  
    > [!NOTE]
    >  如果使用不显示**“生成”**菜单的 Express 版，请在菜单栏上依次选择**“工具”**、**“设置”**、**“专家设置”**来启用。  
  
     来自生成的输出应显示在**“输出”**窗口中。  如果生成成功，输出应类似于：  
  
  **1\>\-\-\-\-\-\- 生成已开始: 项目: Game, 配置: Debug Win32 \-\-\-\-\-\-**  
**1\>  TestGames.cpp**  
**1\>  Cardgame.cpp**  
**1\>  正在生成代码...**  
**1\>  Game.vcxproj \-\> c:\\users\\username\\documents\\visual studio\\Projects\\Game\\Debug\\Game.exe**  
**\=\=\=\=\=\=\=\=\=\= 生成: 1 成功, 0 失败, 0 最新, 0 被跳过 \=\=\=\=\=\=\=\=\=\=**     **“输出”**窗口可以根据不同的版本和生成配置显示不同步骤，但是，如果项目生成成功，最后一行应类似于上面显示的输出。  
  
     如果生成未成功，请将你的代码与前面步骤中提供的代码进行比较。  
  
2.  若要运行项目，请在菜单栏上依次选择**“调试”**、**“开始执行\(不调试\)”**。  输出应该与下面的内容类似：  
  
  **4 个玩家开始了新游戏。现在共有 4 个玩家。**  
**8 个玩家开始了新游戏。现在共有 12 个玩家。**  
**1 个玩家开始了新游戏。现在共有 13 个玩家。**  
**5 个玩家开始了新游戏。现在共有 18 个玩家。**  
  
## 后续步骤  
 **上一部分：** [使用 Visual Studio IDE 进行 C\+\+ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  **下一部分：**[演练：生成项目 \(C\+\+\)](../ide/walkthrough-building-a-project-cpp.md)。  
  
## 请参阅  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)