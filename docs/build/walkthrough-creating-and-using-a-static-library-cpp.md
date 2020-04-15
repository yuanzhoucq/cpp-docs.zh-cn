---
title: 演练：创建和使用静态库 （C++）
description: 使用C++在可视化工作室中创建静态库 （.lib）。
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 7148cc1de7c06ae57d61560311b342a1fc9dda1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335137"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>演练：创建和使用静态库

此分步演练演示如何创建用于 C++ 应用的静态库（.lib 文件）。 使用静态库是重用代码的一种绝佳方式。 而不是在每个应用中重新实现需要该功能的相同例程，而是在静态库中编写一次例程，然后从应用中引用它。 从静态库链接的代码将成为应用的一部分，您无需安装另一个文件来使用该代码。

本演练涵盖以下任务：

- [创建静态库项目](#CreateLibProject)

- [将类添加到静态库](#AddClassToLib)

- [创建引用静态库的C++控制台应用](#CreateAppToRefTheLib)

- [使用应用中静态库中的功能](#UseLibInApp)

- [运行应用](#RunApp)

## <a name="prerequisites"></a>先决条件

你需要了解 C++ 语言的基础知识。

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a>创建静态库项目

有关如何创建项目的说明因可视化工作室的版本而异。 要查看您首选版本的 Visual Studio 的文档，请使用**版本**选择器控件。 它位于此页面的目录顶部。

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建静态库项目

1. 在菜单栏上，选择“文件”“新建”“项目”，打开“创建新项目”对话框**** > **** > ********。

1. 在对话框顶部，将“语言”**** 设置为“C++”****，将“平台”**** 设置为“Windows”****，并将“项目类型”**** 设置为“库”****。

1. 从筛选的项目类型列表中，选择 Windows**桌面向导**，然后选择 **"下一步**"。

1. 在"**配置新项目**"页中，在 **"项目名称**"框中输入*MathLibrary*以指定项目的名称。 在 **"解决方案"名称**框中输入*静态数学*。 选择 **"创建**"按钮以打开**Windows 桌面项目**对话框。

1. 在 **"Windows 桌面项目"** 对话框中，在 **"应用程序类型**"下，选择**静态库 （.lib）。**

1. 在 **"其他选项**"下，如果选中 **"预编译标头**"复选框，则取消选中该复选框。 选中"**空项目**"框。

1. 选择 **"确定"** 以创建项目。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中创建静态库项目

1. 在菜单栏上选择“文件”**“新建”** > **“项目”** > ****。

1. 在 **"新项目**"对话框中，选择 **"安装** > **的可视C++** > **Windows 桌面**。 在中心窗格中，选择“Windows 桌面向导”****。

1. 在 **"名称"** 框中指定项目的名称（例如 *，MathLibrary）。* 在 **"解决方案名称**"框中指定解决方案的名称（例如*StaticMath）。* 选择“确定”按钮。****

1. 在 **"Windows 桌面项目"** 对话框中，在 **"应用程序类型**"下，选择**静态库 （.lib）。**

1. 在 **"其他选项**"下，如果选中 **"预编译标头**"复选框，则取消选中该复选框。 选中"**空项目**"框。

1. 选择 **"确定"** 以创建项目。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>在 Visual Studio 2015 中创建静态库项目

1. 在菜单栏上选择“文件”**“新建”** > **“项目”** > ****。

1. 在 **"新项目**"对话框中，选择 **"已安装** > **模板** > **"可视C++** > **Win32**。 在中间窗格中，选择 **“Win32 控制台应用程序”**。

1. 在 **"名称"** 框中指定项目的名称（例如 *，MathLibrary）。* 在 **"解决方案名称**"框中指定解决方案的名称（例如*StaticMath）。* 选择“确定”按钮。****

1. 在**Win32 应用程序向导**中，选择 **"下一步**"。

1. 在 **"应用程序设置"** 页中，在 **"应用程序类型**"下，选择 **"静态库**"。 在 **"其他选项**"下，取消选中**预编译标头**复选框。 选择 **"完成"** 以创建项目。

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>将类添加到静态库

### <a name="to-add-a-class-to-the-static-library"></a>向静态库添加类

1. 要为新类创建标题文件，请右键单击以打开**解决方案资源管理器**中的**MathLibrary**项目的快捷方式菜单，然后选择"**添加新** > **项目**"。

1. 在"**添加新项目"** 对话框中，选择 **"可视C++** > **代码**"。 在中间窗格中，选择 **“头文件(.h)”**。 指定头文件的名称，例如*MathLibrary.h*，然后选择 **"添加**"按钮。 将显示几乎空白的标头文件。

1. 添加名为的`Arithmetic`类的声明，以执行常见数学运算，如加法、减法、乘法和除法。 代码应类似于：

    ```cpp
    // MathLibrary.h
    #pragma once

    namespace MathLibrary
    {
        class Arithmetic
        {
        public:
            // Returns a + b
            static double Add(double a, double b);

            // Returns a - b
            static double Subtract(double a, double b);

            // Returns a * b
            static double Multiply(double a, double b);

            // Returns a / b
            static double Divide(double a, double b);
        };
    }
    ```

1. 要为新类创建源文件，请打开**解决方案资源管理器**中的**MathLibrary**项目的快捷菜单，然后选择"**Add** > **添加新项**"。

1. 在"**添加新项目"** 对话框中，在中心窗格中，选择**C++文件 （.cpp）**。 指定源文件的名称（例如 *，MathLibrary.cpp），* 然后选择 **"添加**"按钮。 将显示一个空白源文件。

1. 使用此源文件实现类`Arithmetic`的功能。 代码应类似于：

    ```cpp
    // MathLibrary.cpp
    // compile with: cl /c /EHsc MathLibrary.cpp
    // post-build command: lib MathLibrary.obj

    #include "MathLibrary.h"

    namespace MathLibrary
    {
        double Arithmetic::Add(double a, double b)
        {
            return a + b;
        }

        double Arithmetic::Subtract(double a, double b)
        {
            return a - b;
        }

        double Arithmetic::Multiply(double a, double b)
        {
            return a * b;
        }

        double Arithmetic::Divide(double a, double b)
        {
            return a / b;
        }
    }
    ```

1. 要生成静态库，请在菜单栏上选择 > **"生成生成解决方案**"。 **Build** 生成创建一个静态库 *，MathLibrary.lib*，可以由其他程序使用。

   > [!NOTE]
   > 如果使用 Visual Studio 命令行生成，必须分两个步骤来生成程序。 首先，运行`cl /c /EHsc MathLibrary.cpp`以编译代码并创建名为*MathLibrary.obj*的对象文件。（该`cl`命令调用编译器 Cl.exe，`/c`该选项指定编译而不链接。 有关详细信息，请参阅[/c（编译而不链接）](../build/reference/c-compile-without-linking.md).其次，运行`lib MathLibrary.obj`以链接代码并创建静态库*MathLibrary.lib*。 （`lib` 命令可调用库管理器 Lib.exe。 有关详细信息，请参阅 [LIB Reference](../build/reference/lib-reference.md)。）

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>创建引用静态库的C++控制台应用

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>创建引用 Visual Studio 2019 中的静态库的C++控制台应用

1. 在**解决方案资源管理器**中，右键单击顶部节点 **"静态数学"** 以打开快捷菜单。 选择 **"添加新** > **项目**"以打开"**添加新项目**"对话框。

1. 在对话框的顶部，将**项目类型**筛选器设置为**控制台**。

1. 从筛选的项目类型列表中，选择“控制台应用”，然后选择“下一步”********。 在下一页中，在 **"名称"** 框中输入*MathClient*以指定项目的名称。

1. 选择“创建”**** 按钮创建客户端项目。

1. 创建控制台应用后，将为你创建一个空程序。 源文件的名称与你之前选择的名称相同。 在此示例中，它名为`MathClient.cpp`。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>创建引用 Visual Studio 2017 中的静态库的C++控制台应用

1. 在**解决方案资源管理器**中，右键单击顶部节点 **"静态数学"** 以打开快捷菜单。 选择 **"添加新** > **项目**"以打开"**添加新项目**"对话框。

1. 在"**添加新项目**"对话框中，选择 **"安装** > **的可视C++** > **Windows 桌面**。 在中心窗格中，选择“Windows 桌面向导”****。

1. 在 **"名称"** 框中指定项目的名称（例如*MathClient）。* 选择“确定”按钮。****

1. 在**Windows 桌面项目**对话框中，在 **"应用程序类型"** 下，选择**控制台应用程序 （.exe）。**

1. 在 **"其他选项**"下，如果选中 **"预编译标头**"复选框，则取消选中该复选框。

1. 选择 **"确定"** 以创建项目。

1. 创建控制台应用后，将为你创建一个空程序。 源文件的名称与你之前选择的名称相同。 在此示例中，它名为`MathClient.cpp`。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>创建引用 Visual Studio 2015 中的静态库的C++控制台应用

1. 在**解决方案资源管理器**中，右键单击顶部节点 **"静态数学"** 以打开快捷菜单。 选择 **"添加新** > **项目**"以打开"**添加新项目**"对话框。

1. 在"**添加新项目**"对话框中，选择 **"已安装** > **视觉C++** > **Win32**。 在中间窗格中，选择 **“Win32 控制台应用程序”**。

1. 在 **"名称"** 框中指定项目的名称（例如*MathClient）。* 选择“确定”按钮。****

1. 在**Win32 应用程序向导**对话框中，选择 **"下一步**"。

1. 在 **"应用程序设置"** 页上，在 **"应用程序类型**"下，请确保选择了**控制台应用程序**。 在 **"其他选项**"下，取消选中**预编译标头**，然后选中 **"空项目**"复选框。 选择 **"完成"** 以创建项目。

1. 要将源文件添加到空项目中，请右键单击以打开**解决方案资源管理器**中的**MathClient**项目的快捷方式菜单，然后选择"**添加新**>**项**"。

1. 在"**添加新项目"** 对话框中，选择 **"可视C++** > **代码**"。 在中间窗格中，选择 **“C++ 文件(.cpp)”**。 指定源文件的名称（例如*MathClient.cpp），* 然后选择 **"添加**"按钮。 将显示一个空白源文件。

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>使用应用中静态库中的功能

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在应用中使用静态库的功能

1. 必须引用静态库才能使用其中的算术例程。 在**解决方案资源管理器**中打开**MathClient**项目的快捷菜单，然后选择 **"添加** > **参考**"。

1. **“添加引用”** 对话框列出了可以引用的库。 "**项目"** 选项卡列出当前解决方案中的项目及其引用的任何库。 打开"**项目**"选项卡，选择 **"数学库**"复选框，然后选择"**确定**"按钮。

1. 要引用`MathLibrary.h`标头文件，必须修改包含的目录路径。 在**解决方案资源管理器**中，右键单击**MathClient**以打开快捷菜单。 选择 **"属性**"以打开 **"数学客户端属性页"** 对话框。

1. 在 **"MathClient 属性页**"对话框中，将 **"配置**"下拉至 **"所有配置**"。 将**平台**下拉列表设置为 **"所有平台**"。

1. 选择**配置属性** > **C/C++** > **常规**属性页。 在 **"其他包含目录"** 属性中，指定**MathLibrary**目录的路径，或浏览该目录。

   要浏览目录路径：

   1. 打开 **"其他包含目录**"属性值下拉列表，然后选择 **"编辑**"。

   1. 在"**其他包含目录"** 对话框中，双击文本框顶部。 然后选择行尾的省略号按钮 （**...）。**

   1. 在 **"选择目录"** 对话框中，向上导航一个级别，然后选择**MathLibrary**目录。 然后选择 **"选择文件夹"** 按钮以保存您的选择。

   1. 在"**其他包含目录"对话框中**，选择"**确定"** 按钮。

   1. 在"**属性页"** 对话框中，选择"**确定**"按钮以保存对项目的更改。

1. 现在，`Arithmetic`您可以通过在代码中包含标头来使用此应用中的`#include "MathLibrary.h"`类。 将 的内容`MathClient.cpp`替换为以下代码：

    ```cpp
    // MathClient.cpp
    // compile with: cl /EHsc MathClient.cpp /link MathLibrary.lib

    #include <iostream>
    #include "MathLibrary.h"

    int main()
    {
        double a = 7.4;
        int b = 99;

        std::cout << "a + b = " <<
            MathLibrary::Arithmetic::Add(a, b) << std::endl;
        std::cout << "a - b = " <<
            MathLibrary::Arithmetic::Subtract(a, b) << std::endl;
        std::cout << "a * b = " <<
            MathLibrary::Arithmetic::Multiply(a, b) << std::endl;
        std::cout << "a / b = " <<
            MathLibrary::Arithmetic::Divide(a, b) << std::endl;

        return 0;
    }
    ```

1. 要生成可执行文件，请选择**Build** > 菜单栏上的**生成生成解决方案**。

## <a name="run-the-app"></a><a name="RunApp"></a>运行应用

### <a name="to-run-the-app"></a>运行应用

1. 确保**MathClient**被选为默认项目。 要选择它，请右键单击以打开**解决方案资源管理器**中的**MathClient**的快捷菜单，然后选择"**设置为启动项目**"。

1. 要运行项目，在菜单栏上，选择 **"不调试即可启动调试**"。 **Debug** >  输出应类似于：

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>另请参阅

[演练：创建和使用动态链接库 （C++）](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[桌面应用程序 (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
