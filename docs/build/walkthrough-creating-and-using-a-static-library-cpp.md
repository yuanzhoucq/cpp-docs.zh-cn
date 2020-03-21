---
title: 演练：创建和使用静态库 (C++)
description: 使用C++在 Visual Studio 中创建静态库（.lib）。
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: c81ccd970383c8571a7d0d1e77d4b8fe44900bcf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078184"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>演练：创建和使用静态库 (C++)

此分步演练演示如何创建用于 C++ 应用的静态库（.lib 文件）。 使用静态库是重用代码的一种绝佳方式。 不需要在每个需要功能的应用程序中重新实现相同的例程，只需在静态库中写入一次，然后从应用程序中引用它即可。 从静态库链接的代码成为了应用的一部分，这样你就不必安装另一个文件来使用代码。

本演练涵盖以下任务：

- [创建静态库项目](#CreateLibProject)

- [向静态库添加类](#AddClassToLib)

- [创建引用静态库的 C++ 控制台应用](#CreateAppToRefTheLib)

- [在应用中使用静态库的功能](#UseLibInApp)

- [运行应用程序](#RunApp)

## <a name="prerequisites"></a>必备条件

你需要了解 C++ 语言的基础知识。

##  <a name="creating-a-static-library-project"></a><a name="CreateLibProject"></a> 创建静态库项目

根据你使用的是 Visual Studio 2019 还是早期版本，如何创建项目的说明有所不同。 请确保在此页的左上角设置正确的版本。

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建静态库项目

1. 在菜单栏上，选择 "**文件**" ">**新建**>**项目**" 打开 "新建**项目**" 对话框。

1. 在对话框顶部，将“语言”设置为“C++”，将“平台”设置为“Windows”，并将“项目类型”设置为“库”。

1. 从筛选的项目类型列表中，选择 "**静态库**"，然后选择 "**下一步**"。 在下一页中，在 "**名称**" 框中输入*MathFuncsLib*以指定项目的名称，并指定项目位置（如果需要）。

1. 选择“创建”按钮创建客户端项目。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中创建静态库项目

1. 在菜单栏上，依次选择“文件”>“新建”>“项目”。

1. 在 "**新建项目**" 对话框的左窗格中，展开 "**已安装** >  **C++视觉对象**，然后选择" **Windows 桌面**"。 在中心窗格中，选择“Windows 桌面向导”。

1. 在 *“名称”* 框中为项目指定名称，例如 **MathFuncsLib** 。 在 *“解决方案名称”* 框中为解决方案指定名称，例如 **StaticLibrary** 。 选择“确定”按钮。

1. 在 "**应用程序类型**" 下，选择 "**静态库（.lib）** "。

1. 在 "**其他选项**" 下，取消选中 "**预编译标头**" 复选框。

1. 选择 **"确定"** 以创建项目。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>在 Visual Studio 2015 中创建静态库项目

1. 在菜单栏上，依次选择“文件”>“新建”>“项目”。

1. 在 "**新建项目**" 对话框中，展开 "**已安装** > **模板** > "**视觉C++对象**，然后选择 " **Win32**"。 在中间窗格中，选择 **“Win32 控制台应用程序”** 。

1. 在 *“名称”* 框中为项目指定名称，例如 **MathFuncsLib** 。 在 *“解决方案名称”* 框中为解决方案指定名称，例如 **StaticLibrary** 。 选择“确定”按钮。

1. 单击“下一步”。

1. 在 "**应用程序类型**" 下，选择 "**静态库**"。 然后取消选中 "**预编译标头**" 框，然后选择 "**完成**"。

::: moniker-end

##  <a name="adding-a-class-to-the-static-library"></a><a name="AddClassToLib"></a> 向静态库添加类

### <a name="to-add-a-class-to-the-static-library"></a>向静态库添加类

1. 若要为新类创建头文件，请在**解决方案资源管理器**中打开**MathFuncsLib**项目的快捷菜单，然后选择 "**添加** > **新项**"。 在 **“添加新项”** 对话框的左窗格中，在 **“Visual C++”** 下选择 **“代码”** 。 在中间窗格中，选择 **“头文件(.h)”** 。 为头文件指定名称（例如 *MathFuncsLib.h*），然后选择 **“添加”** 按钮。 将显示一个空白头文件。

1. 添加一个名为 `MyMathFuncs` 的类以执行常见的算术运算，如加法、减法、乘法和除法。 代码应类似于：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. 若要为新类创建源文件，请在**解决方案资源管理器**中打开**MathFuncsLib**项目的快捷菜单，然后选择 "**添加** > **新项**"。 在 **“添加新项”** 对话框的左窗格中，在 **“Visual C++”** 下选择 **“代码”** 。 在中间窗格中，选择 **“C++ 文件(.cpp)”** 。 为源文件指定名称（例如 *MathFuncsLib.cpp*），然后选择 **“添加”** 按钮。 将显示一个空白源文件。

1. 请使用此源文件实现 **MyMathFuncs**的功能。 代码应类似于：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. 通过在菜单栏上选择 "**生成** > **生成解决方案**" 来编译静态库。 编译会创建一个可供其他程序使用的静态库。

   > [!NOTE]
   > 如果使用 Visual Studio 命令行生成，必须分两个步骤来生成程序。 首先，运行 `cl /c /EHsc MathFuncsLib.cpp` 来编译代码并创建一个名为 `MathFuncsLib.obj`的对象文件。 （`cl` 命令可调用编译器 Cl.exe，并且 `/c` 选项可指定编译而无需链接。 有关详细信息，请参阅[/c （在不链接的情况下编译）](../build/reference/c-compile-without-linking.md)。）其次，运行 `lib MathFuncsLib.obj` 以链接代码并创建静态库 `MathFuncsLib.lib`。 （`lib` 命令可调用库管理器 Lib.exe。 有关详细信息，请参阅 [LIB Reference](../build/reference/lib-reference.md)。）

##  <a name="creating-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a> 创建引用静态库的 C++ 控制台应用

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>在 Visual Studio C++ 2019 中创建引用静态库的控制台应用

1. 在**解决方案资源管理器**中，右键单击解决方案的顶层节点，然后选择 "**添加**>"**新建项目**"以打开"**添加新项目**"对话框。

1. 在对话框顶部，将“语言”设置为“C++”，将“平台”设置为“Windows”，并将“项目类型”设置为“控制台”。

1. 从筛选的项目类型列表中，选择“控制台应用”，然后选择“下一步”。 在下一页中，在 "**名称**" 框中输入*MyExecRefsLib*以指定项目的名称，并指定项目位置（如果需要）。

1. 选择“创建”按钮创建客户端项目。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>在 Visual Studio C++ 2017 中创建引用静态库的控制台应用

1. 在菜单栏上，依次选择“文件”>“新建”>“项目”。

1. 在 "**新建项目**" 对话框的左窗格中，展开 "**已安装** >  **C++视觉对象**，然后选择" **Windows 桌面**"。 在中心窗格中，选择“Windows 桌面向导”。

1. 在 *“名称”* 框中为项目指定名称，例如 **MyExecRefsLib** 。 在 **“解决方案”** 旁的下拉列表中选择 **“添加到解决方案”** 。 此命令会将新项目添加到包含静态库的解决方案。 选择“确定”按钮。

1. 在 "**应用程序类型**" 下，选择 "**控制台应用程序（.exe）** "。

1. 在 "**其他选项**" 下，取消选中 "**预编译标头**" 复选框。

1. 选择 **"确定"** 以创建项目。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>在 Visual Studio C++ 2015 中创建引用静态库的控制台应用

1. 在菜单栏上，依次选择“文件”>“新建”>“项目”。

1. 在 "**新建项目**" 对话框中，展开 "**已安装** > **模板** > "**视觉C++对象**，然后选择 " **Win32**"。 在中间窗格中，选择 **“Win32 控制台应用程序”** 。

1. 在 *“名称”* 框中为项目指定名称，例如 **MyExecRefsLib** 。 在 **“解决方案”** 旁的下拉列表中选择 **“添加到解决方案”** 。 此命令会将新项目添加到包含静态库的解决方案。 选择“确定”按钮。

1. 单击“下一步”。

1. 请确保已选择 "**控制台应用程序**"。 然后选中 "**空项目**" 框，然后选择 "**完成**"。

::: moniker-end

##  <a name="using-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a> 在应用中使用静态库的功能

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在应用中使用静态库的功能

1. 创建控制台应用后，将为你创建一个空程序。 源文件的名称与你之前选择的名称相同。 在此示例中，它的名称为 `MyExecRefsLib.cpp`。

1. 必须引用静态库才能使用其中的算术例程。 在**解决方案资源管理器**中打开**MyExecRefsLib**项目的快捷菜单，然后选择 "**添加** > **引用**"。

1. **“添加引用”** 对话框列出了可以引用的库。 "**项目**" 选项卡列出了当前解决方案中的项目及其引用的任何库。 在 **“项目”** 选项卡上，选中 **“MathFuncsLib”** 复选框，然后选择 **“确定”** 按钮。

1. 若要引用 `MathFuncsLib.h` 头文件，必须修改包含的目录路径。 在**MyExecRefsLib**的 "**属性页**" 对话框中，展开 "**配置属性**" 节点，展开 " **C++ C/** " 节点，然后选择 "**常规**"。 在 "**附加包含目录**" 旁边，指定**MathFuncsLib**目录的路径或浏览到该目录。

   若要浏览至目录路径，请打开属性值下拉列表框，然后选择 **“编辑”** 。 在 "**附加包含目录**" 对话框的 "文本" 框中，选择一个空行，然后选择行尾的省略号按钮（ **...** ）。 在 **“选择目录”** 对话框中，选择 **MathFuncsLib** 目录，然后选择 **“选择文件夹”** 按钮以保存所做选择并关闭对话框。 在 **“附加包含目录”** 对话框中，选择 **“确定”** 按钮，然后在 **“属性页”** 对话框中，选择 **“确定”** 按钮以保存对该项目进行的更改。

1. 你现在可以通过在代码中包含 `#include "MathFuncsLib.h"` 标头，在此应用程序中使用 `MyMathFuncs` 类。 将 `MyExecRefsLib.cpp` 的内容替换为以下代码：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. 通过在菜单栏上选择 "**生成** > **生成解决方案**" 来生成可执行文件。

##  <a name="running-the-app"></a><a name="RunApp"></a> 运行应用程序

### <a name="to-run-the-app"></a>运行应用

1. 在 **“解决方案资源管理器”** 中打开 **MyExecRefsLib** 的快捷菜单，然后选择 **“设为启动项目”** ，确保选择 **MyExecRefsLib**作为默认项目。

1. 要运行项目，请在菜单栏上选择“调试” > “开始执行(不调试)”。 输出应类似于：

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>另请参阅

[演练：创建和使用动态链接库 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[桌面应用程序 (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
