---
title: 演练：创建和使用静态库 (C++)
description: 使用C++若要在 Visual Studio 中创建静态库 (.lib)。
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: afb12cc38dbaf0af88e93a9b329a59f3b54c8557
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217564"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>演练：创建和使用静态库 (C++)

此分步演练演示如何创建用于 C++ 应用的静态库（.lib 文件）。 使用静态库是重用代码的一种绝佳方式。 而不是重新实现同一例程需要一个编写这些功能，每个应用中的时间以静态库，然后从应用中引用它。 从静态库链接的代码成为了应用的一部分，这样你就不必安装另一个文件来使用代码。

本演练涵盖以下任务：

- [创建静态库项目](#CreateLibProject)

- [向静态库添加类](#AddClassToLib)

- [创建引用静态库的 C++ 控制台应用](#CreateAppToRefTheLib)

- [在应用中使用静态库的功能](#UseLibInApp)

- [运行应用程序](#RunApp)

## <a name="prerequisites"></a>系统必备

你需要了解 C++ 语言的基础知识。

##  <a name="CreateLibProject"></a> 创建静态库项目

有关如何创建项目的说明使用 Visual Studio 2019 或早期版本而异。 请确保已设置在此页的左上角的正确版本。

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中创建静态库项目

1. 在菜单栏上依次选择**文件** > **新建** > **项目**打开**创建一个新项目**对话框。

1. 在对话框顶部，设置**语言**到**C++**，将**平台**到**Windows**，并设置**项目类型**到**库**。 

1. 从已筛选的项目类型列表中，选择**静态库**然后选择**下一步**。 在下一页上，输入*MathFuncsLib*中**名称**框来指定项目的名称并根据需要指定项目位置。

1. 选择**创建**按钮以创建客户端项目。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>若要在 Visual Studio 2017 中创建静态库项目

1. 在菜单栏上选择“文件”>“新建”>“项目”。

1. 在左窗格中**新的项目**对话框框中，展开**已安装** > **Visual C++** ，然后选择**Windows 桌面**. 在中心窗格中，选择**Windows 桌面向导**。

1. 在 *“名称”* 框中为项目指定名称，例如 **MathFuncsLib** 。 在 *“解决方案名称”* 框中为解决方案指定名称，例如 **StaticLibrary** 。 选择“确定”  按钮。

1. 下**应用程序类型**，选择**静态库 (.lib)**。

1. 下**其他选项**，取消选中**预编译标头**复选框。

1. 选择**确定**创建项目。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>若要在 Visual Studio 2015 中创建静态库项目

1. 在菜单栏上选择“文件”>“新建”>“项目”。

1. 在中**新的项目**对话框框中，展开**已安装** > **模板** > **Visual C++** ，并然后选择**Win32**。 在中间窗格中，选择 **“Win32 控制台应用程序”**。

1. 在 *“名称”* 框中为项目指定名称，例如 **MathFuncsLib** 。 在 *“解决方案名称”* 框中为解决方案指定名称，例如 **StaticLibrary** 。 选择“确定”  按钮。

1. 单击 **“下一步”**。

1. 下**应用程序类型**，选择**静态库**。 然后取消选中**预编译标头**框，然后选择**完成**。

::: moniker-end

##  <a name="AddClassToLib"></a> 向静态库添加类

### <a name="to-add-a-class-to-the-static-library"></a>向静态库添加类

1. 若要创建新类的标头文件，打开快捷菜单**MathFuncsLib**项目中**解决方案资源管理器**，然后选择**添加** >  **新项**。 在 **“添加新项”** 对话框的左窗格中，在 **“Visual C++”** 下选择 **“代码”**。 在中间窗格中，选择 **“头文件(.h)”**。 为头文件指定名称（例如 *MathFuncsLib.h*），然后选择 **“添加”** 按钮。 将显示一个空白头文件。

1. 添加一个名为类`MyMathFuncs`以执行常见的算术运算，例如加法、 减法、 乘法和除法。 代码应类似于：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. 若要创建新的类的源代码文件，打开快捷菜单**MathFuncsLib**项目中**解决方案资源管理器**，然后选择**添加** >  **新项**。 在 **“添加新项”** 对话框的左窗格中，在 **“Visual C++”** 下选择 **“代码”**。 在中间窗格中，选择 **“C++ 文件(.cpp)”**。 为源文件指定名称（例如 *MathFuncsLib.cpp*），然后选择 **“添加”** 按钮。 将显示一个空白源文件。

1. 请使用此源文件实现 **MyMathFuncs**的功能。 代码应类似于：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. 编译静态库，通过选择**构建** > **生成解决方案**菜单栏上。 编译创建可由其他程序的静态库。

   > [!NOTE]
   > 如果使用 Visual Studio 命令行生成，必须分两个步骤来生成程序。 首先，运行`cl /c /EHsc MathFuncsLib.cpp`以编译代码并创建名为的对象文件`MathFuncsLib.obj`。 （`cl` 命令可调用编译器 Cl.exe，并且 `/c` 选项可指定编译而无需链接。 有关详细信息，请参阅[/c （编译而无需链接）](../build/reference/c-compile-without-linking.md)。)其次，运行`lib MathFuncsLib.obj`以链接代码并创建静态库`MathFuncsLib.lib`。 （`lib` 命令可调用库管理器 Lib.exe。 有关详细信息，请参阅 [LIB Reference](../build/reference/lib-reference.md)。）

##  <a name="CreateAppToRefTheLib"></a> 创建引用静态库的 C++ 控制台应用

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>若要创建C++控制台应用，它引用静态库中 Visual Studio 2019

1. 在**解决方案资源管理器**，右键单击该解决方案的顶级节点，然后选择**添加** > **新建项目**打开**添加新项目**对话框。

1. 在对话框顶部，设置**语言**到**C++**，将**平台**到**Windows**，并设置**项目类型**到**控制台**。 

1. 从已筛选的项目类型列表中，选择**控制台应用程序**然后选择**下一步**。 在下一页上，输入*MyExecRefsLib*中**名称**框来指定项目的名称并根据需要指定项目位置。

1. 选择**创建**按钮以创建客户端项目。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>若要创建C++控制台应用，它引用静态库在 Visual Studio 2017

1. 在菜单栏上选择“文件”>“新建”>“项目”。

1. 在左窗格中**新的项目**对话框框中，展开**已安装** > **Visual C++** ，然后选择**Windows 桌面**. 在中心窗格中，选择**Windows 桌面向导**。

1. 在 *“名称”* 框中为项目指定名称，例如 **MyExecRefsLib** 。 在 **“解决方案”** 旁的下拉列表中选择 **“添加到解决方案”**。 该命令将新项目添加到包含静态库的解决方案。 选择“确定”  按钮。

1. 下**应用程序类型**，选择**控制台应用程序 (.exe)**。

1. 下**其他选项**，取消选中**预编译标头**复选框。

1. 选择**确定**创建项目。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>若要创建C++控制台应用，它引用静态库在 Visual Studio 2015

1. 在菜单栏上选择“文件”>“新建”>“项目”。

1. 在中**新的项目**对话框框中，展开**已安装** > **模板** > **Visual C++** ，并然后选择**Win32**。 在中间窗格中，选择 **“Win32 控制台应用程序”**。

1. 在 *“名称”* 框中为项目指定名称，例如 **MyExecRefsLib** 。 在 **“解决方案”** 旁的下拉列表中选择 **“添加到解决方案”**。 该命令将新项目添加到包含静态库的解决方案。 选择“确定”  按钮。

1. 单击 **“下一步”**。

1. 请确保**控制台应用程序**处于选中状态。 然后，检查**空项目**框，然后选择**完成**。

::: moniker-end

##  <a name="UseLibInApp"></a> 在应用中使用静态库的功能

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在应用中使用静态库的功能

1. 创建控制台应用后，将为你创建一个空程序。 源文件的名称与你之前选择的名称相同。 在示例中，名为`MyExecRefsLib.cpp`。

1. 必须引用静态库才能使用其中的算术例程。 打开快捷菜单**MyExecRefsLib**项目中**解决方案资源管理器**，然后选择**添加** > **引用**.

1. **“添加引用”** 对话框列出了可以引用的库。 **项目**选项卡列出了当前解决方案以及它们引用的所有库中的项目。 在 **“项目”** 选项卡上，选中 **“MathFuncsLib”** 复选框，然后选择 **“确定”** 按钮。

1. 为引用`MathFuncsLib.h`标头文件中，您必须修改包含的目录路径。 在中**属性页**对话框**MyExecRefsLib**，展开**配置属性**节点，展开**C /C++** 节点，并选择**常规**。 下一步**附加包含目录**，指定的路径**MathFuncsLib**目录中或浏览。

   若要浏览至目录路径，请打开属性值下拉列表框，然后选择 **“编辑”**。 在中**附加包含目录**对话框中，在文本框中，选择一个空行，然后选择省略号按钮 (**...**) 在行尾。 在 **“选择目录”** 对话框中，选择 **MathFuncsLib** 目录，然后选择 **“选择文件夹”** 按钮以保存所做选择并关闭对话框。 在 **“附加包含目录”** 对话框中，选择 **“确定”** 按钮，然后在 **“属性页”** 对话框中，选择 **“确定”** 按钮以保存对该项目进行的更改。

1. 现在，您可以使用`MyMathFuncs`通过包含此应用程序中的类`#include "MathFuncsLib.h"`在代码中的标头。 内容替换为`MyExecRefsLib.cpp`使用以下代码：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. 通过选择来生成可执行文件**构建** > **生成解决方案**菜单栏上。

##  <a name="RunApp"></a> 运行应用程序

### <a name="to-run-the-app"></a>运行应用

1. 在 **“解决方案资源管理器”** 中打开 **MyExecRefsLib** 的快捷菜单，然后选择 **“设为启动项目”**，确保选择 **MyExecRefsLib**作为默认项目。

1. 要运行项目，请在菜单栏上选择“调试” > “开始执行(不调试)”。 输出应类似于：

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>请参阅

[演练：创建和使用动态链接库 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[桌面应用程序 (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
