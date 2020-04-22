---
title: 创建 C++ 控制台应用项目
description: 在可视化工作室中使用 Microsoft C++创建 Hello World 控制台应用程序。
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749308"
---
# <a name="create-a-c-console-app-project"></a>创建 C++ 控制台应用项目

C++ 程序员通常从在命令行上运行的“Hello, world!” 应用程序开始。 这是您将在 Visual Studio 中创建的步骤。

## <a name="prerequisites"></a>先决条件

- 在 Visual Studio 中安装“使用 C++ 的桌面开发”工作负载并在计算机上运行。 如果尚未安装，请参阅[在 Visual Studio 中安装 C++ 支持](vscpp-step-0-installation.md)。

## <a name="create-your-app-project"></a>创建应用项目

Visual Studio 使用项目来组织应用的代码，使用解决方案来组织项目****。 项目包含用于生成应用的所有选项、配置和规则。 它管理项目的所有文件和任何外部文件之间的关系。 要创建应用，需首先创建一个新项目和解决方案。

::: moniker range=">=vs-2019"

1. 在可视化工作室中，打开 **"文件**"菜单并选择 **"新建>项目**"以打开"**创建新项目"** 对话框。 选择具有**C++、Windows**和**控制台**标记**Windows****的控制台应用**模板，然后选择 **"下一步**"。

   ![创建新项目](media/vs2019-choose-console-app.png "打开"创建新项目"对话框")

1. 在"**配置新项目**"对话框中，在 **"项目名称**编辑"框中输入*HelloWorld。* 选择 **"创建**"以创建项目。

   ![命名并创建新项目](media/vs2019-configure-new-project-hello-world.png "命名并创建新项目")

   可视化工作室创建一个新项目。 它可供您添加和编辑源代码。 默认情况下，控制台应用模板使用"Hello World"应用填充源代码：

   ![你好世界项目在IDE](media/vs2019-hello-world-code.png "你好世界项目在IDE")

   当编辑器中的代码如下所示时，您可以继续下一步并构建应用。

[我遇到了问题。](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. 在可视化工作室中，打开 **"文件**"菜单并选择 **"新项目>项目**以打开 **"新项目**"对话框。

   ![打开“新建项目”对话框](media/vscpp-file-new-project.gif "打开“新建项目”对话框")

1. 在"**新项目"** 对话框中，选择"**已安装>可视化C++（** 如果尚未选中），然后选择 **"空项目**"模板。 在 **"名称"** 字段中，输入*HelloWorld*。 选择 **"确定"** 以创建项目。

   ![命名并创建新项目](media/vscpp-concierge-project-name-callouts.png "命名并创建新项目")

可视化工作室创建一个新的空项目。 它可供您专门用于要创建的应用类型并添加源代码文件。 我们会在下一步完成该操作。

[我遇到了问题。](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>使项目成为控制台应用

Visual Studio 可以为 Windows 和其他平台创建各种应用和组件。 **空项目**模板不特定于它创建的应用类型。 *控制台应用*是在控制台或命令提示窗口中运行的应用。 要创建一个，您必须告诉 Visual Studio 构建应用以使用控制台子系统。

1. 在可视化工作室中，打开 **"项目"** 菜单并选择 **"属性**"以打开**HelloWorld 属性页**对话框。

1. 在 **"属性页"** 对话框中，选择 **"配置属性>链接器>系统**，然后选择**子系统**属性旁边的编辑框。 在显示的下拉菜单中，选择**控制台（/SUBSYSTEM：CONSOLE）。** 选择“确定”以保存更改****。

   ![打开属性页对话框](media/vscpp-properties-linker-subsystem.gif "打开属性页对话框")

Visual Studio 现在知道要构建要在控制台窗口中运行的项目。 接下来，您将添加一个源代码文件，并输入应用的代码。

[我遇到了问题。](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>添加源代码文件

1. 在**解决方案资源管理器中**，选择 HelloWorld 项目。 在菜单栏上，选择 **"项目**"，**添加新项目**以打开"**添加新项目"** 对话框。

1. 在"**添加新项目"** 对话框中，如果尚未选中"已安装"，则在"**已安装**"下选择 **"可视C++"。** 在中心窗格中，选择**C++文件 （.cpp）**。 将**名称**更改为*HelloWorld.cpp*。 选择 **"添加"** 以关闭对话框并创建文件。

   ![为 HelloWorld.cpp 添加源文件](media/vscpp-add-new-item.gif "为 HelloWorld.cpp 添加源文件")

Visual Studio 会创建一个新的空源代码文件，并在编辑器窗口中打开该文件，以便输入源代码。

[我遇到了问题。](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>将代码添加到源文件

1. 将此代码复制到 HelloWorld.cpp 编辑器窗口中。

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   代码应在编辑器窗口中如下所示：

   ![你好世界代码在编辑器](media/vscpp-hello-world-editor.png "你好世界代码在编辑器")

当编辑器中的代码如下所示时，您可以继续下一步并构建应用。

[我遇到了问题。](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [生成并运行C++项目](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>故障排除指南

创建第一个C++项目时，请在此处寻求常见问题的解决方案。

### <a name="create-your-app-project-issues"></a>创建应用项目：问题

::: moniker range="vs-2019"

"**新项目**"对话框应显示具有**C++、Windows**和**C++****控制台标记的****控制台应用**模板。 如果您看不到它，则有两个可能的原因。 它可能从列表中筛选出来，或者可能未安装。 首先，检查模板列表顶部的筛选器下拉列表。 将它们设置为**C++、Windows**和**控制台**。 **Windows** 应显示C++**控制台应用**模板;否则，未安装**具有C++工作负载的桌面开发**。

要使用 C++ 安装**桌面开发**，可以从 **"新项目"** 对话框中直接运行安装程序。 在模板列表底部选择 **"安装更多工具和功能**"链接以启动安装程序。 如果**用户帐户控制**对话框请求权限，请选择"**是**"。 在安装程序中，请确保选中**具有C++工作负载的桌面开发**。 然后选择 **"修改"** 以更新可视化工作室安装。

如果另一个具有相同名称的项目已存在，请为项目选择另一个名称。 或者，删除现有项目，然后重试。 要删除现有项目，请删除文件资源管理器中的解决方案文件夹（包含*helloworld.sln*文件的文件夹）。

[回去](#create-your-app-project)吧。

::: moniker-end

::: moniker range="vs-2017"

如果 **"新项目"** 对话框未在 **"已安装**"下显示 **"视觉C++"** 条目，则 Visual Studio 的副本可能没有安装C++工作负载的**桌面开发**。 您可以直接从 **"新项目"** 对话框运行安装程序。 选择 **"打开可视化工作室安装程序"** 链接以重新启动安装程序。 如果**用户帐户控制**对话框请求权限，请选择"**是**"。 如有必要，更新安装程序。 在安装程序中，请确保选中**具有C++工作负载的桌面开发**，然后选择 **"确定"** 以更新 Visual Studio 安装。

::: moniker-end

::: moniker range="<=vs-2017"

如果另一个具有相同名称的项目已存在，请为项目选择另一个名称。 或者，删除现有项目，然后重试。 要删除现有项目，请删除文件资源管理器中的解决方案文件夹（包含*helloworld.sln*文件的文件夹）。

[回去](#create-your-app-project)吧。

### <a name="make-your-project-a-console-app-issues"></a>使项目成为控制台应用：问题

如果未在**配置属性**下列出**链接器**，请选择 **"取消"** 以关闭**属性页**对话框。 在重试之前，请确保**HelloWorld**项目在**解决方案资源管理器**中被选中。 不要在**解决方案资源管理器**中选择**HelloWorld**解决方案或其他项目。

在选择该属性之前，下拉控件不会显示在**SubSystem**属性编辑框中。 单击编辑框以选择它。 或者，您可以按**Tab**以循环浏览对话框控件，直到**突出显示子系统**。 选择下拉控件或按 **"向下"** 将其打开。

[回去](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>添加源代码文件：问题

如果给源代码文件指定不同的名称，则没关系。 但是，不要向项目添加多个包含相同代码的文件。

如果将错误的文件类型添加到项目（如头文件）中，请将其删除，然后重试。 要删除该文件，请在**解决方案资源管理器**中选择该文件。 然后按 **"删除**"键。

[回去](#add-a-source-code-file)吧。

### <a name="add-code-to-the-source-file-issues"></a>将代码添加到源文件：问题

如果意外关闭了源代码文件编辑器窗口，则可以轻松地再次打开它。 要打开它，请在**解决方案资源管理器**窗口中双击 HelloWorld.cpp。

如果源代码编辑器中的任何内容下出现红色波浪，请检查代码是否与拼写、标点符号和大小写中的示例匹配。 案例在C++代码中非常重要。

[回去](#add-code-to-the-source-file)吧。

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
