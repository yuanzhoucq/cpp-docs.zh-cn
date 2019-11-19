---
title: 演练：创建标准C++程序（）C++
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 9b2d1f3bf1a229a0590553369e37bc07f35ada33
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627133"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>演练：创建标准C++程序（）C++

可以使用 Visual Studio 创建标准C++程序。 通过执行本演练中的步骤，您可以创建一个项目，将一个新文件添加到该项目，修改该文件以C++添加代码，然后使用 Visual Studio 编译和运行该程序。

您可以键入自己C++的程序，也可以使用其中一个示例程序。 本演练中的示例程序是一个控制台应用程序。 此应用程序使用C++标准库中的 `set` 容器。

> [!NOTE]
> 如果需要符合C++语言标准的特定版本（例如 c + + 14 或 c + + 17），请使用 `/std:c++14` 或 `/std:c++17` 编译器选项。 （Visual Studio 2017 及更高版本。）

## <a name="prerequisites"></a>Prerequisites

若要完成本演练，你必须了解 C++ 语言的基础知识。

### <a name="to-create-a-project-and-add-a-source-file"></a>创建项目并添加源文件

根据使用的 Visual Studio 版本，以下步骤会有所不同。 确保本页左上角的版本选择器已正确设置。

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>在 Visual Studio C++ 2019 中创建项目

1. 在主菜单中，选择“文件”>“新建”>“项目”，打开“创建新项目”对话框。

1. 在对话框顶部，将“语言”设置为“C++”，将“平台”设置为“Windows”，并将“项目类型”设置为“控制台”。 

1. 从筛选的项目类型列表中，选择“控制台应用”，然后选择“下一步”。 在下一页中，输入项目的名称，并指定项目位置（如果需要）。

1. 选择“创建”按钮创建项目。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>在 Visual Studio C++ 2017 中创建项目

1. 通过指向 "**文件**" 菜单上的 "**新建**"，然后单击 "**项目**" 来创建项目。

1. 在 "**可视C++** 项目类型" 窗格中，单击 " **windows 桌面**"，然后单击 " **windows 控制台应用程序**"。

1. 键入项目的名称。 默认情况下，包含项目的解决方案具有与项目相同的名称，但您可以键入不同的名称。 你还可以为项目键入不同的位置。

1. 单击“确定”，创建项目。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>在 Visual Studio C++ 2015 中创建项目

1. 通过指向 "**文件**" 菜单上的 "**新建**"，然后单击 "**项目**" 来创建项目。

1. 在 "**可视C++** 项目类型" 窗格中，单击 " **windows 桌面**"，然后单击 " **windows 控制台应用程序**"。

1. 在 "**新建项目**" 对话框中，展开 "**已安装** > **模板** > "**视觉C++对象**，然后选择 " **Win32**"。 在中间窗格中，选择 **“Win32 控制台应用程序”** 。

1. 键入项目的名称。 默认情况下，包含项目的解决方案具有与项目相同的名称，但您可以键入不同的名称。 你还可以为项目键入不同的位置。

1. 单击“确定”，创建项目。

1. 完成 " **Win32 应用程序向导**"。 

1. 单击 "**下一步**"，确保选中 "**控制台应用程序**"，并取消选中 "**预编译标头**" 框。 

1. 单击 **“完成”** 。

::: moniker-end

## <a name="add-a-new-source-file"></a>添加新源文件

1. 如果**解决方案资源管理器**未显示，请在 "**视图**" 菜单上单击 "**解决方案资源管理器**"。

1. 向项目中添加一个新的源文件，如下所示。

   1. 在**解决方案资源管理器**中，右键单击 "**源文件**" 文件夹，指向 "**添加**"，然后单击 "**新建项**"。

   1. 在 "**代码**" 节点中，单击 **C++ "文件（.cpp）** "，键入文件的名称，然后单击 "**添加**"。

   .Cpp 文件将显示在**解决方案资源管理器**的 "**源文件**" 文件夹中，并在 Visual Studio 编辑器中打开该文件。

1. 在编辑器中的文件中，键入使用C++ C++标准库的有效程序，或复制其中一个示例程序，然后将其粘贴到文件中。

1. 保存该文件。

1. 在 **“生成”** 菜单上，单击 **“生成解决方案”** 。

   "**输出**" 窗口显示有关编译进度的信息，例如，生成日志的位置和指示生成状态的消息。

1. 在“调试”菜单上，单击“开始执行(不调试)”。

   如果使用了示例程序，将显示一个命令窗口，并显示是否在集中找到了某些整数。

## <a name="next-steps"></a>后续步骤

**Previous：** [视觉对象C++中的控制台应用程序](../windows/console-applications-in-visual-cpp.md)<br/>
**下一步：** [演练：在C++命令行上编译本机程序](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
