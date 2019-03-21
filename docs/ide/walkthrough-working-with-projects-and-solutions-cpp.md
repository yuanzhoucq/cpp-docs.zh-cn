---
title: 演练：使用项目和解决方案 (C++)
ms.date: 09/14/2018
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 9408938b670d8130305f2e1c1258fc6fcb9875bb
ms.sourcegitcommit: 9e85c2e029d06b4c1c69837437468718b4d54908
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2019
ms.locfileid: "57820060"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>演练：使用项目和解决方案 (C++)

此处介绍如何在 Visual Studio 中创建 C++ 项目，添加代码，然后生成并运行该项目。 本演练中的项目是一个程序，该程序跟踪正在玩各种纸牌游戏的玩家数量。

在 Visual Studio 中，可以将工作组织为项目和解决方案。 一个解决方案可以包含多个项目，例如，一个 DLL 和一个引用该 DLL 的可执行文件。 有关详细信息，请参阅[解决方案和项目](/visualstudio/ide/solutions-and-projects-in-visual-studio)。

## <a name="before-you-start"></a>准备工作

要完成本演练，需要 Visual Studio 2017 版本 15.3 或更高版本。 如果需要副本，下面是简要指南：[在 Visual Studio 中安装 C++ 支持](../build/vscpp-step-0-installation.md)。 如果尚未安装，请按照通过“Hello, World”教程完成安装后的后续步骤操作，确保 Visual C++ 正确安装且正常工作。

了解 C++ 语言的基础知识以及编译器、链接器和调试程序的用途会很有帮助。 本教程还假定你熟悉 Windows 及其菜单、对话框的使用方式。

## <a name="create-a-project"></a>创建项目

若要创建项目，请先选择项目类型模板。 对于每种项目类型，Visual Studio 会设置编译器设置，并根据类型生成起始代码，稍后可修改该代码。

### <a name="to-create-a-project"></a>创建项目

1. 在菜单栏上，依次选择“文件” > “新建” > “项目”。

1. 在“新建项目”对话框的左窗格中展开“已安装”，并选择“Visual C++”（如果它尚未打开）。

1. 在中间窗格的已安装模板列表中，选择“Windows 控制台应用程序”。

   > [!NOTE]
   > 在以前版本的 Visual Studio 中，安装的模板被称为“Win32 控制台应用程序”。

1. 在“名称”框中输入项目的名称。 对于此示例，请输入“游戏”。

   可以接受“位置”下拉列表中的默认位置、输入其他位置或者选择“浏览”按钮，浏览要保存项目的目录。

   创建项目时，Visual Studio 将该项目放入一个解决方案。 默认情况下，解决方案的名称与项目名称相同。 可以更改“解决方案名称”框中的名称，但是对于此示例，请保留默认名称。

1. 选择 **“确定”** 按钮，创建单元测试项目。

   Visual Studio 创建新的解决方案和项目文件，并为它生成的 Game.cpp 源代码文件打开编辑器。

## <a name="organize-projects-and-files"></a>组织项目和文件

可以使用“解决方案资源管理器”来组织和管理解决方案中的项目、文件及其他资源。

本部分演练演示如何将类添加到项目中。 添加类时，Visual Studio 添加相应的 .h 和 .cpp 文件。 可以在“解决方案资源管理器”中查看结果。

### <a name="to-add-a-class-to-a-project"></a>向项目添加类

1. 如果 Visual Studio 中未显示“解决方案资源管理器”窗口，请在菜单栏上选择“视图” > “解决方案资源管理器”。

1. 在“解决方案资源管理器”中，选择“游戏”项目。 在菜单栏上选择“项目” > “添加类”。

1. 在“添加类”对话框中的“类名”框内输入“Cardgame”。 请勿修改默认的文件名和设置。 选择“确定”  按钮。

   Visual Studio 创建新的文件并将其添加到项目。 可以在“解决方案资源管理器”窗口中查看这些文件。 Cardgame.h 和 Cardgame.cpp 文件在编辑器中打开。

1. 编辑 Cardgame.h 文件，并进行以下更改：

   - 在类定义的左大括号之后添加两个私有数据成员。
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - 修改 Visual Studio 生成的默认构造函数。 在 `public:` 访问说明符之后，将发现如下所示的行：

      `Cardgame();`

      修改构造函数，使其带有一个类型为 `int`、名为“players”的参数。

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - 在默认析构函数之后，为名为 GetParticipants 的 `static int` 成员函数添加内联声明，该成员函数没有参数且返回 `totalParticipants` 值。

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   在你对 Cardgame.h 文件进行更改之后，该文件应类似于以下代码：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->

    ```cpp
    #pragma once
    class Cardgame
    {
        int players;
        static int totalParticipants;
    public:
        Cardgame(int players);
        ~Cardgame();
        static int GetParticipants() { return totalParticipants; }
    };
    ```

   `#pragma once` 行通知编译器仅包含一次头文件。 有关详细信息，请参阅 [once](../preprocessor/once.md)。 有关上述头文件中其他 C++ 关键字的信息，请参阅[类](../cpp/class-cpp.md)、[int](../cpp/fundamental-types-cpp.md)、[静态](../cpp/storage-classes-cpp.md)和[公共](../cpp/public-cpp.md)。

1. 选择编辑窗格顶部的“Cardgame.cpp”选项卡，打开它进行编辑。

1. 删除文件中的所有内容，并将其替换为以下代码：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h"
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
   > 输入代码时，可以使用自动完成功能。 例如，如果使用键盘输入此代码，可以输入 pl 或 tot，然后按 Ctrl+空格键。 自动完成功能可为你输入 `players` 或 `totalParticipants`。

## <a name="add-test-code-to-your-main-function"></a>向主函数添加测试代码

向应用添加一些测试新函数的代码。

### <a name="to-add-test-code-to-the-project"></a>向项目添加测试代码

1. 在 Game.cpp 编辑器窗口中，用下列代码替换现有代码：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h"
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

   此代码会将测试函数 `PlayGames` 添加到源代码，并在 `main` 中调用。

## <a name="build-and-run-your-app-project"></a>生成并运行应用项目

接下来，生成项目并运行应用。

### <a name="to-build-and-run-the-project"></a>生成并运行此项目

1. 在菜单栏上，依次选择“生成” > “生成解决方案”。

   来自生成的输出显示在“输出”窗口中。 如果生成成功，输出应类似于：

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   “输出”窗口可以根据不同的生成配置显示不同步骤，但是如果项目生成成功，最后一行应类似于上面显示的输出。

   如果生成未成功，请将你的代码与前面步骤中显示的代码进行比较。

1. 要运行项目，请在菜单栏上选择“调试” > “开始执行(不调试)”。 应显示控制台窗口，并且其输出应类似于：

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   按任意键关闭控制台窗口。

恭喜，你已成功生成应用项目和解决方案。 继续完成本演练，详细了解如何在 Visual Studio 中生成 C++ 代码项目。

## <a name="next-steps"></a>后续步骤

上一步：[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**下一篇：**[演练：生成项目 (C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[项目和生成系统](../build/projects-and-build-systems-cpp.md)<br/>
