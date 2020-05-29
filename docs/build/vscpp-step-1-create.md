---
title: 创建 C++ 控制台应用项目
description: 在 Visual Studio 中使用 Microsoft C++ 创建 Hello World 控制台应用。
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749308"
---
# <a name="create-a-c-console-app-project"></a>创建 C++ 控制台应用项目

C++ 程序员通常从在命令行上运行的“Hello, world!” 应用程序开始。 这就是此步骤将在 Visual Studio 中创建的内容。

## <a name="prerequisites"></a>先决条件

- 在 Visual Studio 中安装“使用 C++ 的桌面开发”工作负载并在计算机上运行。 如果尚未安装，请参阅[在 Visual Studio 中安装 C++ 支持](vscpp-step-0-installation.md)。

## <a name="create-your-app-project"></a>创建应用项目

Visual Studio 使用项目来组织应用的代码，使用解决方案来组织项目   。 项目包含用于生成应用的所有选项、配置和规则。 它负责管理所有项目文件和任何外部文件间的关系。 要创建应用，需首先创建一个新项目和解决方案。

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中，打开“文件”  菜单，然后选择“新建”>“项目”  以打开“创建新项目”  对话框。 选择具有“C++”、“Windows”和“控制台”标记的“控制台应用”模板，然后选择“下一步”      。

   ![创建新项目](media/vs2019-choose-console-app.png "打开“创建新项目”对话框")

1. 在“配置新项目”  对话框中，在“项目名称”  编辑框中输入“HelloWorld”  。 选择“创建”  创建项目。

   ![命名并创建新项目](media/vs2019-configure-new-project-hello-world.png "命名并创建新项目")

   Visual Studio 随即创建新项目。 你已准备好添加和编辑源代码。 默认情况下，控制台应用模板会使用“Hello World”应用程序填充源代码：

   ![IDE 中的 Hello World 项目](media/vs2019-hello-world-code.png "IDE 中的 Hello World 项目")

   当代码在编辑器中类似于以下内容时，便可以继续执行下一步，并生成应用。

[我遇到了问题。](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. 在 Visual Studio 中，打开“文件”  菜单，然后选择“新建”>“项目”  以打开“新建项目”  对话框。

   ![打开“新建项目”对话框](media/vscpp-file-new-project.gif "打开“新建项目”对话框")

1. 如果尚未选中，则在“新建项目”对话框中，选择“已安装”>“Visual C++”   ，然后选择“空项目”  模板。 在“名称”  字段中，输入“HelloWorld”  。 选择“确定”，创建项目  。

   ![命名并创建新项目](media/vscpp-concierge-project-name-callouts.png "命名并创建新项目")

Visual Studio 随即创建新的空项目。 你已准备好专门处理要创建的应用类型，并添加源代码文件。 我们会在下一步完成该操作。

[我遇到了问题。](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>使项目成为控制台应用

Visual Studio 可以针对 Windows 和其他平台创建各种类型的应用和组件。 “空项目”  模板不特定于它所创建的应用类型。 控制台应用  是在控制台或命令提示窗口中运行的应用。 若要创建应用，必须告知 Visual Studio 生成应用以使用控制台子系统。

1. 在 Visual Studio 中，打开“项目”  菜单，然后选择“属性”  以打开“HelloWorld 属性页”  对话框。

1. 在“属性页”  对话框中，选择“配置属性”>“链接器”>“系统”  ，然后选择“子系统”  属性旁的编辑框。 在出现的下拉菜单中，选择“控制台(/SUBSYSTEM:CONSOLE)”  。 选择“确定”以保存更改  。

   ![打开“属性页”对话框](media/vscpp-properties-linker-subsystem.gif "打开“属性页”对话框")

Visual Studio 现在知道生成项目以在控制台窗口中运行。 接下来，将添加源代码文件，并为应用输入代码。

[我遇到了问题。](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>添加源代码文件

1. 在“解决方案资源管理器”中，选择 HelloWorld 项目  。 在菜单栏中，依次选择“项目”、“添加新项”以打开“添加新项”对话框    。

1. 在“添加新项”  对话框中，在“已安装”  下选择“Visual C++”  （如果尚未选择）。 在中间窗格中，选择“C++ 文件(.cpp)”  。 将“名称”  更改为 HelloWorld.cpp  。 选择“添加”  以关闭对话框并创建文件。

   ![为 HelloWorld.cpp 添加源文件](media/vscpp-add-new-item.gif "为 HelloWorld.cpp 添加源文件")

Visual studio 会创建新的空源代码文件，并在编辑器窗口中打开该文件，准备好输入源代码。

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

   代码在编辑器窗口中应如下所示：

   ![编辑器中的 Hello World 代码](media/vscpp-hello-world-editor.png "编辑器中的 Hello World 代码")

当代码在编辑器中类似于以下内容时，便可以继续执行下一步，并生成应用。

[我遇到了问题。](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [生成和运行 C++ 项目](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>故障排除指南

此指南提供创建第一个 C++ 项目时的常见问题的解决方案。

### <a name="create-your-app-project-issues"></a>创建应用项目：问题

::: moniker range="vs-2019"

“新建项目”  对话框应显示一个具有“C++”、“Windows”和“控制台”标记的“控制台应用”模板     。 如果未显示，则有两个可能的原因。 它可能已从列表中筛选掉，或可能未安装。 首先，检查模板列表顶部的筛选器下拉菜单。 将它们设置为“C++”  、“Windows”  和“控制台”  。 C++“控制台应用”  模板应出现；否则，不会安装“使用 C++ 的桌面开发”  工作负载。

若要安装“使用 C++ 的桌面开发”  ，可以直接从“新建项目”  对话框运行安装程序。 选择模板列表底部的“安装更多工具和功能”  链接，以启动安装程序。 如果“用户帐户控制”  对话框请求权限，则选择“是”  。 在安装程序中，请务必选中“使用 C++ 的桌面开发”  工作负载。 然后选择“修改”  以更新 Visual Studio 安装。

如果已存在具有相同名称的其他项目，请为你的项目选择其他名称。 或者，删除现有项目，然后重试。 若要删除现有项目，请在文件资源管理器中删除解决方案文件夹（包含 helloworld.sln  文件的文件夹）。

[返回](#create-your-app-project)。

::: moniker-end

::: moniker range="vs-2017"

如果“新建项目”  对话框中未在“已安装”  下显示“Visual C++”  条目，则 Visual Studio 的副本可能未安装“使用 C++ 的桌面开发”  工作负载。 可以直接从“新建项目”  对话框运行安装程序。 选择“打开 Visual Studio 安装程序”链接  以再次启动安装程序。 如果“用户帐户控制”  对话框请求权限，则选择“是”  。 必要时更新安装程序。 在安装程序中，请务必选中“使用 C++ 的桌面开发”  工作负载，然后选择“确定”  以更新 Visual Studio 安装。

::: moniker-end

::: moniker range="<=vs-2017"

如果已存在具有相同名称的其他项目，请为你的项目选择其他名称。 或者，删除现有项目，然后重试。 若要删除现有项目，请在文件资源管理器中删除解决方案文件夹（包含 helloworld.sln  文件的文件夹）。

[返回](#create-your-app-project)。

### <a name="make-your-project-a-console-app-issues"></a>使项目成为控制台应用：问题

如果看不到“配置属性”  下列出了“链接器”  ，请选择“取消”  以关闭“属性页”  对话框。 在重试之前，确保在“解决方案资源管理器”  中选择了“HelloWorld”  项目。 请勿在“解决方案资源管理器”  中选择“HelloWorld”  解决方案或其他项。

下拉控件不会出现在“子系统”  属性编辑框中，直到你选择属性。 在编辑框中单击以选择它。 或者，可以按 Tab  以遍历对话框控件，直到突出显示“子系统”  。 选择下拉控件或按 Alt+Down  以打开它。

[返回](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>添加源代码文件：问题

为源代码文件提供其他名称不会出现问题。 但是，不要将包含相同代码的多个文件添加到项目。

如果向项目中添加了错误的文件类型（如头文件），请删除它，然后重试。 若要删除文件，请在“解决方案资源管理器”  中选择它。 然后按 Delete  键。

[返回](#add-a-source-code-file)。

### <a name="add-code-to-the-source-file-issues"></a>将代码添加到源文件：问题

如果意外关闭了源代码文件编辑器窗口，则可以轻松地再次打开。 若要打开它，请在“解决方案资源管理器”  窗口中双击 HelloWorld.cpp。

如果在源代码编辑器中的任何内容下出现红色波形曲线，请检查代码是否在拼写、标点和大小写方面与示例相符。 大小写在 C++ 代码中十分重要。

[返回](#add-code-to-the-source-file)。

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
