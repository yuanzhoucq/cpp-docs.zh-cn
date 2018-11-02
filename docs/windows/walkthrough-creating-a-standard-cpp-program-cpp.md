---
title: 演练： 创建标准 c + + 程序 （c + +）
ms.custom: get-started-article
ms.date: 09/18/2018
f1_keywords:
- vcfirstapp
- vccreatefirst
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 78d19a277f8bedcdbd098a662c69d6fc622a7cff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647452"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>演练： 创建标准 c + + 程序 （c + +）

可以使用 Visual Studio 集成的开发环境 (IDE) 中的 Visual c + + 创建标准 c + + 程序。 按照此演练中的步骤操作，可以创建项目，向项目添加新文件，修改文件以添加 c + + 代码，然后编译并通过使用 Visual Studio 中运行程序。

可以键入自己的 c + + 程序，也可以使用示例程序之一。 在本演练中的示例程序是一个控制台应用程序。 此应用程序使用`set`c + + 标准库中的容器。

Visual c + + 遵循 2003 c + + 标准，与以下几点主要例外： 两阶段名称查找、 异常规范和导出。 此外，Visual c + + 支持若干 c++0x 功能，例如，lambda、 自动、 static_assert、 rvalue 引用和 extern 模板。

> [!NOTE]
> 如果所需的标准遵从性，请使用`/Za`编译器选项来禁用标准的 Microsoft 扩展。 有关详细信息，请参阅[/Za，/Ze （禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md)。

## <a name="prerequisites"></a>系统必备

若要完成本演练，你必须了解 C++ 语言的基础知识。

### <a name="to-create-a-project-and-add-a-source-file"></a>若要创建一个项目并添加源文件

1. 通过指向创建项目**新建**上**文件**菜单中，然后单击**项目**。

1. 在中**Visual c + +** 项目类型窗格中，单击**Windows Desktop**，然后单击**Windows 控制台应用程序**。

   > [!NOTE]
   > 对于版本的 Visual Studio 2017，在**新的项目**对话框框中，展开**已安装** > **模板** >  **Visual c + +**，然后选择**Win32**。 在中间窗格中，选择 **“Win32 控制台应用程序”**。

   键入项目的名称。

   默认情况下，包含项目的解决方案具有相同的名称为项目，但您可以键入不同名称。 此外可以键入项目的不同位置。

   单击“确定”，创建项目。

   > [!NOTE]
   > 对于版本的 Visual Studio 2017 中，填写**Win32 应用程序向导**。 单击**下一步**，然后确保**控制台应用程序**处于选中状态，并取消选中**预编译标头**框。 单击 **“完成”**。

1. 如果**解决方案资源管理器**不显示，请在**视图**菜单中，单击**解决方案资源管理器**。

1. 将新的源文件添加到项目中，按如下所示。

   1. 在中**解决方案资源管理器**，右键单击**源文件**文件夹，指向**添加**，然后单击**新项**。

   1. 在中**代码**节点中，单击**c + + 文件 (.cpp)**，键入该文件的名称，然后单击**添加**。

   .Cpp 文件将显示在**源文件**中的文件夹**解决方案资源管理器**，并在 Visual Studio 编辑器中打开该文件。

1. 中的文件在编辑器中，键入一个有效的 c + + 程序，使用 c + + 标准库，或复制其中一个示例程序并将其粘贴在文件中。

1. 保存该文件。

1. 在 **“生成”** 菜单上，单击 **“生成解决方案”**。

   **输出**窗口显示编译进度，例如，生成日志和一条指示生成状态消息的位置有关的信息。

1. 在“调试”菜单上，单击“开始执行(不调试)”。

   如果使用示例程序，命令窗口会显示，并显示是否在集中找到了特定的整数。

## <a name="next-steps"></a>后续步骤

**上一步：** [控制台在 Visual c + + 中的应用程序](../windows/console-applications-in-visual-cpp.md)<br/>
**下一步：** [演练： 编译本机 c + + 程序命令行上](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)<br/>
