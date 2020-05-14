---
title: 演练：创建并使用静态库 (C++)
description: 使用 C++ 在 Visual Studio 中创建静态库 (.lib)。
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 7148cc1de7c06ae57d61560311b342a1fc9dda1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335137"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>演练：创建并使用静态库

此分步演练演示如何创建用于 C++ 应用的静态库（.lib 文件）。 使用静态库是重用代码的一种绝佳方式。 你不必在要求功能的每个应用中重新实现同一例程，而只需将其写入静态数据库一次，然后从应用引用它们即可。 从静态库链接的代码成为了应用的一部分，这样你就不必安装另一个文件来使用代码。

本演练涵盖以下任务：

- [创建静态库项目](#CreateLibProject)

- [向静态库添加类](#AddClassToLib)

- [创建引用静态库的 C++ 控制台应用](#CreateAppToRefTheLib)

- [在应用中使用静态库的功能](#UseLibInApp)

- [运行应用](#RunApp)

## <a name="prerequisites"></a>先决条件

你需要了解 C++ 语言的基础知识。

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a> 创建静态库项目

关于如何创建项目的说明取决于 Visual Studio 版本。 若要查看 Visual Studio 首选项的文档，请使用“版本”选择器控件  。 它位于此页面上目录表的顶部。

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建静态库项目

1. 在菜单栏上，选择“文件”>“新建”>“项目”，打开“创建新项目”对话框     。

1. 在对话框顶部，将“语言”  设置为“C++”  ，将“平台”  设置为“Windows”  ，并将“项目类型”  设置为“库”  。

1. 从经过筛选的项目类型列表中，选择“Windows 桌面向导”，然后选择“下一步”   。

1. 在“配置新项目”页面，在“项目名称”框中输入“MathLibrary”，以指定项目的名称    。 在“解决方案名称”框中输入“StaticMath”   。 选择“创建”按钮，打开“Windows 桌面项目”对话框   。

1. 在“Windows 桌面项目”对话框的“应用程序类型”下，选择“静态库(.lib)”    。

1. 在“其他选项”下，取消选中“预编译标头”复选框（如果已选中）   。 选中“空项目”框  。

1. 选择“确定”，创建项目  。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中创建静态库项目

1. 在菜单栏上，依次选择“文件”  >“新建”  >“项目”  。

1. 在“新建项目”对话框中，选择“已安装” > “Visual C++” > “Windows 桌面”     。 在中心窗格中，选择“Windows 桌面向导”  。

1. 在“名称”框中为项目指定名称，例如 MathLibrary   。 在“解决方案名称”框中为解决方案指定名称，例如 StaticMath   。 选择“确定”  按钮。

1. 在“Windows 桌面项目”对话框的“应用程序类型”下，选择“静态库(.lib)”    。

1. 在“其他选项”下，取消选中“预编译标头”复选框（如果已选中）   。 选中“空项目”框  。

1. 选择“确定”，创建项目  。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>在 Visual Studio 2015 中创建静态库项目

1. 在菜单栏上，依次选择“文件”  >“新建”  >“项目”  。

1. 在“新建项目”对话框中，选择“已安装” > “模板” > “Visual C++” > “Win32”      。 在中间窗格中，选择 **“Win32 控制台应用程序”** 。

1. 在“名称”框中为项目指定名称，例如 MathLibrary   。 在“解决方案名称”框中为解决方案指定名称，例如 StaticMath   。 选择“确定”  按钮。

1. 在“Win32 应用程序向导”中，选择“下一步”   。

1. 在“应用程序设置”页的“应用程序类型”下，选择“静态库”    。 在“其他”选项下，取消选中“预编译标头”复选框   。 选择“完成”以创建项目  。

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a> 向静态库添加类

### <a name="to-add-a-class-to-the-static-library"></a>向静态库添加类

1. 要为新类创建头文件，请右键单击打开“解决方案资源管理器”中的“MathLibrary”项目的快捷菜单，然后依次选择“添加” > “新建项”     。

1. 在“添加新项”对话框中，选择“Visual C++” > “代码”    。 在中间窗格中，选择 **“头文件(.h)”** 。 为头文件指定名称（例如 MathLibrary.h），然后选择“添加”按钮   。 这将显示一个近乎空白的头文件。

1. 为名为 `Arithmetic` 的类添加声明，以执行常见的数学运算，如加法、减法、乘法和除法。 代码应类似于：

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

1. 要为新类创建源文件，请在“解决方案资源管理器”中打开“MathLibrary”项目的快捷菜单，然后依次选择“添加” > “新建项”     。

1. 在“添加新项”对话框的中心窗格中，选择“C++ 文件(.cpp)”   。 为源文件指定名称（例如 MathLibrary.cpp），然后选择“添加”按钮   。 将显示一个空白源文件。

1. 使用此源文件实现类 `Arithmetic` 的功能。 代码应类似于：

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

1. 若要生成静态库，请在菜单栏上依次选择“生成” > “生成解决方案”   。 该生成将创建一个可供其他程序使用的静态库 MathLibrary  。

   > [!NOTE]
   > 如果使用 Visual Studio 命令行生成，必须分两个步骤来生成程序。 首先，运行 `cl /c /EHsc MathLibrary.cpp` 以编译代码并创建名为 MathLibrary.obj 的对象文件  。（`cl` 命令可调用编译器 Cl.exe，并且 `/c` 选项可指定编译而无需链接。 有关详细信息，请参阅 [/c（在不链接的情况下进行编译）](../build/reference/c-compile-without-linking.md)。接下来，运行 `lib MathLibrary.obj` 以链接代码并创建静态库 MathLibrary.lib  。 （`lib` 命令可调用库管理器 Lib.exe。 有关详细信息，请参阅 [LIB Reference](../build/reference/lib-reference.md)。）

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a> 创建引用静态库的 C++ 控制台应用

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建引用静态库的 C++ 控制台应用

1. 在“解决方案资源管理器”中，右键单击顶部节点“解决方案 StaticMath”，打开快捷菜单   。 选择“添加” > “新建项目”，打开“添加新项目”对话框    。

1. 在对话框的顶部，将“项目类型”筛选器设置为“控制台”   。

1. 从筛选的项目类型列表中，选择“控制台应用”，然后选择“下一步”   。 在下一页中，在“名称”框中输入“MathClient”，以指定项目的名称   。

1. 选择“创建”  按钮创建客户端项目。

1. 创建控制台应用后，将为你创建一个空程序。 源文件的名称与你之前选择的名称相同。 在此示例中，命名为 `MathClient.cpp`。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>在 Visual Studio 2017 中创建引用静态库的 C++ 控制台应用

1. 在“解决方案资源管理器”中，右键单击顶部节点“解决方案 StaticMath”，打开快捷菜单   。 选择“添加” > “新建项目”，打开“添加新项目”对话框    。

1. 在“添加新项目”对话框中，选择“已安装” > “Visual C++” > “Windows 桌面”     。 在中心窗格中，选择“Windows 桌面向导”  。

1. 在“名称”框中为项目指定名称，例如 MathClient   。 选择“确定”  按钮。

1. 在“Windows 桌面项目”对话框的“应用程序类型”下，选择“控制台应用程序(.exe)”    。

1. 在“其他选项”下，取消选中“预编译标头”复选框（如果已选中）   。

1. 选择“确定”，创建项目  。

1. 创建控制台应用后，将为你创建一个空程序。 源文件的名称与你之前选择的名称相同。 在此示例中，命名为 `MathClient.cpp`。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>在 Visual Studio 2015 中创建引用静态库的 C++ 控制台应用

1. 在“解决方案资源管理器”中，右键单击顶部节点“解决方案 StaticMath”，打开快捷菜单   。 选择“添加” > “新建项目”，打开“添加新项目”对话框    。

1. 在“添加新项目”对话框中，选择“已安装” > “Visual C++” > “Win32”     。 在中间窗格中，选择 **“Win32 控制台应用程序”** 。

1. 在“名称”框中为项目指定名称，例如 MathClient   。 选择“确定”  按钮。

1. 在“Win32 应用程序向导”对话框中，选择“下一步”   。

1. 在“应用程序设置”页的“应用程序类型”下，确保已选中“控制台应用程序”    。 在“其他选项”下，取消选中“预编译标头”，然后选中“空项目”复选框    。 选择“完成”以创建项目  。

1. 若要将源文件添加到空项目中，请右键单击打开“解决方案资源管理器”中“MathClient”项目的快捷菜单，然后选择“添加”>“新项”     。

1. 在“添加新项”对话框中，选择“Visual C++” > “代码”    。 在中间窗格中，选择 **“C++ 文件(.cpp)”** 。 为源文件指定名称（例如 MathClient.cpp），然后选择“添加”按钮   。 将显示一个空白源文件。

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a> 在应用中使用静态库的功能

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在应用中使用静态库的功能

1. 必须引用静态库才能使用其中的算术例程。 打开“解决方案资源管理器”中“MathClient”项目的快捷菜单，然后选择“添加” > “引用”     。

1. **“添加引用”** 对话框列出了可以引用的库。 “项目”选项卡列出当前解决方案中的项目及其引用的任何库  。 打开“项目”选项卡，选中“MathLibrary”复选框，然后选择“确定”按钮    。

1. 若要引用 `MathLibrary.h` 头文件，必须修改包含的目录路径。 在“解决方案资源管理器”中，右键单击“MathClient”，打开快捷菜单   。 选择“属性”，打开“MathClient 属性页”对话框   。

1. 在“MathClient 属性页”对话框中，将“配置”下拉列表设置为“所有配置”    。 将“平台”下拉列表设置为“所有平台”   。

1. 选择“配置属性” > “C/C++” > “常规”属性页    。 在“附加包含目录”属性中，指定“MathLibrary”目录的路径，或浏览该目录   。

   浏览目录路径：

   1. 打开“附加包含目录”属性值下拉列表，然后选择“编辑”   。

   1. 在“附加包含目录”对话框中，双击文本框顶部  。 然后选择行末尾的省略号按钮 (…)  。

   1. 在“选择目录”对话框中，向上导航一级，然后选择“MathLibrary”目录   。 然后选择“选择文件夹”按钮，保存所做的选择  。

   1. 在“附加包含目录”对话框中，选择“确定”按钮   。

   1. 在“属性页”对话框中，选择“确定”按钮以保存对项目所做的更改   。

1. 现在可以通过在代码中包含 `#include "MathLibrary.h"` 标头来使用此应用程序中的 `Arithmetic` 类。 用以下代码替换 `MathClient.cpp` 的内容：

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

1. 若要生成可执行文件，请在菜单栏上选择“生成” > “生成解决方案”   。

## <a name="run-the-app"></a><a name="RunApp"></a> 运行应用

### <a name="to-run-the-app"></a>运行应用

1. 请确保已将“MathClient”选为默认项目  。 若要选择它，请右键单击打开“解决方案资源管理器”中“MathClient”的快捷菜单，然后选择“设置为启动项目”    。

1. 要运行项目，请在菜单栏上选择“调试”   > “开始执行(不调试)”  。 输出应类似于：

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>请参阅

[演练：创建和使用动态链接库 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[桌面应用程序 (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
