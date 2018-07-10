---
title: 演练： 创建和使用你自己动态链接库 （c + +） |Microsoft 文档
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19c9c013d591f4c6de14ecd4a2c582d8f0f3e4d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392583"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>演练： 创建和使用你自己动态链接库 （c + +）

此分步演练演示如何使用 Visual Studio IDE 来创建你自己编写 c + + 中的动态链接库 (DLL)，然后从另一个 c + + 应用程序中使用它。 Dll 是最有用的一种 Windows 组件之一。 若要缩小你的应用，并使其更轻松地服务和扩展你的应用程序，可以使用作为一种方式来共享代码和资源，它们。 在本演练中，你创建一个 DLL，它实现某些数学函数，然后创建一个控制台应用程序使用 DLL 中的函数。 与此同时，你获得的简介的一些编程的方法和在 Windows Dll 中使用的约定。

本演练涵盖以下任务：

- 在 Visual Studio 中创建 DLL 项目。

- 将导出的函数和变量添加到该 DLL。

- 在 Visual Studio 中创建一个控制台应用程序项目。

- 使用的函数和从控制台应用程序中的 DLL 导入的变量。

- 运行已完成的应用程序。

如静态链接的库，DLL_导出_变量、 函数和资源的名称和你的应用程序_导入_这些名称用于这些变量、 函数和资源。 与静态链接的库，不同，Windows 将应用程序中的导入连接到在加载时或在运行时，而不是将它们连接在链接时在 DLL 中导出。 Windows 要求不属于标准的 c + + 编译模型，以使这些连接的额外信息。 Visual c + + 编译器实现 c + + 提供此额外信息某些 Microsoft 专用扩展。 我们看一下，我们会介绍这些扩展。

本演练将创建两个 Visual Studio 解决方案;一个生成 DLL，另一个生成客户端应用程序。 DLL 使用 C 调用约定，因此可以从，只要的平台和调用和链接约定相匹配，通过使用其他语言，生成的应用程序对它进行调用。 客户端应用程序使用_隐式链接_、 Windows 其中链接到 DLL 在加载时的应用程序。 这使应用可以调用静态链接库中的一样函数 DLL 提供的函数。

本演练中未包含的某些常见的情况。 它不显示使用的 c + + Dll 的其他编程语言。 它不显示如何创建纯资源 DLL。 它也不显示显式链接加载 Dll，在运行时中，而不是在加载时使用。 放心，你可以使用 Visual c + + 执行所有这些操作。 有关 Dll 的详细信息的链接，请参阅[Visual c + + 中的 Dll](../build/dlls-in-visual-cpp.md)。 有关隐式链接和显式链接的详细信息，请参阅[确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。 有关创建适用于编程语言中使用 C 语言链接约定的 c + + Dll 的信息，请参阅[用于 C 语言可执行文件中导出 c + + 函数](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)。 有关如何创建 Dll 以用于.NET 语言的信息，请参阅[从 Visual Basic 应用程序调用 DLL 函数](../build/calling-dll-functions-from-visual-basic-applications.md)。

本演练使用 Visual Studio 2017 年，但代码和说明的大多数是适用于早期版本。 若要生成新项目的步骤更改在 Visual Studio 2017 版本 15.3 中启动。 本演练介绍如何创建新版和旧版的项目。 查找 Visual Studio 的版本匹配的步骤。

## <a name="prerequisites"></a>系统必备

- 运行 Microsoft Windows 7 或更高版本的计算机。 为获得最佳的开发体验，我们建议 Windows 10。

- Visual Studio 2017 的副本。 有关如何下载和安装 Visual Studio 的信息，请参阅[安装 Visual Studio 2017](/visualstudio/install/install-visual-studio)。 当你运行安装程序时，请确保**使用 c + + 桌面开发**检查工作负荷。 如果你在安装 Visual Studio 时，未安装此工作负荷，请不要担心。 你可以再次运行安装程序并立即安装。

   ![使用 c + + 桌面开发](media/desktop-development-with-cpp.png "使用 c + + 桌面开发")

- 使用 Visual Studio IDE 的基础知识的了解。 如果你已使用在之前的 Windows 桌面应用，你可能保持同步。 有关简介，请参阅[Visual Studio IDE 功能教程](/visualstudio/ide/visual-studio-ide)。

- 你需要了解的足够多的 c + + 语言要遵循的基础知识。 别担心，我们不执行任何操作太复杂。

## <a name="create-the-dll-project"></a>创建 DLL 项目

在此任务组，为您的 DLL 创建一个项目，添加代码，并生成它。 若要开始，启动 Visual Studio IDE，并登录，如果你需要。 Visual Studio 2017 版本 15.3 的说明出现在最前面。 对于早期版本的说明进入更高版本时，因此跳过这些必要时。

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>在 Visual Studio 自 2017 年 1 版本中创建 DLL 项目，15.3 或更高版本

1. 在菜单栏上，选择**文件**，**新建**，**项目**以打开**新项目**对话框。

1. 在左窗格中**新项目**对话框框中，展开**已安装**和**Visual c + +** 如果需要，然后选择**Windows 桌面**。 在中心窗格中，选择**Windows 桌面向导**。 输入`MathLibrary`中**名称**框以指定项目的名称。

   ![将 MathLibrary 项目](media/mathlibrary-new-project-name-153.png "MathLibrary 项目")

1. 选择**确定**按钮以关闭**新项目**对话框并开始**Windows 桌面项目**向导。

1. 在**Windows 桌面项目**向导时下,**应用程序类型**，选择**动态链接库 (.dll)**。

   ![在 Windows 桌面项目向导中创建 DLL](media/mathlibrary-desktop-project-wizard-dll.png "在 Windows 桌面项目向导中创建 DLL")

1. 选择 **“确定”** 按钮，创建单元测试项目。

> [!NOTE]
> 在 Visual Studio 2017 版本 15.3 修复某个问题，需要执行其他步骤。 按照这些说明来确定是否需要进行此更改。
>
>1. 在**解决方案资源管理器**，如果它尚不选择**MathLibrary**项目下**解决方案 MathLibrary**。
>
>1. 在菜单栏上，依次选择“项目”、“属性”。
>
>1. 在左窗格中**属性页**对话框中，选择**预处理器**下**配置属性**， **C/c + +**。 请检查内容**预处理器定义**属性。<br/><br/>![检查预处理器定义属性](media/mathlibrary-153bug-preprocessor-definitions-check.png "检查预处理器定义属性")<br/><br/>如果你看到**MATHLIBRARY&#95;导出**中**预处理器定义**列表，则不需要更改任何内容。 如果你看到**MathLibrary&#95;导出**相反，然后继续执行以下步骤。
>
>1. 在顶部**属性页**对话框中，更改**配置**下拉到**所有配置**。
>
>1. 在属性窗格中，选择旁边的编辑框的下拉列表控件**预处理器定义**，然后选择**编辑**。<br/><br/>![编辑预处理器定义属性](media/mathlibrary-153bug-preprocessor-definitions-property.png "编辑预处理器定义属性")
>
>1. 中的顶部窗格**预处理器定义**对话框中，添加一个新的符号， `MATHLIBRARY_EXPORTS`。<br/><br/>![添加 MATHLIBRARY_EXPORTS 符号](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "添加 MATHLIBRARY_EXPORTS 符号")
>
>1. 选择**确定**关闭**预处理器定义**对话框中，然后选择**确定**若要将所做的更改保存到项目属性。

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>若要在较旧版本的 Visual Studio 中创建 DLL 项目

1. 在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。

1. 在左窗格中**新项目**对话框框中，展开**已安装**，**模板**，然后选择**Visual c + +**，然后在中心窗格中，选择**Win32 控制台应用程序**。 输入`MathLibrary`中**名称**编辑框，以指定项目的名称。

   ![将 MathLibrary 项目](media/mathlibrary-project-name.png "MathLibrary 项目")

1. 选择**确定**按钮以关闭**新项目**对话框并开始**Win32 应用程序向导**。

   ![Win32 应用程序向导概述](media/mathlibrary-project-wizard-1.png "Win32 应用程序向导概述")

1. 选择“下一步”按钮。 上**应用程序设置**页上，在**应用程序类型**，选择**DLL**。

   ![在 Win32 应用程序向导中创建 DLL](media/mathlibrary-project-wizard-2.png "在 Win32 应用程序向导中创建 DLL")

1. 选择 **“完成”** 按钮创建项目。

在向导完成后解决方案，你可以看到中生成的项目和源文件**解决方案资源管理器**Visual Studio 中的窗口。

![在 Visual Studio 中生成解决方案](media/mathlibrary-solution-explorer-153.png "在 Visual Studio 中生成解决方案")

右现在，此 DLL 不执行非常相似。 接下来，创建要将函数声明 DLL 的标头文件导出，，然后将函数定义添加到 DLL 以使其更为有用。

### <a name="to-add-a-header-file-to-the-dll"></a>若要将标头文件添加到 DLL

1. 若要创建您的函数的标头文件的菜单栏上，选择**项目**，**添加新项**。

1. 在**添加新项**对话框中，在左侧的窗格中，选择**Visual c + +**。 在中间窗格中，选择 **“头文件(.h)”**。 指定`MathLibrary.h`作为标头文件的名称。

   ![在添加新项对话框添加标头](media/mathlibrary-add-new-item-header-file.png "添加标头文件中添加新项对话框")

1. 选择**添加**按钮以生成一个空白头文件，其中显示在新的编辑器窗口中。

   ![在编辑器中的空 MathLibrary.h 文件](media/edit-empty-mathlibrary-header.png "编辑器中的空 MathLibrary.h 文件")

1. 标头文件的内容替换此代码：

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

此标头文件声明以产生通用斐波那契序列，给定两个初始值某些函数。 调用`fibonacci_init(1, 1)`生成熟悉斐波那契数字序列。

请注意在文件顶部的预处理器语句。 默认情况下，DLL 的新项目模板将添加 ***PROJECTNAME *&#95;导出**DLL 项目的已定义的预处理器宏。 在此示例中，Visual Studio 定义**MATHLIBRARY&#95;导出**生成 MathLibrary DLL 项目时。 （在 Visual Studio 2017 版本 15.3 向导不会强制为大写形式此符号定义。 如果命名你的项目"MathLibrary"，然后定义的符号是 MathLibrary&#95;而不是 MATHLIBRARY 导出&#95;导出。 That's 原因有更高版本以将此符号添加的额外步骤。)

当**MATHLIBRARY&#95;导出**定义宏， **MATHLIBRARY&#95;API**宏设置`__declspec(dllexport)`函数声明上的修饰符。 此修饰符，可以告诉编译器和链接器以从 DLL 导出函数或变量，以便它可以由其他应用程序。 当**MATHLIBRARY&#95;导出**未定义，例如，当标头文件包括由客户端应用程序， **MATHLIBRARY&#95;API**适用`__declspec(dllimport)`修饰符添加到构造声明。 此修饰符将优化的导入的函数或应用程序中的变量。 有关详细信息，请参阅[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。

### <a name="to-add-an-implementation-to-the-dll"></a>若要将实现添加到 DLL

1. 在编辑器窗口中，选择的选项卡**MathLibrary.cpp**如果已打开。 如果不是，在**解决方案资源管理器**，打开**MathLibrary.cpp**中**源文件**文件夹**MathLibrary**项目。

1. 在编辑器中，将 MathLibrary.cpp 文件的内容替换为以下代码：

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h"
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

若要验证一切就绪到目前为止，编译动态链接库。 若要编译，选择**生成**，**生成解决方案**菜单栏上。 输出应如下所示：

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

祝贺你，你已创建使用 Visual c + + DLL ！ 接下来，你将创建的客户端应用程序使用 DLL 导出的函数。

## <a name="create-a-client-app-that-uses-the-dll"></a>创建的客户端应用程序使用 DLL

创建 DLL 时，必须考虑如何使用您的 DLL。 若要编译调用由 DLL 导出的函数的代码，必须在客户端的源代码包含声明。 在链接时，这些对 DLL 函数的调用时解析，链接器必须具有*导入库*，一种特殊的库文件，其中包含有关如何查找函数，而不是实际的代码适用于 Windows 的信息。 和在运行时，DLL 必须可供客户端，操作系统可找到的位置中。

可以使用一个 DLL，是否你拥有或第三方 DLL，客户端应用程序项目必须能够找到声明 DLL 的标头导出时，为链接器中和本身的 DLL 导入库。 若要执行此操作的一种方法是将所有这些文件复制到客户端项目。 对于第三方 Dll 是不太可能更改正在开发你的客户端时，这可能是使用它们的最佳方式。 但是，还生成 DLL，则最好避免重复。 如果你正在开发的 DLL 文件的副本，你可能会意外地更改一个副本而非另中的标头文件或使用过期的库。 若要避免此问题，我们建议在客户端项目包括 DLL 标头文件从 DLL 项目中设置包含路径。 此外，在你的客户端项目以包括从 DLL 项目的 DLL 导入库中设置的库路径。 和最后，将从 DLL 项目的生成的 DLL 复制到生成输出目录。 这可以确保客户端应用程序使用相同的 DLL 代码生成。

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>在 Visual Studio 自 2017 年 1 版本中创建客户端应用程序，15.3 或更高版本

1. 若要创建的 c + + 应用程序使用 DLL 你刚刚创建，在菜单栏上，选择**文件**，**新建**，**项目**。

1. 在左窗格中**新项目**对话框中，选择**Windows 桌面**下**已安装**， **Visual c + +**。 在中心窗格中，选择**Windows 桌面向导**。 为项目指定名称，`MathClient`中**名称**编辑框。

   ![将客户端项目](media/mathclient-new-project-name-153.png "命名客户端项目")

1. 选择**确定**启动**Windows 桌面项目**向导。 在向导中，选择**确定**创建客户端应用程序项目。

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>若要在较旧版本的 Visual Studio 2017 创建一个客户端应用

1. 若要创建的 c + + 应用程序使用 DLL 你刚刚创建，在菜单栏上，选择**文件**，**新建**，**项目**。

1. 在左窗格中**新项目**对话框中，选择**Win32**下**已安装**，**模板**， **Visual c + +**. 在中间窗格中，选择 **“Win32 控制台应用程序”**。 为项目指定名称，`MathClient`中**名称**编辑框。

   ![将客户端项目](media/mathclient-project-name.png "命名客户端项目")

1. 选择**确定**按钮以关闭**新项目**对话框并开始**Win32 应用程序向导**。 在 **“Win32 应用程序向导”** 对话框的 **“概述”** 页上，选择 **“下一步”** 按钮。

1. 上**应用程序设置**页上，在**应用程序类型**，选择**控制台应用程序**如果尚未选择。

1. 选择 **“完成”** 按钮创建项目。

向导完成后，将为你创建的最小的控制台应用程序项目。 主源代码文件的名称是你之前输入的项目名称相同。 在此示例中，名为**MathClient.cpp**。 你可以生成它，但它不会将你的 DLL。

接下来，若要在源代码中调用 MathLibrary 函数，你的项目必须包括 MathLibrary.h 文件。 你无法将此标头文件复制到客户端应用程序项目，然后将其添加到现有项的项目。 这可以是一个不错的第三方库选择。 但是，如果你正在的代码上适合您的 DLL 在同一时间作为你的客户端，这可能导致不会反映在另一个标头文件中的更改。 若要避免此问题，可以更改**附加包含目录**项目以包括原始标头的路径中的路径。

### <a name="to-add-the-dll-header-to-your-include-path"></a>若要添加到 DLL 标头你包括路径

1. 打开**属性页**对话框**MathClient**项目。

1. 在**配置**下拉列表框中，选择**所有配置**如果尚未选择。

1. 在左窗格中，选择**常规**下**配置属性**， **C/c + +**。

1. 在属性窗格中，选择的下拉列表控件旁边**附加包含目录**编辑框时，，然后选择**编辑**。

   ![编辑附加包含目录属性](media/mathclient-additional-include-directories-property.png "编辑附加包含目录属性")

1. 顶部窗格中双击**附加包含目录**对话框中，若要启用编辑控件。

1. 在编辑控件中，指定的位置的路径**MathLibrary.h**标头文件。 在这种情况下，你可以使用相对路径：

   `..\..\MathLibrary\MathLibrary`

   ![将标头位置添加到附加包含目录属性](media/mathclient-additional-include-directories.png "将标头位置添加到附加包含目录属性")

1. 已到标头文件中输入路径后**附加包含目录**对话框框中，选择**确定**按钮以返回到**属性页**对话框中，和然后选择**确定**按钮以保存所做的更改。

你现在可以包含**MathLibrary.h**文件中并使用它在客户端应用程序中声明的函数。 内容替换**MathClient.cpp**使用以下代码：

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "stdafx.h"
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

此代码可以编译，但未链接，因为链接器找不到尚未生成应用程序所需的导入库。 链接器必须能够找到 MathLibrary.lib 文件链接才能成功。 你必须将 MathLibrary.lib 文件添加到生成中通过设置**附加依赖项**属性。 同样，你可以将库文件复制到客户端应用程序项目中，但如果正在开发的库和客户端应用程序，这可能导致不会反映在另一个副本中的更改。 若要避免此问题，可以更改**附加库目录**在项目链接时包含原始库的路径中的路径。

### <a name="to-add-the-dll-import-library-to-your-project"></a>将 DLL 导入库添加到你的项目

1. 打开**属性页**对话框**MathClient**项目。

1. 在**配置**下拉列表框中，选择**所有配置**如果尚未选择。

1. 在左窗格中，选择**输入**下**配置属性**，**链接器**。 在属性窗格中，选择的下拉列表控件旁边**附加依赖项**编辑框时，，然后选择**编辑**。

   ![编辑的附加依赖项属性](media/mathclient-additional-dependencies-property.png "编辑附加依赖项属性")

1. 在**附加依赖项**对话框中，添加`MathLibrary.lib`到顶部中的列表中，编辑控件。

   ![添加库依赖项](media/mathclient-additional-dependencies.png "添加库依赖项")

1. 选择**确定**回到**属性页**对话框。

1. 在左窗格中，选择**常规**下**配置属性**，**链接器**。 在属性窗格中，选择的下拉列表控件旁边**附加库目录**编辑框时，，然后选择**编辑**。

   ![编辑附加库目录属性](media/mathclient-additional-library-directories-property.png "编辑附加库目录属性")

1. 顶部窗格中双击**附加库目录**对话框中，若要启用编辑控件。 在编辑控件中，指定的位置的路径**MathLibrary.lib**文件。 输入此值，以使用适用于调试和发布生成的宏：

   `..\..\MathLibrary\$(IntDir)`

   ![将库目录添加](media/mathclient-additional-library-directories.png "添加的库目录")

1. 已输入到中的库文件路径后**附加库目录**对话框框中，选择**确定**按钮以返回到**属性页**对话框。

客户端应用程序可以现在编译和链接才能成功，但它仍不具有所需运行的一切。 当操作系统加载你的应用时，它会查找 MathLibrary DLL。 如果某些系统目录、 环境路径或的本地应用程序目录中找不到该 DLL，则加载会失败。 若要避免此问题的一种方法是将 DLL 复制到生成过程的一部分包含客户端可执行文件的目录。 若要将 DLL 复制，可以添加**后期生成事件**到你的项目，添加命令，将 DLL 复制到生成输出目录。 此处指定的命令将 DLL 复制仅当它缺少或已更改，并使用宏来复制到和从你的配置正确的调试版本还是发布位置。

### <a name="to-copy-the-dll-in-a-post-build-event"></a>将 DLL 复制在生成后事件

1. 打开**属性页**对话框**MathClient**项目如果尚未打开。

1. 在配置下拉列表中，选择**所有配置**如果尚未选择。

1. 在左窗格中，选择**后期生成事件**下**配置属性**，**生成事件**。

1. 在属性窗格中，选择中的编辑控件**命令行**字段，然后输入以下命令：

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![添加后期生成命令](media/mathclient-post-build-command-line.png "添加后期生成命令")

1. 选择**确定**按钮以将所做的更改保存到项目属性。

现在你的客户端应用程序所生成并运行所需的一切。 通过选择生成应用程序**生成**，**生成解决方案**菜单栏上。 **输出**Visual Studio 中的窗口应类似如下内容：

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

祝贺你，你已创建的应用程序在 DLL 中调用函数。 现在运行你的应用程序，以查看它能做什么。 在菜单栏上，选择**调试**，**启动但不调试**。 Visual Studio 将打开命令窗口运行程序。 输出的最后部分应如下所示：

![启动客户端应用程序而不调试](media/mathclient-run-without-debugging.png "启动客户端应用程序而不进行调试")

按任意键关闭命令窗口。

现在，你已创建一个 DLL 和客户端应用程序，你可以进行试验。 请尝试在客户端应用程序中的代码中设置断点并在调试器中运行应用程序。 请参阅你单步执行库调用时会发生什么情况。 将其他函数添加到库中，或写入另一个客户端应用程序使用 DLL。

在部署你的应用程序时，你还必须部署它使用的 Dll。 将从第三方的 Dll 生成或包含提供给你的应用程序的最简单方法是将它们放在与你的应用，相同的目录也称为*应用本地部署*。 有关部署的详细信息，请参阅[Visual c + + 中的部署](..\ide\deployment-in-visual-cpp.md)。

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)  
[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)  
[演练：部署程序 (C++)](../ide/walkthrough-deploying-your-program-cpp.md)  
[从 Visual Basic 应用程序调用 DLL 函数](../build/calling-dll-functions-from-visual-basic-applications.md)