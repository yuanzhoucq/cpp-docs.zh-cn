---
title: 演练：创建一个标准C++程序 (C++)
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: ed9c19dad029f8fc9495d38ab6e5c0ba8ad6d529
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877421"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>演练：创建一个标准C++程序 (C++)

您可以使用 Visual Studio 将创建标准C++程序。 按照此演练中的步骤操作，可以创建项目，向项目添加新文件，修改要添加的文件C++的代码，然后编译和使用 Visual Studio 中运行程序。

您可以键入自己C++程序或使用示例程序之一。 在本演练中的示例程序是一个控制台应用程序。 此应用程序使用`set`容器中的C++标准库。

> [!NOTE]
> 如果符合特定版本的C++语言标准 （即 C + + 14 或 C + + 17） 是必需的请使用`/std:C++14`或`/std:c++17`编译器选项。 (Visual Studio 2017 和更高版本。)

## <a name="prerequisites"></a>系统必备

若要完成本演练，你必须了解 C++ 语言的基础知识。

### <a name="to-create-a-project-and-add-a-source-file"></a>若要创建一个项目并添加源文件

以下步骤会有所不同，具体取决于所使用的 Visual Studio 版本。 确保左上版本选择器的此页设置正确。

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>若要创建C++Visual Studio 2019 中的项目

1. 从主菜单中，选择**文件** > **新建** > **项目**打开**创建一个新项目**对话框框。

1. 在对话框顶部，设置**语言**到**C++**，将**平台**到**Windows**，并设置**项目类型**到**控制台**。 

1. 从已筛选的项目类型列表中，选择**控制台应用程序**然后选择**下一步**。 在下一步的页中，输入项目的名称并根据需要指定项目位置。

1. 选择**创建**按钮创建项目。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>若要创建C++Visual Studio 2017 中的项目

1. 通过指向创建项目**新建**上**文件**菜单中，然后单击**项目**。

1. 在中**可视化C++** 项目类型窗格中，单击**Windows Desktop**，然后单击**Windows 控制台应用程序**。

1. 键入项目的名称。 默认情况下，包含项目的解决方案具有相同的名称为项目，但您可以键入不同名称。 此外可以键入项目的不同位置。

1. 单击“确定”，创建项目。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>若要创建C++Visual Studio 2015 中的项目

1. 通过指向创建项目**新建**上**文件**菜单中，然后单击**项目**。

1. 在中**可视化C++** 项目类型窗格中，单击**Windows Desktop**，然后单击**Windows 控制台应用程序**。

1. 在中**新的项目**对话框框中，展开**已安装** > **模板** > **Visual C++** ，并然后选择**Win32**。 在中间窗格中，选择 **“Win32 控制台应用程序”**。

1. 键入项目的名称。 默认情况下，包含项目的解决方案具有相同的名称为项目，但您可以键入不同名称。 此外可以键入项目的不同位置。

1. 单击“确定”，创建项目。

1. 完成**Win32 应用程序向导**。 

1. 单击**下一步**，然后确保**控制台应用程序**处于选中状态，并取消选中**预编译标头**框。 

1. 单击 **“完成”**。

::: moniker-end

## <a name="add-a-new-source-file"></a>添加新的源文件

1. 如果**解决方案资源管理器**不显示，请在**视图**菜单中，单击**解决方案资源管理器**。

1. 将新的源文件添加到项目中，按如下所示。

   1. 在中**解决方案资源管理器**，右键单击**源文件**文件夹，指向**添加**，然后单击**新项**。

   1. 在中**代码**节点中，单击**C++文件 (.cpp)**，键入该文件的名称，然后单击**添加**。

   .Cpp 文件将显示在**源文件**中的文件夹**解决方案资源管理器**，并在 Visual Studio 编辑器中打开该文件。

1. 在编辑器中文件中，键入一个有效C++程序，使用C++标准库或复制其中某个示例程序，并将其粘贴在文件中。

1. 保存该文件。

1. 在 **“生成”** 菜单上，单击 **“生成解决方案”**。

   **输出**窗口显示编译进度，例如，生成日志和一条指示生成状态消息的位置有关的信息。

1. 在“调试”菜单上，单击“开始执行(不调试)”。

   如果使用示例程序，命令窗口会显示，并显示是否在集中找到了特定的整数。

## <a name="next-steps"></a>后续步骤

上一步：[Visual C++ 中的控制台应用程序](../windows/console-applications-in-visual-cpp.md)<br/>
**下一篇：**[演练：在命令行上编译本机 C++ 程序](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)<br/>
