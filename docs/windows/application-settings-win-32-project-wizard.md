---
title: Win 32 项目向导的应用程序设置
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.win32.appset
helpviewer_keywords:
- application settings [C++]
- Win32 Project Wizard, application settings
ms.assetid: d6b818f0-9b23-4793-a6c5-df1c8c594bad
ms.openlocfilehash: b9d9e8c0919429a961b4ef47507270534afacf75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592668"
---
# <a name="application-settings-win-32-project-wizard"></a>Win 32 项目向导的应用程序设置

使用向导的此页可以设置 Win32 项目的选项。

## <a name="application-type"></a>应用程序类型

创建指定的应用程序类型。

|选项|描述|
|------------|-----------------|
|**控制台应用程序**|创建控制台应用程序。 控制台程序开发与[控制台函数](https://msdn.microsoft.com/library/ms813137.aspx)，它提供的信息在控制台窗口中的字符模式支持。 Visual c + +[运行时库](../c-runtime-library/c-run-time-library-reference.md)还提供输出和输入从控制台窗口与标准 I/O 函数，如`printf_s()`和`scanf_s()`。 控制台应用程序没有图形用户界面。 它将编译为.exe 文件，并可作为独立的应用程序从命令行运行。<br /><br /> 您可以将 MFC 和 ATL 支持添加到控制台应用程序。|
|**Windows 应用程序**|创建 Win32 程序。 Win32 程序是可执行文件编写的应用程序 (EXE) 在 C 或 c + +，使用对 Win32 API 的调用创建的图形用户界面中。<br /><br /> 不能添加 MFC 或 ATL 支持添加到 Windows 应用程序。|
|**DLL**|创建 Win32 动态链接库 (DLL)。 Win32 DLL 是用 C 或 c + +，使用调用 Win32 API，而不是 MFC 类，以及作为共享库的多个应用程序可同时使用的函数中编写的二进制文件。<br /><br /> 不能添加 MFC 或 ATL 支持向 DLL 应用程序。 您可以指示 DLL 导出的符号。|
|**静态库**|创建静态库。 静态库是一个包含对象及其函数和生成可执行文件时链接到你的程序的数据文件。 本主题说明如何创建的初学者文件和[项目属性](../ide/property-pages-visual-cpp.md)静态库。 静态库文件提供以下优势：<br /><br />-A Win32 静态库是如果您正在使用的应用程序执行调用 Win32 API，而不是 MFC 类很有用。<br />-链接的过程是相同是否在 C 或 c + + 中编写 Windows 应用程序的其余部分。<br />-你可以将静态库链接到一个基于 MFC 的程序或非 MFC 程序。|

## <a name="additional-options"></a>附加选项

定义支持和应用程序，具体取决于其类型的选项。

|选项|描述|
|------------|-----------------|
|**空项目**|指定项目文件为空。 如果有一组源代码文件 （如.cpp 文件、 头文件、 图标、 工具栏、 对话框和等等），并且想要在 Visual c + + 开发环境中创建一个项目，您必须首先创建一个空白项目，然后将文件添加到项目。<br /><br /> 选择此选项将不可用的静态库项目。|
|**导出符号**|指定 DLL 项目导出的符号。|
|**预编译头**|指定静态库项目使用预编译标头。|
|安全开发生命周期 (SDL) 检查|有关 SDL 的详细信息，请参阅[Microsoft 安全开发生命周期 (SDL) 过程指南](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-support-for"></a>添加对的支持

添加一个 Visual c + + 中提供的库的支持。

|选项|描述|
|------------|-----------------|
|**ATL**|将嵌入到类中活动模板库 (ATL) 中的项目支持。 Win32 控制台仅限于应用程序。<br /><br /> **请注意**此选项并不表示对使用 ATL 的 ATL 对象代码向导添加的支持。 可以仅向 ATL 项目添加 ATL 对象或 MFC 与 ATL 项目支持。|
|**MFC**|构建到 Microsoft 基础类 (MFC) 库的项目支持。 Win32 控制台应用程序和仅限静态库。|

## <a name="see-also"></a>请参阅

[Win32 应用程序向导](../windows/win32-application-wizard.md)