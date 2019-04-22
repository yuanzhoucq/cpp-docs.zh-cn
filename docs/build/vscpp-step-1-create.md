---
title: 创建 C++ 控制台应用项目
description: 在 Visual C++ 中创建 Hello World 控制台应用
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 739da0b6e5400117c0b09a3d4c3335bd44529a25
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58898773"
---
# <a name="create-a-c-console-app-project"></a>创建 C++ 控制台应用项目

C++ 程序员通常从在命令行上运行的“Hello, world!” 应用程序开始。 这是创建哪些内容将在 Visual Studio 中在此步骤。

## <a name="prerequisites"></a>系统必备

- 在 Visual Studio 中安装“使用 C++ 的桌面开发”工作负载并在计算机上运行。 如果尚未安装，请参阅[在 Visual Studio 中安装 C++ 支持](vscpp-step-0-installation.md)。

## <a name="create-your-app-project"></a>创建应用项目

Visual Studio 使用项目来组织应用的代码，使用解决方案来组织项目。 项目包含用于构建应用的所有选项、配置和规则，并管理所有项目文件与任何外部文件之间的关系。 要创建应用，需首先创建一个新项目和解决方案。

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中打开**文件**菜单，然后选择**新建** > **项目**以打开**创建一个新项目**对话框。 选择**控制台应用程序**模板，然后选择**下一步**。

   ![创建一个新项目](media/vs2019-choose-console-app.png "打开创建新项目对话框")

1. 在中**配置新项目**对话框中，输入*HelloWorld*中**项目名称**编辑框。 选择**创建**创建项目。

   ![命名并创建新项目](media/vs2019-configure-new-project-hello-world.png "名称并创建新项目")

   Visual Studio 创建一个新项目，就可以添加和编辑你的源代码。 默认情况下的控制台应用程序模板填充与"Hello World"应用程序在源代码中：

   ![在 IDE 中的 hello World 项目](media/vs2019-hello-world-code.png "在 IDE 中的 Hello World 项目")

   代码如下所示在编辑器中，当你准备好转到下一步并构建您的应用程序。

::: moniker-end

::: moniker range="<=vs-2017"

1. 在 Visual Studio 中打开**文件**菜单，然后选择**新建 > 项目**以打开**新项目**对话框。

   ![打开新建项目对话框](media/vscpp-file-new-project.gif "打开新建项目对话框")

1. 在中**新的项目**对话框中，选择**已安装**， **Visual C++** 如果未选中，然后选择**空项目**模板。 在中**名称**字段中，输入*HelloWorld*。 选择**确定**创建项目。

   ![命名并创建新项目](media/vscpp-concierge-project-name-callouts.png "名称并创建新项目")

Visual Studio 创建一个新的空项目可供您希望创建和添加你的源代码文件的应用的那类专用化。 您将执行的下一步。

[我遇到了问题。](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>将控制台应用程序的项目

Visual Studio 可以为 Windows 和其他平台创建各种各样的应用程序和组件。 **空项目**模板没有明确创建哪种应用程序。 若要创建*控制台应用*、 一个控制台或命令提示符窗口中运行，必须告知 Visual Studio 以生成应用以使用控制台子系统。

1. 在 Visual Studio 中打开**项目**菜单，然后选择**属性**以打开**HelloWorld 属性页**对话框。

1. 在中**属性页**对话框下**配置属性**，选择**链接器**，**系统**，然后选择编辑框旁边**子系统**属性。 在显示的下拉列表菜单，选择**控制台 (/ /SUBSYSTEM: CONSOLE)**。 选择“确定”以保存更改。

   ![打开属性页对话框](media/vscpp-properties-linker-subsystem.gif "打开属性页对话框")

Visual Studio 现在知道要生成项目以在控制台窗口中运行。 接下来，将添加一个源代码文件，并输入您的应用程序的代码。

[我遇到了问题。](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>添加一个源代码文件

1. 在中**解决方案资源管理器**，选择 HelloWorld 项目。 在菜单栏上依次选择**项目**，**添加新项**以打开**添加新项**对话框。

1. 在中**添加新项**对话框中，选择**Visual C++** 下**已安装**如果已选择。 在中心窗格中，选择**C++文件 (.cpp)**。 更改**名称**到*HelloWorld.cpp*。 选择**添加**以关闭对话框并创建该文件。

   ![将源代码文件添加为 HelloWorld.cpp](media/vscpp-add-new-item.gif "为 HelloWorld.cpp 添加源文件")

Visual studio 创建一个新的、 空的源代码文件，并在编辑器窗口，准备好输入你的源代码中打开它。

[我遇到了问题。](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>将代码添加到源代码文件

1. 将此代码复制到 HelloWorld.cpp 编辑器窗口。

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   代码应如下所示在编辑器窗口中：

   ![Hello World 代码编辑器中的](media/vscpp-hello-world-editor.png "编辑器中的 Hello World 代码")

代码如下所示在编辑器中，当你准备好转到下一步并构建您的应用程序。

[我遇到了问题。](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [生成并运行C++项目](vscpp-step-2-build.md)

::: moniker range="<=vs-2017"

## <a name="troubleshooting-guide"></a>故障排除指南

到这里的解决方案到常见的问题时创建你的第一个C++项目。

### <a name="create-your-app-project-issues"></a>创建您的应用程序项目问题

如果**新的项目**对话框不显示**Visual C++** 条目下的**已安装**，您的 Visual Studio 副本可能不具有**桌面使用开发C++** 已安装工作负载。 可以运行安装程序直接从**新的项目**对话框。 选择**打开 Visual Studio 安装程序**链接以再次启动安装程序。 如果**用户帐户控制**对话框请求权限时，选择**是**。 在安装程序中，请确保**使用的桌面开发C++** 工作负荷处于选中状态，然后选择**确定**来更新你的 Visual Studio 安装。

如果已存在具有相同名称的另一个项目，为你的项目，选择其他名称或删除现有项目，然后重试。 若要删除现有项目，请在文件资源管理器中删除解决方案文件夹 （包含 helloworld.sln 文件的文件夹）。

[返回](#create-your-app-project)。

### <a name="make-your-project-a-console-app-issues"></a>使控制台应用程序问题的项目

如果没有看到**链接器**下列出**配置属性**，选择**取消**以关闭**属性页**对话框，然后请确保**HelloWorld**中选择项目**解决方案资源管理器**，不的解决方案或另一个文件或文件夹，然后重试。

下拉列表控件中没有**子系统**属性编辑框中，直到您选择的属性。 可以通过使用指针，选择它，或者可以按选项卡的对话框控件直到循环**子系统**突出显示。 选择下拉列表控件，或按 Alt + Down 可打开它。

[回去](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>添加源代码文件问题

如果你为源的代码文件提供一个不同的名称，也没关系。 但是，不添加多个源代码文件包含到你的项目的相同代码。

如果将错误的文件类型添加到你的项目，例如，标头文件，将其删除，然后重试。 若要删除该文件，选择在其**解决方案资源管理器**然后按 Delete 键。

[返回](#add-a-source-code-file)。

### <a name="add-code-to-the-source-file-issues"></a>将代码添加到源代码文件问题

如果您意外地关闭源代码文件编辑器窗口中，若要重新打开，双击在 HelloWorld.cpp**解决方案资源管理器**窗口。

如果在源代码编辑器中的任何内容显示红色波浪线，请检查你的代码匹配拼写、 标点符号和用例中的示例。 用例非常重要C++代码。

[返回](#add-code-to-the-source-file)。

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
