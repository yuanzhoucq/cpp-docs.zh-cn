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
ms.openlocfilehash: 3d8be0cc33e0435bc5a18191303dbbc91277de0b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075454"
---
# <a name="windows-desktop-wizard"></a>Windows 桌面向导

Windows 桌面向导替换 Visual Studio 2017 和更高版本中的 Win32 应用程序向导。 通过该向导，您可以创建四种类型的C++项目中的任意一种（在下表的标题中列出）。 在每种情况下，你都可以指定适合于打开项目类型的其他选项。

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

|选项|说明|
|------------|-----------------|
|**控制台应用程序**|创建控制台应用程序。 Visual C++ [运行库](../c-runtime-library/c-run-time-library-reference.md)还通过标准 i/o 函数（如 `printf_s()` 和 `scanf_s()`）提供控制台窗口的输出和输入。 控制台应用程序没有图形用户界面。 它编译到 .exe 文件中，并可从命令行作为独立的应用程序运行。<br /><br /> 您可以向控制台应用程序添加 MFC 和 ATL 支持。|
|**Windows 应用程序**|创建 Win32 程序。 Win32 程序是用 C 或C++编写的可执行应用程序（EXE），使用对 Win32 API 的调用来创建图形用户界面。<br /><br /> 不能将 MFC 或 ATL 支持添加到 Windows 应用程序。|
|**动态链接库**|创建 Win32 动态链接库（DLL）。 Win32 DLL 是用 C 或C++编写的二进制文件，它使用对 Win32 API 而不是 MFC 类的调用，并充当可由多个应用程序同时使用的共享函数库。<br /><br /> 不能将 MFC 或 ATL 支持添加到使用此向导创建的 DLL 应用程序，但可以通过选择 "新建" " **> 项目" > MFC dll**创建 mfc dll。|
|**静态库**|创建静态库。 静态库是一个文件，其中包含在生成可执行文件时链接到程序的对象及其函数和数据。 本主题说明如何创建静态库的 starter 文件和[项目属性](../build/reference/property-pages-visual-cpp.md)。 静态库文件具有以下优点：<br /><br />-如果正在处理的应用程序调用 Win32 API 而不是 MFC 类，则 Win32 静态库很有用。<br />-无论 Windows 应用程序的其余部分是用 C 还是编写的，链接过程都是相同C++的。<br />-可以将静态库链接到基于 MFC 的程序或非 MFC 程序。|

## <a name="additional-options"></a>附加选项

根据应用程序的类型定义该应用程序的支持和选项。

|选项|说明|
|------------|-----------------|
|**空项目**|指定项目文件为空白。 如果你有一组源代码文件（如 .cpp 文件、头文件、图标、工具栏、对话框等），并且想要在视觉C++开发环境中创建一个项目，则必须先创建一个空项目，然后将这些文件添加到项目。<br /><br /> 此选择不适用于静态库项目。|
|**导出符号**|指定 DLL 项目导出符号。|
|**预编译头**|指定静态库项目使用预编译标头。|
|**安全开发生命周期（SDL）检查**|有关 SDL 的详细信息，请参阅[Microsoft 安全开发生命周期 (SDL) 过程指南](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>为以下内容添加常用标头：

添加对视觉对象C++中提供的某个库的支持。

|选项|说明|
|------------|-----------------|
|**ATL**|为活动模板库（ATL）中的类生成项目支持。 仅适用于 Win32 控制台应用程序。<br /><br /> **注意**此选项不指示支持使用 ATL 代码向导添加 ATL 对象。 只能将 ATL 对象添加到 atl 项目或具有 ATL 支持的 MFC 项目。|
|**MFC**|为 Microsoft 基础类（MFC）库提供项目支持。 仅适用于 Win32 控制台应用程序和静态库。|

## <a name="remarks"></a>备注

创建 Windows 桌面应用程序后，即可使用 [泛型](../ide/generic-cpp-class-wizard.md) 代码向导添加泛型 C++ 类。 可以添加其他项，例如 HTML 文件、头文件、资源或文本文件。

> [!NOTE]
> 不能添加 ATL 类，只能向支持 MFC 的 Windows 桌面应用程序类型添加 MFC 类（请参阅上表）。

可在 **解决方案资源管理器**中查看你通过向导为项目创建的文件。 有关向导为项目创建的文件的详细信息，请参阅项目生成的文件 `ReadMe.txt`。 有关文件类型的详细信息，请查看[为 Visual Studio C++项目创建的文件类型](../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另请参阅

[Visual Studio 中的 C++ 项目类型](../build/reference/visual-cpp-project-types.md)