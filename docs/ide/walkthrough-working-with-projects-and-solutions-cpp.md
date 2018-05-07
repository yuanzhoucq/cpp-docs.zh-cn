---
title: 演练： 使用项目和解决方案 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 12/13/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f62b2317669949473c8b0e68ad4410a3d9b03806
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>演练：使用项目和解决方案 (C++)

此处介绍如何在 Visual Studio 中创建 C++ 项目，添加代码，然后生成并运行该项目。 本演练中的项目是一个程序，该程序跟踪正在玩各种纸牌游戏的玩家数量。

在 Visual Studio 中，工作组织为项目和解决方案。 一个解决方案可以包含多个项目，例如，一个 DLL 和一个引用该 DLL 的可执行文件。 有关详细信息，请参阅[解决方案和项目](/visualstudio/ide/solutions-and-projects-in-visual-studio)。

## <a name="before-you-start"></a>准备工作

若要完成本演练，你需要 Visual Studio 2017 版本 15.3 或更高版本。 如果你需要副本，此处是简短的指南： [Visual Studio 中的安装 c + + 支持](../build/vscpp-step-0-installation.md)。 如果尚未为执行操作，请按照下一步的步骤通过"Hello，World"教程，若要确保正确安装 Visual c + + 和它的安装后都能正常工作。

如果你了解 c + + 语言的基础知识并且知道编译器、 链接器和调试器的用途是什么，它可帮助。 本教程还假定你熟悉 Windows 以及如何使用菜单，对话框

## <a name="create-a-project"></a>创建项目

若要创建项目，请先选择项目类型模板。 对于每个项目类型，Visual Studio 设置编译器设置和-根据的类型-生成起始代码，你稍后可以进行修改。

### <a name="to-create-a-project"></a>创建项目

1. 在菜单栏上，选择**文件 > 新建 > 项目**。

1. 在左窗格中**新项目**对话框框中，展开**已安装**和选择**Visual c + +**，如果它尚未打开。

1. 在中心窗格中的已安装模板列表中，选择**Windows 控制台应用程序**。

1. 输入中的项目的名称**名称**框。 对于此示例中，输入**游戏**。

   你可以接受中的默认位置**位置**下拉列表中，输入一个不同的位置，或选择**浏览**按钮以浏览到你想要保存项目的目录。

   当你创建项目时，Visual Studio 会在解决方案中将项目。 默认情况下，解决方案的名称与项目名称相同。 你可以更改中的名称**解决方案名称**框中，但对于本例，请保留默认名称。

1. 选择**“确定”**按钮，创建单元测试项目。

   Visual Studio 创建新解决方案和项目文件，并打开它生成 Game.cpp 源代码文件的编辑器。

## <a name="organize-projects-and-files"></a>项目和文件组织

你可以使用**解决方案资源管理器**来组织和管理项目、 文件和你的解决方案中的其他资源。

本部分演练演示如何将类添加到项目中。 当你添加类时，Visual Studio 将添加相应的.h 和.cpp 文件。 你可以看到中的结果**解决方案资源管理器**。

### <a name="to-add-a-class-to-a-project"></a>向项目添加类

1. 如果**解决方案资源管理器**窗口未显示在 Visual Studio 中，在菜单栏上，选择**视图 > 解决方案资源管理器**。

1. 在**解决方案资源管理器**，选择**游戏**项目。 在菜单栏上，选择**项目 > 添加类**。

1. 在**添加类**对话框中，输入*Cardgame*中**类名**框。 请勿修改默认的文件名和设置。 选择“确定”  按钮。

   Visual Studio 创建新的文件，并将它们添加到你的项目。 你可以看到在**解决方案资源管理器**窗口。 在编辑器中打开 Cardgame.h 和 Cardgame.cpp 文件。

1. 编辑 Cardgame.h 文件，并进行这些更改：

   - 在类定义的左大括号之后添加两个私有数据成员。
      <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - 修改 Visual Studio 生成的默认构造函数。 在 `public:` 访问说明符之后，将发现如下所示的行：

      `Cardgame();`

      修改此构造函数以使用一个类型的参数`int`命名*播放器*。

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - 默认析构函数之后，添加内联声明为`static int`成员函数名为*GetParticipants*用于不带任何参数并返回`totalParticipants`值。

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   在你对 Cardgame.h 文件进行更改之后，该文件应类似于：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->
   ```cpp
   #pragma once
   class Cardgame
   {
       int players;
       static int totalParticipants;
   public:
       Cardgame(int players);
       ~Cardgame(void);
       static int GetParticipants() { return totalParticipants; }
   };
   ```

   行`#pragma once`告知编译器将该标头文件包括一次。 有关详细信息，请参阅[后](../preprocessor/once.md)。 有关此标头文件中的其他 c + + 关键字的信息，请参阅[类](../cpp/class-cpp.md)， [int](../cpp/fundamental-types-cpp.md)，[静态](../cpp/storage-classes-cpp.md)，和[公共](../cpp/public-cpp.md)。

1. 选择**Cardgame.cpp**在编辑窗格中打开进行编辑顶部的选项卡。

1. 删除文件中的所有内容，并用此代码替换：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->
   ```cpp
   #include "stdafx.h"
   #include "Cardgame.h"
   #include <iostream>

   using namespace std;

   int Cardgame::totalParticipants = 0;

   Cardgame::Cardgame(int players)
       : players(players)
   {
       totalParticipants += players;
       cout << players << " players have started a new game.  There are now "
            << totalParticipants << " players in total." << endl;
   }

   Cardgame::~Cardgame()
   {
   }
   ```

   > [!NOTE]
   > 输入代码时，可以使用自动完成功能。 例如，如果输入键盘上输入此代码，你可以输入*pl*或*tot*然后按 Ctrl + 空格键。 自动完成进入`players`或`totalParticipants`为你。

## <a name="add-test-code-to-your-main-function"></a>将测试代码添加到主函数

向应用程序测试新的函数中添加一些代码。

### <a name="to-add-test-code-to-the-project"></a>若要将测试代码添加到项目

1. 在 Game.cpp 编辑器窗口中，与此替换现有代码：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->
   ```cpp
   // Game.cpp : Defines the entry point for the console application.
   //

   #include "stdafx.h"
   #include "Cardgame.h"
   #include <iostream>

   using namespace std;

   void PlayGames()
   {
       Cardgame bridge(4);
       Cardgame blackjack(8);
       Cardgame solitaire(1);
       Cardgame poker(5);
   }

   int main()
   {
       PlayGames();
       return 0;
   }
   ```
此代码将添加一个测试函数， `PlayGames`、 源代码，并调用在`main`。 

## <a name="build-and-run-your-app-project"></a>生成并运行应用程序项目

接下来，生成项目并运行应用。

### <a name="to-build-and-run-the-project"></a>生成并运行此项目

1. 在菜单栏上，依次选择“生成”>“生成解决方案”。

   从生成的输出显示在**输出**窗口。 如果生成成功，输出应类似于：

   ```Output
   1>------ Build started: Project: Game, Configuration: Debug Win32 ------
   1>  stdafx.cpp
   1>  Game.cpp
   1>  Cardgame.cpp
   1>  Generating Code...
   1>  Game.vcxproj -> C:\Users\username\Source\Repos\Game\Debug\Game.exe
   ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
   ```

   **输出**窗口可以显示不同步骤，具体取决于生成配置，但是，如果项目生成成功，最后一行应类似于显示的输出。

   如果你的生成未成功，将比较你的代码与前面步骤中所示的代码。

1. 若要运行该项目，在菜单栏上，选择**调试 > 启动但不调试**。 应显示控制台窗口，并输出应类似如下：

   ```Output
   4 players have started a new game.  There are now 4 players in total.
   8 players have started a new game.  There are now 12 players in total.
   1 players have started a new game.  There are now 13 players in total.
   5 players have started a new game.  There are now 18 players in total.
   ```
按任意键关闭控制台窗口。

祝贺你，你已成功生成一个应用程序项目和解决方案。 继续本演练来了解有关如何生成 Visual Studio 中的 c + + 代码项目。

## <a name="next-steps"></a>后续步骤

**上一步：** [使用适用于 c + + 桌面开发的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
**下一步：** [演练： 生成项目 （c + +）](../ide/walkthrough-building-a-project-cpp.md)。

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)  
[生成 C/C++ 程序](../build/building-c-cpp-programs.md)