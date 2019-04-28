---
title: 演练：创建和使用动态链接库 (C++)
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 248b423659d026774d4945ee6330a39dc4c6e16e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314367"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>演练：创建和使用动态链接库 (C++)

此分步演练说明如何使用 Visual Studio IDE 来创建你自己编写的动态链接库 (DLL) C++，然后将其从另一个C++应用程序。 Dll 是一种最有用的一种 Windows 组件。 若要缩小你的应用，并使其更轻松地提供服务和扩展你的应用，可以使用作为一种方式来共享代码和资源，它们。 在本演练中，将创建实现某些数学函数，一个 DLL，然后创建一个控制台应用，使用该 DLL 中的函数。 此过程中，您了解到的一些编程方法和在 Windows Dll 中使用的约定。

本演练涵盖以下任务：

- 在 Visual Studio 中创建 DLL 项目。

- 将导出的函数和变量添加到该 DLL。

- 在 Visual Studio 中创建一个控制台应用程序项目。

- 使用的函数和从控制台应用程序中的 DLL 导入的变量。

- 运行已完成的应用程序。

像静态链接的库，DLL_导出_变量、 函数和资源的名称和你的应用_导入_这些名称，若要使用这些变量、 函数和资源。 与静态链接的库，Windows 将应用程序中的导入连接到在加载时或在运行时，而不是将它们连接在链接时在 DLL 中导出。 Windows 要求不是标准的一部分的额外信息C++编译模型，以使这些连接。 MSVC 编译器实现某些 Microsoft 专用扩展C++提供此额外信息。 我们看一下，我们将介绍这些扩展。

本演练将创建两个 Visual Studio 解决方案;一个生成 DLL，另一个生成客户端应用程序。 DLL 使用 C 调用约定，因此可以使用生成的其他语言，只要平台和调用和链接约定匹配的应用中调用它。 客户端应用程序使用_隐式链接_、 Windows 位置链接到 DLL 在加载时的应用程序。 此链接，就像函数一样 DLL 提供的函数调用静态链接库中的应用。

本演练中并未涵盖一些常见的情况。 它不会显示使用C++的其他编程语言的 Dll。 它不会显示如何创建纯资源 DLL。 它也不会显示显式链接在运行时，而不是在加载时加载的 Dll 的使用。 请放心，你可以使用视觉对象C++来执行所有这些操作。 有关 Dll 的详细信息的链接，请参阅[视觉对象中的 Dll C++ ](dlls-in-visual-cpp.md)。 有关隐式链接和显式链接的详细信息，请参阅[确定要使用的链接方法](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。 了解如何创建C++以使用编程语言，使用 C 语言链接约定，请参阅使用 Dll[导出C++函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)。 有关如何创建.NET 语言配合使用的 Dll 的信息，请参阅[从 Visual Basic 应用程序调用 DLL 函数](calling-dll-functions-from-visual-basic-applications.md)。

本演练使用 Visual Studio 2017，但代码和说明的大部分也适用于早期版本。 若要生成新项目的步骤更改在 Visual Studio 2017 版本 15.3 中启动。 本演练介绍如何创建项目类型提供的更高版本和较早版本。 查找与你的 Visual Studio 版本匹配的步骤。

## <a name="prerequisites"></a>系统必备

- 运行 Microsoft Windows 7 或更高版本的计算机。 建议使用 Windows 10 以获得最佳开发体验。

- Visual Studio 2017 的副本。 有关如何下载和安装 Visual Studio 的信息，请参阅[安装 Visual Studio 2017](/visualstudio/install/install-visual-studio)。 当您运行安装程序时，请确保**使用的桌面开发C++** 检查工作负荷。 别担心，如果您未安装 Visual Studio 时安装此工作负荷。 可以再次运行安装程序并立即安装。

   ![使用的桌面开发C++ ](media/desktop-development-with-cpp.png "使用的桌面开发C++")

- 使用 Visual Studio IDE 的基础知识的了解。 如果使用过 Windows 桌面应用程序之前，您可能可以跟上。 有关的介绍，请参阅[Visual Studio IDE 功能导览](/visualstudio/ide/visual-studio-ide)。

- 了解足够的基础知识C++若要跟着介绍一起操作的语言。 别担心，我们不执行任何操作太复杂。

## <a name="create-the-dll-project"></a>创建 DLL 项目

在本系列的任务，创建适合您的 DLL 的项目、 添加代码，并生成它。 若要开始，启动 Visual Studio IDE 中，并在需要时登录。 适用于 Visual Studio 2017 版本 15.3 的说明进行操作出现在最前面。 对于早期版本的说明分为更高版本，因此跳在需要时。

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>若要在 Visual Studio 2017 版本中创建 DLL 项目，15.3 或更高版本

1. 在菜单栏上，依次选择“文件” > “新建” > “项目”，打开“新建项目”对话框。

1. 在左窗格中**新的项目**对话框框中，展开**已安装**并**Visual C++** 如有必要，然后选择**Windows 桌面**. 在中心窗格中，选择**Windows 桌面向导**。 输入`MathLibrary`中**名称**框以指定项目的名称。

   ![MathLibrary 项目命名为](media/mathlibrary-new-project-name-153.png "MathLibrary 项目命名为")

1. 选择**确定**按钮以关闭**新项目**对话框并启动**Windows 桌面项目**向导。

1. 在中**Windows 桌面项目**向导，在**应用程序类型**，选择**动态链接库 (.dll)**。

   ![在 Windows 桌面项目向导中创建 DLL](media/mathlibrary-desktop-project-wizard-dll.png "Windows 桌面项目向导中创建 DLL")

1. 选择 **“确定”** 按钮，创建单元测试项目。

> [!NOTE]
> 其他步骤需要 Visual Studio 2017 版本 15.3 中修复了问题。 按照这些说明进行操作，以确定您是否需要进行此更改。
>
>1. 在中**解决方案资源管理器**，如果它不是已选定，选择**MathLibrary**项目下**解决方案 MathLibrary**。
>
>1. 在菜单栏上，依次选择“项目” > “属性”。
>
>1. 在左窗格中**属性页**对话框中，选择**预处理器**下**配置属性** > **C /C++**. 检查的内容**预处理器定义**属性。<br/><br/>![检查预处理器定义属性](media/mathlibrary-153bug-preprocessor-definitions-check.png "检查预处理器定义属性")<br/><br/>如果您看到**MATHLIBRARY&#95;导出**中**预处理器定义**列表中，则不需要进行任何更改。 如果您看到**MathLibrary&#95;导出**相反，然后继续执行以下步骤。
>
>1. 在顶部**属性页**对话框中，更改**配置**下拉列表**所有配置**。
>
>1. 在属性窗格中选择的编辑框旁的下拉列表控件**预处理器定义**，然后选择**编辑**。<br/><br/>![编辑预处理器定义属性](media/mathlibrary-153bug-preprocessor-definitions-property.png "编辑预处理器定义属性")
>
>1. 中的顶部窗格**预处理器定义**对话框中，添加一个新的符号， `MATHLIBRARY_EXPORTS`。<br/><br/>![添加 MATHLIBRARY_EXPORTS 符号](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "添加 MATHLIBRARY_EXPORTS 符号")
>
>1. 选择**确定**以关闭**预处理器定义**对话框中，然后选择**确定**若要将所做的更改保存到项目属性。

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>若要在较旧版本的 Visual Studio 中创建 DLL 项目

1. 在菜单栏上，依次选择“文件” > “新建” > “项目”。

1. 在左窗格中**新的项目**对话框框中，展开**已安装** > **模板**，然后选择**Visual C++** ，然后在中心窗格中，选择**Win32 控制台应用程序**。 输入`MathLibrary`中**名称**编辑框，以指定项目的名称。

   ![MathLibrary 项目命名为](media/mathlibrary-project-name.png "MathLibrary 项目命名为")

1. 选择**确定**按钮以关闭**新项目**对话框并启动**Win32 应用程序向导**。

   ![Win32 应用程序向导概述](media/mathlibrary-project-wizard-1.png "Win32 应用程序向导概述")

1. 选择“下一步”按钮。 上**应用程序设置**页面上，在**应用程序类型**，选择**DLL**。

   ![在 Win32 应用程序向导中创建 DLL](media/mathlibrary-project-wizard-2.png "在 Win32 应用程序向导中创建 DLL")

1. 选择 **“完成”** 按钮创建项目。

向导完成后该解决方案，可以看到生成的项目和源代码文件中**解决方案资源管理器**Visual Studio 窗口中的。

![在 Visual Studio 中生成解决方案](media/mathlibrary-solution-explorer-153.png "在 Visual Studio 中生成解决方案")

右现在，此 DLL 不会非常相似。 接下来，创建要的函数声明您的 DLL 的标头文件导出，并将函数定义添加到 DLL 以使其更为有用。

### <a name="to-add-a-header-file-to-the-dll"></a>若要将标头文件添加到 DLL

1. 若要创建函数，标头文件的菜单栏上，选择**项目** > **添加新项**。

1. 在中**添加新项**对话框中，在左窗格中，选择**Visual C++** 。 在中间窗格中，选择 **“头文件(.h)”**。 指定`MathLibrary.h`作为标头文件的名称。

   ![在添加新项对话框添加标头](media/mathlibrary-add-new-item-header-file.png "添加标头文件中添加新项对话框")

1. 选择**添加**按钮以生成新的编辑器窗口中显示一个空白的标头文件。

   ![在编辑器中的空 MathLibrary.h 文件](media/edit-empty-mathlibrary-header.png "编辑器中的空 MathLibrary.h 文件")

1. 标头文件的内容替换为此代码：

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

此标头文件声明一些函数以生成一个通用的斐波那契序列，给定两个初始值。 调用`fibonacci_init(1, 1)`生成熟悉斐波那契数字序列。

请注意，在文件顶部的预处理器语句。 默认情况下，DLL 的新项目模板将添加 **<em>PROJECTNAME</em>&#95;导出**DLL 项目的已定义的预处理器宏。 在此示例中，Visual Studio 定义**MATHLIBRARY&#95;导出**MathLibrary DLL 项目生成时。 （Visual Studio 2017 版本 15.3 中的向导不会强制此符号定义为大写。 如果"MathLibrary"，为项目命名，则定义的符号是 MathLibrary&#95;而不是 MATHLIBRARY 导出&#95;的导出。 That's 为什么有更高版本，若要将此符号添加额外的步骤。)

当**MATHLIBRARY&#95;导出**定义宏，则**MATHLIBRARY&#95;API**宏设置`__declspec(dllexport)`函数声明上的修饰符。 此修饰符可以告诉编译器和链接器从 DLL 导出函数或变量，以供其他应用程序可以使用它。 当**MATHLIBRARY&#95;导出**未定义，例如，当标头文件包含由客户端应用程序**MATHLIBRARY&#95;API**适用`__declspec(dllimport)`修饰符添加到构造声明。 此修饰符将优化的函数或变量的应用程序中的导入。 有关详细信息，请参阅[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。

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

若要验证一切运行到目前为止，编译动态链接库。 若要编译，请选择**构建** > **生成解决方案**菜单栏上。 输出应如下所示：

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

恭喜，你已创建的 DLL 使用视觉对象C++！ 接下来，将创建使用 DLL 导出的函数的客户端应用程序。

## <a name="create-a-client-app-that-uses-the-dll"></a>创建使用该 DLL 的客户端应用程序

创建一个 DLL，必须考虑如何使用您的 DLL。 若要编译调用 DLL 导出函数的代码，声明必须包括在客户端源代码。 在链接时，当解析的 DLL 函数对这些调用，链接器必须具有*库导入*，包含有关 Windows 如何查找的函数，而不是实际的代码有关的信息的特殊库文件。 而在运行时，DLL 必须可供客户端操作系统可以找到的位置中。

若要使用的 DLL，是否你拥有或第三方 DLL，客户端应用程序项目必须找到导出的声明 DLL 的标头，为链接器和自身的 DLL 导入库。 一种方法是将所有这些文件复制到客户端项目。 对于第三方 Dll 是不太可能更改在开发您的客户端时，此方法可能的最佳方式使用它们。 但是，还生成 DLL 时，它是更好地以避免重复。 如果你正在开发的 DLL 文件的副本，可能会意外更改标头文件中一个副本，但不是另一个，或使用过期的库。 若要避免此问题，我们建议在客户端项目以包括 DLL 项目中的 DLL 标头文件中设置包含路径。 此外，客户端项目以包括从 DLL 项目的 DLL 导入库中设置的库路径。 和最后，将从 DLL 项目的生成的 DLL 复制到生成输出目录。 此步骤允许客户端应用以使用生成的相同 DLL 代码。

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>若要在 Visual Studio 2017 版本中创建客户端应用程序，15.3 或更高版本

1. 若要创建C++应用程序使用的 DLL 的创建，在菜单栏上，选择**文件** > **新建** > **项目**。

1. 在左窗格中**新的项目**对话框中，选择**Windows Desktop**下**已安装** > **Visual C++** 。 在中心窗格中，选择**Windows 桌面向导**。 指定项目名称`MathClient`，请在**名称**编辑框。

   ![客户端项目命名为](media/mathclient-new-project-name-153.png "命名客户端项目")

1. 选择**确定**以启动**Windows 桌面项目**向导。 在向导中，选择**确定**创建客户端应用程序项目。

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>若要在较旧版本的 Visual Studio 2017 中创建客户端应用

1. 若要创建C++应用程序使用的 DLL 的创建，在菜单栏上，选择**文件** > **新建** > **项目**。

1. 在左窗格中**新的项目**对话框中，选择**Win32**下**已安装** > **模板** > **可视化C++** 。 在中间窗格中，选择 **“Win32 控制台应用程序”**。 指定项目名称`MathClient`，请在**名称**编辑框。

   ![客户端项目命名为](media/mathclient-project-name.png "命名客户端项目")

1. 选择**确定**按钮以关闭**新项目**对话框并启动**Win32 应用程序向导**。 在 **“Win32 应用程序向导”** 对话框的 **“概述”** 页上，选择 **“下一步”** 按钮。

1. 上**应用程序设置**页面上，在**应用程序类型**，选择**控制台应用程序**如果尚未选择它。

1. 选择 **“完成”** 按钮创建项目。

向导完成后，为你创建的最小的控制台应用程序项目。 主源代码文件的名称是你之前输入的项目名称相同。 在此示例中，名为**MathClient.cpp**。 您可以生成它，但它尚不会使用您的 DLL。

接下来，若要在源代码中调用 MathLibrary 函数，你的项目必须包括 MathLibrary.h 文件。 可以将此标头文件复制到客户端应用程序项目中，然后将其添加到为现有的项的项目。 此方法会很不错的选择的第三方库。 但是，如果您正在处理代码适合您的 DLL 同时作为客户端，这可能导致不会显示在另一个标头文件中的更改。 若要避免此问题，可以更改**附加包含目录**中你的项目以包括原始标头的路径的路径。

### <a name="to-add-the-dll-header-to-your-include-path"></a>若要添加到该 DLL 标头将包含路径

1. 打开**属性页**对话框**MathClient**项目。

1. 在中**配置**下拉列表框中，选择**所有配置**如果尚未选择它。

1. 在左窗格中，选择**常规**下**配置属性** > **C /C++**。

1. 在属性窗格中，选择下拉列表控件旁边**附加包含目录**编辑框中，，然后选择**编辑**。

   ![编辑附加包含目录属性](media/mathclient-additional-include-directories-property.png "编辑附加包含目录属性")

1. 在顶部窗格中双击**附加包含目录**对话框，使编辑控件。

1. 在编辑控件中，指定的位置的路径**MathLibrary.h**标头文件。 在这种情况下，您可以从包含客户端项目包含在 DLL 项目中的.h 文件的文件夹中的.cpp 文件的文件夹使用相对路径。 如果客户端项目在单独的解决方案与 DLL 的解决方案的相同文件夹中，相对路径应如下所示：

   `..\..\MathLibrary\MathLibrary`

   如果 DLL 和客户端项目在同一解决方案中，或者解决方案处于不同的文件夹，然后必须相应地调整相对路径。

   ![将标头位置添加到附加包含目录属性](media/mathclient-additional-include-directories.png "将标头位置添加到附加包含目录属性")

1. 到标头文件中输入路径之后**附加包含目录**对话框框中，选择**确定**按钮以返回到**属性页**对话框中，并然后选择**确定**按钮以保存所做的更改。

现在可以包括**MathLibrary.h**文件，并使用它在客户端应用程序中声明的函数。 内容替换为**MathClient.cpp**使用以下代码：

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "pch.h"
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

此代码可以编译，但未链接，因为链接器找不到尚未生成应用程序所需的导入库。 链接器必须找到 MathLibrary.lib 文件链接才能成功。 通过将 MathLibrary.lib 文件添加到生成**附加依赖项**属性。 再次重申，您可以将库文件复制到客户端应用程序项目中，但如果正在开发的库和客户端应用程序，这可能导致不会显示在另一个副本中的更改。 若要避免此问题，可以更改**附加库目录**包含原始的库路径链接时在项目中的路径。

### <a name="to-add-the-dll-import-library-to-your-project"></a>若要添加到你的项目的 DLL 导入库

1. 打开**属性页**对话框**MathClient**项目。

1. 在中**配置**下拉列表框中，选择**所有配置**如果尚未选择它。

1. 在左窗格中，选择**输入**下**配置属性** > **链接器**。 在属性窗格中，选择下拉列表控件旁边**附加依赖项**编辑框中，，然后选择**编辑**。

   ![编辑附加依赖项属性](media/mathclient-additional-dependencies-property.png "编辑附加依赖项属性")

1. 在中**附加依赖项**对话框中，添加`MathLibrary.lib`到顶部中的列表中，编辑控件。

   ![添加库依赖项](media/mathclient-additional-dependencies.png "添加库依赖项")

1. 选择**确定**若要回到**属性页**对话框。

1. 在左窗格中，选择**常规**下**配置属性** > **链接器**。 在属性窗格中，选择下拉列表控件旁边**附加库目录**编辑框中，，然后选择**编辑**。

   ![编辑附加库目录属性](media/mathclient-additional-library-directories-property.png "编辑附加库目录属性")

1. 在顶部窗格中双击**附加库目录**对话框，使编辑控件。 在编辑控件中，指定的位置的路径**MathLibrary.lib**文件。 输入此值可使用适用于调试和发布生成的宏：

   `..\..\MathLibrary\$(IntDir)`

   ![添加库目录](media/mathclient-additional-library-directories.png "添加的库目录")

1. 一旦你输入到中的库文件路径**附加库目录**对话框框中，选择**确定**按钮以返回到**属性页**对话框。

客户端应用现在可以编译和链接成功，但它仍不具有运行所需的所有内容。 当操作系统加载您的应用程序时，它会查找 MathLibrary DLL。 如果它找不到某些系统目录、 环境路径或在本地应用程序目录中的 DLL，则加载会失败。 若要避免此问题的一种方法是将 DLL 复制到生成过程的一部分包含客户端的可执行文件的目录。 若要将该 DLL 复制，可以添加**后期生成事件**到项目中，若要添加一个命令，将 DLL 复制到生成输出目录。 仅当它缺少或已更改，并使用宏来向 / 从你的配置正确的调试版本还是发布位置复制，则此处指定的命令将复制 DLL。

### <a name="to-copy-the-dll-in-a-post-build-event"></a>若要将该 DLL 复制后期生成事件中

1. 打开**属性页**对话框**MathClient**项目如果尚未打开。

1. 在配置下拉列表中，选择**所有配置**如果尚未选择它。

1. 在左窗格中，选择**后期生成事件**下**配置属性** > **生成事件**。

1. 在属性窗格中，选择中的编辑控件**命令行**字段，并输入此命令：

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![添加生成后命令](media/mathclient-post-build-command-line.png "添加生成后命令")

1. 选择**确定**按钮以将所做的更改保存到项目属性。

现在客户端应用程序具有所生成并运行所需的一切。 通过选择来生成应用程序**构建** > **生成解决方案**菜单栏上。 **输出**Visual Studio 窗口中的应看到类似的内容：

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

恭喜，现已创建 DLL 中调用函数的应用程序。 现在运行应用程序以查看它的功能。 在菜单栏上依次选择**调试** > **启动但不调试**。 Visual Studio 会打开命令窗口运行程序。 输出的最后一个部分应如下所示：

![启动客户端应用程序而不进行调试](media/mathclient-run-without-debugging.png "启动客户端应用程序而不进行调试")

按任意键关闭命令窗口。

现在，已创建一个 DLL 和客户端应用程序，您可以进行试验。 尝试在客户端应用的代码中设置断点并在调试器中运行应用程序。 请参阅单步执行库调用时，会发生什么情况。 将其他函数添加到库，或写入另一个使用您的 DLL 的客户端应用。

在部署您的应用程序时，还必须部署它使用的 Dll。 若要将来自第三方的 Dll 生成或包含提供给您的应用程序的最简单方法是将其放在与您的应用程序相同的目录也称为*应用程序本地部署*。 有关部署的更多信息，请参阅 [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md)。

## <a name="see-also"></a>请参阅

[从 Visual Basic 应用程序调用 DLL 函数](calling-dll-functions-from-visual-basic-applications.md)
