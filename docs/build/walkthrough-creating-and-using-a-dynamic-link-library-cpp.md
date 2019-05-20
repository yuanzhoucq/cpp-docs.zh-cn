---
title: 演练：创建和使用自己的动态链接库 (C++)
description: 使用 C++ 在 Visual Studio 中创建 Windows 动态链接库 (DLL)。
ms.custom: conceptual
ms.date: 04/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 53cde029973c14bfc5aae521946ebeadbed738ca
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611988"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>演练：创建和使用自己的动态链接库 (C++)

此分步演练演示如何使用 Visual Studio IDE 通过 C++ 编写自己的动态链接库 (DLL)，然后从另一个 C++ 应用中使用它。 DLL（在基于 UNIX 的操作系统中也称为共享库）是最有用的 Windows 组件类型之一。 可以将其用作共享代码和资源、缩小应用大小以及更轻松地为应用提供服务和扩展的一种方式。 在本演练中，将创建一个可实现某些数学函数的 DLL，然后创建一个使用该 DLL 中的函数的控制台应用。 在此过程中，将了解 Windows DLL 中使用的一些编程技术和约定。

本演练涵盖以下任务：

- 在 Visual Studio 中创建 DLL 项目。

- 将导出的函数和变量添加到该 DLL。

- 在 Visual Studio 中创建一个控制台应用项目。

- 在该控制台应用中使用从 DLL 导入的函数和变量。

- 运行已完成的应用。

与静态链接库类似，DLL 按名称导出变量、函数和资源，而你的应用会导入这些名称以使用这些变量、函数和资源。 与静态链接库不同的是，Windows 在加载时或在运行时将应用中的导入连接到 DLL 中的导出，而不是在链接时连接它们。 Windows 需要不属于标准 C++ 编译模型的额外信息才能建立这些连接。 MSVC 编译器实现了一些 Microsoft 专用 C++ 扩展，以提供此额外信息。 接下来我们将介绍这些扩展。

本演练将创建两个 Visual Studio 解决方案；一个生成 DLL，另一个生成客户端应用。 DLL 使用 C 调用约定，因此只要平台与调用和链接约定匹配，即可从使用其他语言生成的应用调用它。 客户端应用使用隐式链接，其中 Windows 在加载时将应用链接到 DLL。 此链接允许应用调用 DLL 提供的函数，就像调用静态链接库中的函数一样。

本演练并不涵盖一些常见的情况。 它不会演示其他编程语言对 C++ DLL 的使用。 它不会演示如何创建纯资源 DLL。 它也不会演示使用显式链接在运行时（而不是在加载时）加载 DLL。 请放心，可以使用 Visual C++ 执行所有这些操作。 有关 DLL 的详细信息的链接，请参阅[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)。 有关隐式链接和显式链接的详细信息，请参阅[确定要使用的链接方法](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)。 有关创建用于使用 C 语言链接约定的编程语言的 C++ DLL 的信息，请参阅[导出 C++ 函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)。 有关如何创建用于 .NET 语言的 DLL 的信息，请参阅[从 Visual Basic 应用程序调用 DLL 函数](calling-dll-functions-from-visual-basic-applications.md)。

## <a name="prerequisites"></a>系统必备

- 运行 Microsoft Windows 7 或更高版本的计算机。 建议使用 Windows 10 以实现最佳开发体验。

- Visual Studio 的副本。 有关如何下载和安装 Visual Studio 的信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。 运行安装程序时，请务必选中“使用 C++ 的桌面开发”工作负载。 如果在安装 Visual Studio 时未安装此工作负载，请不要担心。 可以再次运行安装程序并立即安装。

   ![使用 C++ 的桌面开发](media/desktop-development-with-cpp.png "使用 C++ 的桌面开发")

- 了解使用 Visual Studio IDE 的基础知识。 如果你之前使用过 Windows 桌面应用，可能具备一定的相关知识。 有关简介，请参阅 [Visual Studio IDE 功能导览](/visualstudio/ide/visual-studio-ide)。

- 了解足够的 C++ 语言基础知识以供继续操作。 别担心，我们不会执行过于复杂的操作。

## <a name="create-the-dll-project"></a>创建 DLL 项目

在本系列的任务中，将创建一个 DLL 项目，添加代码，并生成它。 首先，启动 Visual Studio IDE，并在需要时登录。 根据使用的 Visual Studio 版本，操作说明会略有不同。 请确保在本页左上角的控件中选择了正确的版本。

::: moniker range="=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建 DLL 项目

1. 在菜单栏上，选择“文件”>“新建”>“项目”，打开“创建新项目”对话框。

   ![创建新的 DLL 项目](media/create-new-dll-project-2019.png "创建 MathLibrary 项目")

1. 在对话框顶部，将“语言”设置为“C++”，将“平台”设置为“Windows”，并将“项目类型”设置为“库”。 

1. 从经过筛选的项目类型列表中，选择“动态链接库(DLL)”，然后选择“下一步”。 在下一页中的“名称”框内输入 `MathLibrary` 以指定项目的名称，并根据需要指定项目位置。

1. 选择“创建”按钮创建项目。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中创建 DLL 项目

1. 在菜单栏上，选择“文件”>“新建”>“项目”，打开“新建项目”对话框。

1. 在“新建项目”对话框的左侧窗格中，根据需要展开“已安装”和“Visual C++”，然后选择“Windows 桌面”。 在中心窗格中，选择“Windows 桌面向导”。 在“名称”框中输入 `MathLibrary`，指定项目的名称。

   ![为 MathLibrary 项目命名](media/mathlibrary-new-project-name-153.png "为 MathLibrary 项目命名")

1. 选择“确定”按钮以关闭“新建项目”对话框并启动“Windows 桌面项目”向导。

1. 在“Windows 桌面项目”向导的“应用程序类型”下，选择“动态链接库(.dll)”。

   ![在 Windows 桌面项目向导中创建 DLL](media/mathlibrary-desktop-project-wizard-dll.png "在 Windows 桌面项目向导中创建 DLL")

1. 选择 **“确定”** 按钮，创建单元测试项目。

> [!NOTE]
> 修复 Visual Studio 2017 版本 15.3 中的问题需要执行其他步骤。 请按照以下说明操作，确定是否需要进行此更改。
>
>1. 在“解决方案资源管理器”中，如果尚未在解决方案“MathLibrary”下选择“MathLibrary”项目，请选中它。
>
>1. 在菜单栏上，选择“项目”>“属性”。
>
>1. 在“属性页”对话框的左窗格中，在“配置属性” > “C/C++”下，选择“预处理器”。 检查“预处理器定义”属性的内容。<br/><br/>![检查预处理器定义属性](media/mathlibrary-153bug-preprocessor-definitions-check.png "检查预处理器定义属性")<br/><br/>如果在“预处理器定义”列表中看到“MATHLIBRARY&#95;EXPORTS”，则无需更改任何内容。 但如果看到“MathLibrary&#95;EXPORTS”，则继续执行以下步骤。
>
>1. 在“属性页”对话框顶部，将“配置”下拉列表更改为“所有配置”。
>
>1. 在属性窗格中，选择“预处理器定义”的编辑框旁的下拉控件，然后选择“编辑”。<br/><br/>![编辑预处理器定义属性](media/mathlibrary-153bug-preprocessor-definitions-property.png "编辑预处理器定义属性")
>
>1. 在“预处理器定义”对话框的顶部窗格中，添加一个新符号 `MATHLIBRARY_EXPORTS`。<br/><br/>![添加 MATHLIBRARY_EXPORTS 符号](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "添加 MATHLIBRARY_EXPORTS 符号")
>
>1. 选择“确定”以关闭“预处理器定义”对话框，然后选择“确定”以保存对项目属性的更改。

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>在较旧版本的 Visual Studio 中创建 DLL 项目

1. 在菜单栏上选择“文件”>“新建”>“项目”。

1. 在“新建项目”对话框的左窗格中，展开“已安装” > “模板”，并选择“Visual C++”，然后在中心窗格中，选择“Win32 控制台应用程序”。 在“名称”编辑框中输入 `MathLibrary`，指定项目的名称。

   ![为 MathLibrary 项目命名](media/mathlibrary-project-name.png "为 MathLibrary 项目命名")

1. 选择“确定”按钮以关闭“新建项目”对话框并启动“Win32 应用程序向导”。

   ![Win32 应用程序向导概述](media/mathlibrary-project-wizard-1.png "Win32 应用程序向导概述")

1. 选择“下一步”按钮。 在“应用程序设置”页的“应用程序类型”下，选择“DLL”。

   ![在 Win32 应用程序向导中创建 DLL](media/mathlibrary-project-wizard-2.png "在 Win32 应用程序向导中创建 DLL")

1. 选择 **“完成”** 按钮创建项目。

向导完成解决方案后，就可以在 Visual Studio 中的“解决方案资源管理器”窗口中看到生成的项目和源文件了。

![在 Visual Studio 中生成的解决方案](media/mathlibrary-solution-explorer-153.png "在 Visual Studio 中生成的解决方案")

目前，此 DLL 并没有起到很大的作用。 接下来，创建一个头文件来声明 DLL 导出的函数，然后将函数定义添加到 DLL，使其具备更强大的功能。

::: moniker-end

### <a name="to-add-a-header-file-to-the-dll"></a>将头文件添加到 DLL

1. 若要为函数创建头文件，请在菜单栏上选择“项目” > “添加新项”。

1. 在“添加新项”对话框的左窗格中，选择“Visual C++”。 在中间窗格中，选择 **“头文件(.h)”**。 指定 `MathLibrary.h` 作为头文件的名称。

   ![在“添加新项”对话框中添加标头](media/mathlibrary-add-new-item-header-file.png "在“添加新项”对话框中添加头文件")

1. 选择“添加”按钮以生成一个空白头文件，该文件显示在新的编辑器窗口中。

   ![在编辑器中清空 MathLibrary.h 文件](media/edit-empty-mathlibrary-header.png "在编辑器中清空 MathLibrary.h 文件")

1. 将头文件的内容替换为以下代码：

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

此头文件声明一些函数以生成通用 Fibonacci 序列，给定了两个初始值。 调用 `fibonacci_init(1, 1)` 会生成熟悉的 Fibonacci 数字序列。

请注意文件顶部的预处理器语句。 默认情况下，DLL 的“新建项目”模板会将 \<em>PROJECTNAME\</em>&#95;EXPORTS 添加到 DLL 项目的已定义预处理器宏中。 在此示例中，Visual Studio 在生成 MathLibrary DLL 项目时定义 MATHLIBRARY&#95;EXPORTS。 

::: moniker range="=vs-2017"

（Visual Studio 2017 版本 15.3 中的向导不会强制此符号定义为大写形式。 如果将项目命名为“MathLibrary”，则定义的符号是 MathLibrary&#95;EXPORTS 而不是 MATHLIBRARY&#95;EXPORTS。 这就是为什么前文中使用额外的步骤来添加此符号。）

::: moniker-end

定义 MATHLIBRARY&#95;EXPORTS 宏时，MATHLIBRARY&#95;API 宏会对函数声明设置 `__declspec(dllexport)` 修饰符。 此修饰符指示编译器和链接器从 DLL 导出函数或变量，以便其他应用程序可以使用它。 如果未定义 MATHLIBRARY&#95;EXPORTS（例如，当客户端应用程序包含头文件时），MATHLIBRARY&#95;API 会将 `__declspec(dllimport)` 修饰符应用于声明。 此修饰符可优化应用程序中函数或变量的导入。 有关详细信息，请参阅 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。

### <a name="to-add-an-implementation-to-the-dll"></a>向 DLL 添加实现

::: moniker range="vs-2019"

1. 在“解决方案资源管理器”中，右键单击“源文件”节点，并添加一个名为 `MathLibrary.cpp` 的新 .cpp 文件，其方式与上一步中添加新头文件的方式相同。

::: moniker-end

1. 在编辑器窗口中，选择 MathLibrary.cpp 的选项卡（如果已打开）。 如果未打开，请在“解决方案资源管理器”中，打开 MathLibrary 项目的“源文件”文件夹中的 MathLibrary.cpp。

1. 在编辑器中，将 MathLibrary.cpp 文件的内容替换为以下代码：

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019
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

若要验证到目前为止是否一切正常，请编译动态链接库。 若要编译，请在菜单栏上选择“生成” > “生成解决方案”。 输出应该类似于以下内容：

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

祝贺你，你已使用 Visual C++ 创建了一个 DLL！ 接下来，将创建一个使用 DLL 导出的函数的客户端应用。

## <a name="create-a-client-app-that-uses-the-dll"></a>创建可使用 DLL 的客户端应用

创建 DLL 时，必须考虑如何使用 DLL。 若要编译可调用 DLL 导出的函数的代码，声明必须包含在客户端源代码中。 在链接时，当解析对 DLL 函数的这些调用时，链接器必须具有导入库，这是一个特殊的库文件，其中包含有关如何查找函数的 Windows 信息，而不是实际代码。 而在运行时，DLL 必须可供客户端使用，位于操作系统可以找到的位置。

若要使用 DLL，无论是自己的还是第三方 DLL，客户端应用都必须找到声明 DLL 导出的标头、链接器的导入库以及 DLL 本身。 一种方法是将所有这些文件复制到客户端项目中。 对于在客户端处于开发阶段时不太可能更改的第三方 DLL，此方法可能是使用它们的最佳方法。 但是，如果还要同时生成 DLL，最好避免重复。 如果复制正在开发的 DLL 文件，可能会意外更改一个副本而不是另一个中的头文件，或使用过期的库。 为避免此问题，建议在客户端项目中设置包含路径以包括 DLL 项目中的 DLL 头文件。 此外，在客户端项目中设置库路径以包括 DLL 项目中的 DLL 导入库。 最后，将生成的 DLL 从 DLL 项目复制到生成输出目录中。 此步骤允许客户端应用使用生成的同一 DLL 代码。

::: moniker range="vs-2019"

### <a name="to-create-a-client-app-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建客户端应用

1. 在菜单栏上，选择“文件”>“新建”>“项目”，打开“创建新项目”对话框。

1. 在对话框顶部，将“语言”设置为“C++”，将“平台”设置为“Windows”，并将“项目类型”设置为“控制台”。 

1. 从筛选的项目类型列表中，选择“控制台应用”，然后选择“下一步”。 在下一页中的“名称”框内输入 `MathClient` 以指定项目的名称，并根据需要指定项目位置。

   ![为客户端项目命名](media/mathclient-project-name-2019.png "为客户端项目命名")

1. 选择“创建”按钮创建客户端项目。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>在 Visual Studio 2017 中创建客户端应用

1. 若要创建使用创建的 DLL 的 C++ 应用，在菜单栏上，选择“文件”>“新建”>“项目”。

1. 在“新建项目”对话框的左窗格中，选择“已安装” > “Visual C++”下的“Windows 桌面”。 在中心窗格中，选择“Windows 桌面向导”。 在“名称”编辑框中指定项目的名称 `MathClient`。

   ![为客户端项目命名](media/mathclient-new-project-name-153.png "为客户端项目命名")

1. 选择“确定”以启动“Windows 桌面项目”向导。 在向导中，选择“确定”以创建客户端应用项目。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>在较旧版本的 Visual Studio 2017 中创建客户端应用

1. 若要创建使用创建的 DLL 的 C++ 应用，在菜单栏上，选择“文件”>“新建”>“项目”。

1. 在“新建项目”对话框的左窗格中，选择“已安装” > “模板” > “Visual C++”下的“Win32”。 在中间窗格中，选择 **“Win32 控制台应用程序”**。 在“名称”编辑框中指定项目的名称 `MathClient`。

   ![为客户端项目命名](media/mathclient-project-name.png "为客户端项目命名")

1. 选择“确定”按钮以关闭“新建项目”对话框并启动“Win32 应用程序向导”。 在 **“Win32 应用程序向导”** 对话框的 **“概述”** 页上，选择 **“下一步”** 按钮。

1. 在“应用程序设置”页的“应用程序类型”下，选择“控制台应用程序”（如果尚未选择）。

1. 选择 **“完成”** 按钮创建项目。

::: moniker-end

向导完成后，将为你创建一个最小的控制台应用程序项目。 主源文件的名称与你之前输入的项目名称相同。 在本例中，命名为 MathClient.cpp。 可以生成它，但它还不会使用你的 DLL。

接下来，要在源代码中调用 MathLibrary 函数，你的项目必须包括 MathLibrary.h 文件。 可以将此头文件复制到客户端应用项目中，然后将其作为现有项添加到项目中。 对于第三方库，此方法可能是一个不错的选择。 但是，如果与客户端同时处理 DLL 的代码，可能会导致一个头文件中的更改未在另一个头文件中显示。 若要避免此问题，可以更改项目中的“附加包含目录”路径以包含指向原始标头的路径。

### <a name="to-add-the-dll-header-to-your-include-path"></a>将 DLL 标头添加到包含路径

1. 右键单击“解决方案资源管理器”中的“MathClient”节点以打开“属性页”对话框。

1. 在“配置”下拉框中，选择“所有配置”（如果尚未选择）。

1. 在左窗格中，选择“配置属性” > “C/C++”下的“常规”。

1. 在属性窗格中，选择“附加包含目录”编辑框旁的下拉控件，然后选择“编辑”。

   ![编辑“附加包含目录”属性](media/mathclient-additional-include-directories-property.png "编辑“附加包含目录”属性")

1. 在“附加包含目录”对话框的顶部窗格中双击以启用编辑控件。

1. 在编辑控件中，指定指向 MathLibrary.h 头文件的位置的路径。 在这种情况下，可以使用从包含客户端项目中的 .cpp 文件的文件夹到 DLL 项目中包含 .h 文件的文件夹的相对路径。 如果客户端项目位于与 DLL 解决方案相同的文件夹中的单独解决方案中，则相对路径应如下所示：

   `..\..\MathLibrary\MathLibrary`

   如果 DLL 和客户端项目位于同一解决方案中，或者解决方案位于不同的文件夹中，则必须相应地调整相对路径。

   ![将标头位置添加到“附加包含目录”属性](media/mathclient-additional-include-directories.png "将标头位置添加到“附加包含目录”属性")

1. 在“附加包含目录”对话框中输入指向头文件的路径后，选择“确定”按钮返回到“属性页”对话框，然后选择“确定”按钮以保存更改。

现在可以包括 MathLibrary.h 文件，并使用它在客户端应用程序中声明的函数。 使用以下代码替换 MathClient.cpp 的内容：

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
// #include "pch.h" Uncomment for Visual Studio 2017 and earlier
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

可以编译此代码，但无法链接它，因为链接器尚且无法找到生成应用所需的导入库。 链接器必须找到 MathLibrary.lib 文件才能成功链接。 通过设置“附加依赖项”属性将 MathLibrary.lib 文件添加到生成中。 同样，可以将库文件复制到客户端应用项目中，但如果库和客户端应用都处于开发过程中，则可能会导致一个副本中的更改未在另一个副本中显示。 若要避免此问题，可更改项目中的“附加库目录”路径以在链接时包含指向原始库的路径。

### <a name="to-add-the-dll-import-library-to-your-project"></a>将 DLL 导入库添加到项目中

1. 右键单击“解决方案资源管理器”中的“MathClient”节点以打开“属性页”对话框。

1. 在“配置”下拉框中，选择“所有配置”（如果尚未选择）。 此设置可确保为“调试”和“发布”版本均设置路径。

1. 在左窗格中，选择“配置属性” > “链接器”下的“输入”。 在属性窗格中，选择“附加依赖项”编辑框旁的下拉控件，然后选择“编辑”。

   ![编辑“附加依赖项”属性](media/mathclient-additional-dependencies-property.png "编辑“附加依赖项”属性")

1. 在“附加依赖项”对话框中，将 `MathLibrary.lib` 添加到顶部编辑控件的列表中。

   ![添加库依赖项](media/mathclient-additional-dependencies.png "添加库依赖项")

1. 选择“确定”返回到“属性页”对话框。

1. 在左窗格中，选择“配置属性” > “链接器”下的“常规”。 在属性窗格中，选择“附加库目录”编辑框旁的下拉控件，然后选择“编辑”。

   ![编辑“附加库目录”属性](media/mathclient-additional-library-directories-property.png "编辑“附加库目录”属性")

1. 在“附加库目录”对话框的顶部窗格中双击以启用编辑控件。 在编辑控件中，指定指向 MathLibrary.lib 文件位置的路径。 输入此值可使用同时适用于“调试”和“发布”版本的宏：

   `..\..\MathLibrary\$(IntDir)`

   ![添加库目录](media/mathclient-additional-library-directories.png "添加库目录")

1. 在“附加库目录”对话框中输入指向库文件的路径后，选择“确定”按钮返回到“属性页”对话框。

客户端应用现在可以成功编译和链接，但它仍未具备运行所需的全部条件。 当操作系统加载应用时，它会查找 MathLibrary DLL。 如果在某些系统目录、环境路径或本地应用目录中找不到 DLL，则加载会失败。 避免此问题的一种方法是将 DLL 复制到包含客户端可执行文件的目录中，作为生成过程的一部分。 若要复制 DLL，可以将“生成后事件”添加到项目中，以便添加将 DLL 复制到生成输出目录的命令。 此处指定的命令仅在 DLL 丢失或已更改时才复制 DLL，并使用宏在配置的正确“调试”或“发布”位置之间进行复制。

### <a name="to-copy-the-dll-in-a-post-build-event"></a>在生成后事件中复制 DLL

1. 右键单击“解决方案资源管理器”中的“MathClient”节点以打开“属性页”对话框。

1. 在“配置”下拉框中，选择“所有配置”（如果尚未选择）。

1. 在左窗格中，选择“配置属性” > “生成事件”下的“生成后事件”。

1. 在属性窗格中，在“命令行”字段中选择编辑控件，然后输入以下命令：

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![添加生成后命令](media/mathclient-post-build-command-line.png "添加生成后命令")

1. 选择“确定”按钮以保存对项目属性所做的更改。

现在，客户端应用具备生成和运行所需的全部条件。 通过在菜单栏上选择“生成” > “生成解决方案”来生成应用程序。 Visual Studio 中的“输出”窗口应显示如下内容：

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

祝贺你，你已创建一个可调用 DLL 中的函数的应用程序。 现在运行应用程序以查看它执行的操作。 在菜单栏上，选择“调试” > “启动而不调试”。 此时，Visual Studio 会打开一个命令窗口，供程序在其中运行。 输出的最后一部分应如下所示：

![启动客户端应用而不调试](media/mathclient-run-without-debugging.png "启动客户端应用而不调试")

按任意键关闭命令窗口。

现在，你已创建一个 DLL 和一个客户端应用程序，可以进行试验。 尝试在客户端应用的代码中设置断点，并在调试器中运行该应用。 看看单步执行库调用时会发生什么情况。 将其他函数添加到库中，或编写另一个使用 DLL 的客户端应用。

部署应用时，还必须部署它使用的 DLL。 若要通过最简单的方法使生成的或从第三方加入的 DLL 可用于应用，可将其放在应用所在的同一目录中，也称为“应用本地部署”。 有关部署的更多信息，请参阅 [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md)。

## <a name="see-also"></a>请参阅

[从 Visual Basic 应用程序调用 DLL 函数](calling-dll-functions-from-visual-basic-applications.md)
