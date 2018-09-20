---
title: 演练： 创建和使用静态库 （c + +） |Microsoft Docs
ms.custom: get-started-article
ms.date: 07/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9b71435b4fd2952746b2b097d08008624f8942b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412530"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>演练：创建和使用静态库 (C++)

此分步演练演示如何创建用于 C++ 应用的静态库（.lib 文件）。 使用静态库是重用代码的一种绝佳方式。 你不必在要求功能的每个应用中重新实现同一例程，而只需将其写入静态数据库一次，然后从应用引用它们即可。 从静态库链接的代码成为了应用的一部分，这样你就不必安装另一个文件来使用代码。

本演练涵盖以下任务：

- [创建静态库项目](#CreateLibProject)

- [向静态库添加类](#AddClassToLib)

- [创建一个 c + + 控制台应用程序引用静态库](#CreateAppToRefTheLib)

- [在应用中的静态库中使用的功能](#UseLibInApp)

- [运行该应用程序](#RunApp)

## <a name="prerequisites"></a>系统必备

你需要了解 C++ 语言的基础知识。

##  <a name="CreateLibProject"></a> 创建静态库项目

### <a name="to-create-a-static-library-project"></a>创建静态库项目

1. 在菜单栏上，依次选择“文件” > “新建” > “项目”。

2. 在左窗格中**新的项目**对话框框中，展开**已安装，Visual c + +**，然后选择**Windows 桌面**。

3. 在中心窗格中，选择**Windows 桌面向导**。

4. 指定项目的名称 — 例如， *MathFuncsLib*— 在**名称**框。 指定解决方案的名称 — 例如， *StaticLibrary*— 在**解决方案名称**框。 选择“确定”  按钮。

5. 下**应用程序类型**，选择静态库 (.lib)。

6. 下**其他选项**，取消选中**预编译标头**复选框。

7. 选择**确定**创建项目。

##  <a name="AddClassToLib"></a> 向静态库添加类

### <a name="to-add-a-class-to-the-static-library"></a>向静态库添加类

1. 若要为新类创建头文件，请在 **“解决方案资源管理器”** 中打开 **MathFuncsLib**项目的快捷菜单，然后依次选择 **“添加”**、 **“新建项”**。 在 **“添加新项”** 对话框的左窗格中，在 **“Visual C++”** 下选择 **“代码”**。 在中间窗格中，选择 **“头文件(.h)”**。 指定的标头文件的名称 — 例如， *MathFuncsLib.h*，然后选择**添加**按钮。 将显示一个空白头文件。

2. 添加一个名为类`MyMathFuncs`以执行常见的算术运算，例如加法、 减法、 乘法和除法。 代码应类似如下:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

3. 若要为新类创建源文件，请在 **“解决方案资源管理器”** 中打开 **MathFuncsLib**项目的快捷菜单，然后依次选择 **“添加”**、 **“新建项”**。 在 **“添加新项”** 对话框的左窗格中，在 **“Visual C++”** 下选择 **“代码”**。 在中间窗格中，选择 **“C++ 文件(.cpp)”**。 指定的源文件的名称 — 例如， *MathFuncsLib.cpp*，然后选择**添加**按钮。 将显示一个空白源文件。

4. 请使用此源文件实现 **MyMathFuncs**的功能。 代码应类似如下:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

5. 编译静态库，通过选择**构建** > **生成解决方案**菜单栏上。 这将创建一个可供其他程序使用的静态库。

   > [!NOTE]
   > 如果使用 Visual Studio 命令行生成，必须分两个步骤来生成程序。 首先，运行`cl /c /EHsc MathFuncsLib.cpp`以编译代码并创建名为的对象文件`MathFuncsLib.obj`。 （`cl` 命令可调用编译器 Cl.exe，并且 `/c` 选项可指定编译而无需链接。 有关详细信息，请参阅[/c （编译而无需链接）](../build/reference/c-compile-without-linking.md)。)其次，运行`lib MathFuncsLib.obj`以链接代码并创建静态库`MathFuncsLib.lib`。 （`lib` 命令可调用库管理器 Lib.exe。 有关详细信息，请参阅 [LIB Reference](../build/reference/lib-reference.md)。）

##  <a name="CreateAppToRefTheLib"></a> 创建一个 c + + 控制台应用程序引用静态库

### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>创建引用静态库的 C++ 控制台应用

1. 在菜单栏上，依次选择“文件” > “新建” > “项目”。

2. 在左窗格中**新的项目**对话框框中，展开**已安装，Visual c + +**，然后选择**Windows 桌面**。

3. 在中心窗格中，选择**Windows 桌面向导**。

4. 指定项目的名称 — 例如， *MyExecRefsLib*— 在**名称**框。 在 **“解决方案”** 旁的下拉列表中选择 **“添加到解决方案”**。 这会将新项目添加到包含此静态库的解决方案。 选择“确定”  按钮。
5. 下**应用程序类型**，选择**控制台应用程序 (.exe)**。

6. 下**Additioal 选项**，取消选中**预编译标头**复选框。

7. 选择**确定**创建项目。

##  <a name="UseLibInApp"></a> 在应用中的静态库中使用的功能

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在应用中使用静态库的功能

1. 创建控制台应用后，将为你创建一个空程序。 源文件的名称与你之前选择的名称相同。 在此示例中，名为`MyExecRefsLib.cpp`。

2. 必须引用静态库才能使用其中的算术例程。 若要执行此操作，打开快捷菜单**MyExecRefsLib**项目中**解决方案资源管理器**，然后选择**添加** > **引用**.

3. **“添加引用”** 对话框列出了可以引用的库。 **“项目”** 选项卡列出了当前解决方案中的所有项目以及它们包含的所有库。 在 **“项目”** 选项卡上，选中 **“MathFuncsLib”** 复选框，然后选择 **“确定”** 按钮。

4. 为引用`MathFuncsLib.h`标头文件中，您必须修改包含的目录路径。 在中**属性页**对话框**MyExecRefsLib**，展开**配置属性**节点，展开**C/c + +** 节点，并然后选择**常规**。 在 **“附加包含目录”** 旁，指定 **MathFuncsLib** 目录的路径或浏览至该目录。

   若要浏览至目录路径，请打开属性值下拉列表框，然后选择 **“编辑”**。 在中**附加包含目录**对话框中，在文本框中，选择一个空行，然后选择省略号按钮 (**...**) 在行尾。 在 **“选择目录”** 对话框中，选择 **MathFuncsLib** 目录，然后选择 **“选择文件夹”** 按钮以保存所做选择并关闭对话框。 在 **“附加包含目录”** 对话框中，选择 **“确定”** 按钮，然后在 **“属性页”** 对话框中，选择 **“确定”** 按钮以保存对该项目进行的更改。

5. 现在，您可以使用`MyMathFuncs`此应用程序中的类。 若要执行此操作，内容替换为`MyExecRefsLib.cpp`使用以下代码：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

6. 通过选择来生成可执行文件**构建** > **生成解决方案**菜单栏上。

##  <a name="RunApp"></a> 运行该应用程序

### <a name="to-run-the-app"></a>运行应用

1. 在 **“解决方案资源管理器”** 中打开 **MyExecRefsLib** 的快捷菜单，然后选择 **“设为启动项目”**，确保选择 **MyExecRefsLib**作为默认项目。

2. 若要运行该项目，在菜单栏上，选择**调试** > **启动但不调试**。 输出应该与下面的内容类似：

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>请参阅

[演练：创建和使用动态链接库 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[桌面应用程序 (Visual C++)](../windows/desktop-applications-visual-cpp.md)