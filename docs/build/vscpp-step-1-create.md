---
title: "创建 c + + 控制台应用程序项目 |Microsoft 文档"
description: "在 Visual c + + 中创建的 Hello World 控制台应用"
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: get-started-article
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76975054aad3173fef99a2e0f6c5ca1c642dea86
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2018
---
# <a name="create-a-c-console-app-project"></a>创建 c + + 控制台应用程序项目

C + + 程序员为常用的起始点"Hello，world ！" 在命令行运行的应用程序。 这是什么你将 Visual Studio 中创建在此步骤。

## <a name="prerequisites"></a>系统必备

- 具有 c + + 工作负荷安装并在计算机上运行与桌面开发的 Visual Studio。 如果未尚未安装，请参阅[Visual Studio 中的安装 c + + 支持](../build/vscpp-step-0-installation.md)。

## <a name="create-your-app-project"></a>创建应用程序项目

Visual Studio 使用项目来组织应用的代码，使用解决方案来组织项目。 项目包含所有选项、 配置和规则用于生成你的应用，并管理所有项目文件和任何外部文件之间的关系。 若要创建您的应用程序，首先，你将创建新项目和解决方案。

1. 在 Visual Studio 中，打开**文件**菜单，然后选择**新建 > 项目**以打开**新项目**对话框。

   ![打开新项目对话框](../build/media/vscpp-file-new-project.gif "打开新项目对话框")

1. 在**新项目**对话框中，选择**已安装**， **Visual c + +**如果它未连接，请选中，然后选择**空项目**模板。 在**名称**字段中，输入*HelloWorld*。 选择**确定**以创建该项目。

   ![命名并创建新项目](../build/media/vscpp-concierge-project-name-callouts.png "名称并创建新项目")

Visual Studio 创建新的空项目，并且可供您特别指明你想要创建并添加你的源代码文件的应用程序的类型。 你将执行该下一步。

[我遇到了问题。](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>使你的项目的控制台应用程序

Visual Studio 可以创建用于 Windows 和其他平台的所有类型的应用程序和组件。 **空项目**模板并不特定有关创建哪种类型的应用程序。 若要创建*控制台应用程序*、 一个运行在控制台或命令提示符窗口中，你必须告知 Visual Studio 生成应用程序为使用控制台子系统。

1. 在 Visual Studio 中，打开**项目**菜单，然后选择**属性**以打开**HelloWorld 属性页**对话框。

1. 在**属性页**对话框下**配置属性**，选择**链接器**，**系统**，然后选择编辑框旁边**子系统**属性。 在下拉列表中显示的菜单中，选择**控制台 (/ 子系统： 控制台)**。 选择**确定**以保存所做的更改。

   ![打开属性页对话框](../build/media/vscpp-properties-linker-subsystem.gif "打开属性页对话框")

Visual Studio 现在知道生成项目以在控制台窗口中运行。 接下来，将添加一个源代码文件，并为你的应用中输入的代码。

[我遇到了问题。](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>添加一个源代码文件

1. 在**解决方案资源管理器**，选择 HelloWorld 项目。 在菜单栏上，选择**项目**，**添加新项**以打开**添加新项**对话框。

1. 在**添加新项**对话框中，选择**Visual c + +**下**已安装**如果已选中。 在中心窗格中，选择**c + + 文件 (.cpp)**。 更改**名称**到*HelloWorld.cpp*。 选择**添加**以关闭对话框并创建该文件。

   ![添加一个源文件的 HelloWorld.cpp](../build/media/vscpp-add-new-item.gif "为 HelloWorld.cpp 添加源文件")

Visual studio 创建新的空代码文件，并将其打开在编辑器窗口中，可以输入你的源代码。

[我遇到了问题。](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>将代码添加到源文件

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

   ![Hello World 代码编辑器中的](../build/media/vscpp-hello-world-editor.png "在编辑器中的 Hello World 代码")

代码如下所示在编辑器中，当你准备好转到下一步并生成你的应用程序。

[我遇到了问题。](#add-a-source-code-file-issues)

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [生成并运行 c + + 项目](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>故障排除指南

出于此处解决方案的常见问题时创建第一个 c + + 项目。

### <a name="create-your-app-project-issues"></a>创建你的应用程序项目问题

如果**新项目**对话框不会显示**Visual c + +**下的项**已安装**，你的 Visual Studio 副本可能不具有**桌面使用 c + + 开发**安装的工作负荷。 你可以运行安装程序直接从**新项目**对话框。 选择**打开 Visual Studio 安装程序**再次启动安装程序的链接。 如果**用户帐户控制**对话框请求的权限，选择**是**。 在安装程序，请确保**使用 c + + 桌面开发**工作负荷已选中，然后选择**确定**更新你的 Visual Studio 安装。

如果已存在具有相同名称的另一个项目，为你的项目，选择其他名称或删除现有的项目，然后重试。 若要删除现有项目，请在文件资源管理器删除的解决方案文件夹 （包含 helloworld.sln 文件的文件夹）。

[返回](#create-your-app-project)。

### <a name="make-your-project-a-console-app-issues"></a>使该项目控制台应用程序问题

如果看不到**链接器**下列出**配置属性**，选择**取消**关闭**属性页**对话框，然后请确保**HelloWorld**中选择项目**解决方案资源管理器**，不解决方案或另一个文件或文件夹，然后重试。

下拉控件中未出现在**子系统**属性编辑框中，直到你选择的属性。 你可以选择它通过使用指针，或可以按 tab 键的对话框控件之前循环**子系统**突出显示。 选择的下拉列表控件，或按 Alt + 向下将其打开。

[回去](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>添加源代码文件问题

如果你为源代码文件提供一个不同的名称，也没关系。 但是，请勿添加多个源代码文件包含到你的项目相同的代码。

如果你添加到项目的文件的错误类型，例如，头文件中，将其删除，然后重试。 若要删除该文件，选择在**解决方案资源管理器**然后按 Delete 键。

[返回](#add-a-source-code-file)。

### <a name="add-code-to-the-source-file-issues"></a>将代码添加到源代码文件问题

如果你意外关闭源代码文件编辑器窗口中，若要重新打开，双击在 HelloWorld.cpp**解决方案资源管理器**窗口。

如果红色波浪线显示在源代码编辑器中的任何内容，请检查你的代码与匹配拼写、 标点符号和用例中的示例。 用例很重要 c + + 代码。

[返回](#add-code-to-the-source-file)。

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />