---
title: Windows 桌面向导
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: a434a329febc38d6a46881dcabba6b05a402fbca
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708057"
---
# <a name="windows-desktop-wizard"></a>Windows 桌面向导

Windows 桌面向导取代 Win32 应用程序向导中，在 Visual Studio 2017 及更高版本。 该向导允许您创建的四种类型的任何C++项目 （在下表中的标题列出）。 在每种情况下，你都可以指定适合于打开项目类型的其他选项。 

   ![Windows 桌面向导](media/windows-desktop-wizard.png)

下表指示了每个应用程序类型可用的选项。

|支持级别|控制台应用程序|可执行 (Windows) 应用程序|动态链接库|静态库|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**空项目**|是|是|是|否|
|**导出符号**|否|否|是|否|
|**预编译头**|否|否|否|是|
|**ATL 支持**|是|否|否|否|
|**MFC 支持**|是|否|否|是|

## <a name="overview"></a>概述

此向导页描述你正在创建的 Win32 应用程序的当前项目设置。 默认设置了以下选项：

- 该项目是 Windows 应用程序。

- 该项目不为空。

- 该项目不包含导出符号。

- 该项目不使用预编译的头文件（此选项仅适用于静态库项目）。

- 该项目不包含对 MFC 和 ATL 的支持。

## <a name="application-type"></a>应用程序类型

创建指定的应用程序类型。

|选项|描述|
|------------|-----------------|
|**控制台应用程序**|创建控制台应用程序。 控制台程序开发与[控制台函数](https://msdn.microsoft.com/library/ms813137.aspx)，它提供的信息在控制台窗口中的字符模式支持。 视觉对象C++[运行时库](../c-runtime-library/c-run-time-library-reference.md)还提供输出和输入从控制台窗口与标准 I/O 函数，如`printf_s()`并`scanf_s()`。 控制台应用程序没有图形用户界面。 它将编译为.exe 文件，并可作为独立的应用程序从命令行运行。<br /><br /> 您可以将 MFC 和 ATL 支持添加到控制台应用程序。|
|**Windows 应用程序**|创建 Win32 程序。 Win32 程序是用 C 编写的应用可执行程序 (EXE) 或C++，使用对 Win32 API 的调用创建的图形用户界面。<br /><br /> 不能添加 MFC 或 ATL 支持添加到 Windows 应用程序。|
|**动态链接库**|创建 Win32 动态链接库 (DLL)。 Win32 DLL 是用 C 编写的二进制文件或C++，使用调用 Win32 API，而不是 MFC 类，以及作为共享库的多个应用程序可同时使用的函数中。<br /><br /> 无法将 MFC 或 ATL 支持添加到使用此向导中，创建一个 DLL 应用程序，但您可以创建非 MFC DLL 通过选择**新建 > 项目 > MFC DLL**。|
|**静态库**|创建静态库。 静态库是一个包含对象及其函数和生成可执行文件时链接到你的程序的数据文件。 本主题说明如何创建的初学者文件和[项目属性](../build/reference/property-pages-visual-cpp.md)静态库。 静态库文件提供以下优势：<br /><br />-A Win32 静态库是如果您正在使用的应用程序执行调用 Win32 API，而不是 MFC 类很有用。<br />-链接的过程是相同的以 C 编写的 Windows 应用程序其余部分还是在C++。<br />-你可以将静态库链接到一个基于 MFC 的程序或非 MFC 程序。|

## <a name="additional-options"></a>附加选项

定义支持和应用程序，具体取决于其类型的选项。

|选项|描述|
|------------|-----------------|
|**空项目**|指定项目文件为空。 如果你有一组源代码文件 （如.cpp 文件、 头文件、 图标、 工具栏、 对话框等） 并想要在视觉对象中创建一个项目C++开发环境中，您必须首先创建一个空白项目，然后将文件添加到项目。<br /><br /> 选择此选项将不可用的静态库项目。|
|**导出符号**|指定 DLL 项目导出的符号。|
|**预编译头**|指定静态库项目使用预编译标头。|
|**安全开发生命周期 (SDL) 检查**|有关 SDL 的详细信息，请参阅[Microsoft 安全开发生命周期 (SDL) 过程指南](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>添加常用标头为：

添加一个视觉对象中提供的库支持C++。

|选项|描述|
|------------|-----------------|
|**ATL**|将嵌入到类中活动模板库 (ATL) 中的项目支持。 Win32 控制台仅限于应用程序。<br /><br /> **请注意**此选项并不表示对使用 ATL 的 ATL 对象代码向导添加的支持。 可以仅向 ATL 项目添加 ATL 对象或 MFC 与 ATL 项目支持。|
|**MFC**|构建到 Microsoft 基础类 (MFC) 库的项目支持。 Win32 控制台应用程序和仅限静态库。|

## <a name="remarks"></a>备注

创建 Windows 桌面应用程序后，即可使用 [泛型](../ide/generic-cpp-class-wizard.md) 代码向导添加泛型 C++ 类。 可以添加其他项，例如 HTML 文件、头文件、资源或文本文件。

> [!NOTE]
> 不能添加 ATL 类，只能向支持 MFC 的 Windows 桌面应用程序类型添加 MFC 类（请参阅上表）。

可在 **解决方案资源管理器**中查看你通过向导为项目创建的文件。 向导将创建为你的项目文件的详细信息，请参阅项目生成的文件， `ReadMe.txt`。 有关详细信息的文件类型，[用于 Visual Studio 创建的文件类型C++项目](../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>请参阅

[C++在 Visual Studio 中的项目类型](../build/reference/visual-cpp-project-types.md)