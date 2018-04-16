---
title: "Visual c + + 项目类型 |Microsoft 文档"
ms.custom: 
ms.date: 10/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- Visual C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a837aa04b0e0c2b8d3d9f5cfd48181a9ea23b346
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="visual-c-project-types"></a>Visual C++ 项目类型

可以使用项目模板来创建基本程序结构、菜单、工具栏、图标、引用以及适合要创建的项目类型的 `#include` 语句。 Visual Studio 包括多种类型的 Visual C++ 项目模板并为其中许多项目模板提供了向导，以便可以在创建项目时对其进行自定义。 立即创建一个项目后，你可以生成它并运行该应用程序;很好的做法间歇性生成，当你开发你的应用程序。

不必使用模板来创建项目，但在大多数情况下这样做会更为高效，因为修改提供的项目文件和结构比从头创建它们更为简单。  
  
> [!NOTE]
> 你可以使用 C++ 项目模板来创建 C 语言项目。 在生成的项目中，找到文件扩展名为 .cpp 的文件并将它更改为 .c。 然后，在该项目（而非解决方案）的“项目属性”  页上，依次展开“配置属性” 和“C/C++”  ，然后选择“高级” 。 将“编译为”  设置更改为“编译为 C 代码 (/TC)” 。

## <a name="project-templates"></a>项目模板

Visual Studio 中包含的项目模板依赖于的产品版本和已安装的工作负荷。 如果使用 c + + 工作负荷，已安装桌面开发，Visual Studio 将具有这些 Visual c + + 项目模板。

### <a name="windows-desktop"></a>Windows 桌面

|项目模板|描述|  
|----------------------|-----------------------------| 
|[Windows 控制台应用程序](../windows/creating-a-console-application.md)|用于创建一个 Windows 控制台应用程序的项目。|
|[Windows 桌面应用程序](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|用于创建 Windows 桌面 (Win32) 应用程序的项目。|
|[动态链接库](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|用于创建动态链接库 (DLL) 项目。|
|[静态库](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|用于创建静态库 (LIB) 的项目。|
|Windows 桌面向导|用于创建具有其他选项的 Windows 桌面应用程序和库向导。|

### <a name="general"></a>常规

|项目模板|描述|
|----------------------|-----------------------------|
|空项目|用于创建应用程序、 库或 DLL 的空项目。 你必须添加任何代码或所需的资源。|
|[生成文件项目](../ide/creating-a-makefile-project.md)|使用外部的项目生成系统。|
|共享项项目|一个用于多个项目之间共享文件的项目。|

### <a name="atl"></a>ATL

|项目模板|描述|
|----------------------|-----------------------------|
|[ATL 项目](../atl/reference/creating-an-atl-project.md)|使用 Active Template Library 的项目。|

### <a name="test"></a>测试

|项目模板|描述|
|----------------------|-----------------------------|
|[本机单元测试项目](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|包含本机 c + + 单元测试项目。|

### <a name="mfc"></a>MFC

如果你添加的 MFC 和 ATL 支持到你的 Visual Studio 安装的组件，这些项目模板将添加到 Visual Studio 中。

|项目模板|描述|
|----------------------|-----------------------------|
|[MFC 应用程序](../mfc/reference/creating-an-mfc-application.md)|用于创建使用 Microsoft 基础类 (MFC) 库的应用程序的项目。|
|[MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)|用于创建 ActiveX 控件使用 MFC 库的项目。|
|[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md)|用于创建动态链接库的项目使用 MFC 库。|

### <a name="windows-universal-apps"></a>Windows 通用应用

如果将 c + + Windows 通用平台工具组件添加到你的 Visual Studio 安装中时，这些项目模板将添加到 Visual Studio 中。

C + + 中的通用 Windows 应用的概述，请参阅[通用 Windows 应用 （c + +）](../windows/universal-windows-apps-cpp.md)。

|项目模板|描述|
|----------------------|-----------------------------|
|空白应用程序|没有预定义的控件或布局的单页通用 Windows 平台 (UWP) 应用的项目。|
|DirectX 11 应用|使用 DirectX 11 的通用 Windows 平台应用项目。|
|DirectX 12 应用|使用 DirectX 12 的通用 Windows 平台应用项目。|
|DirectX 11 和 XAML 的应用程序|使用 DirectX 11 和 XAML 的通用 Windows 平台应用项目。|
|单元测试应用|要创建通用 Windows 平台 (UWP) 应用的单元测试应用的项目。|
|DLL|通用 Windows 平台应用程序或运行时组件可以使用的本机动态链接库 (DLL) 项目。|
|静态库|通用 Windows 平台应用程序或运行时组件可以使用本机静态链接库 (LIB) 的项目。|
|Windows 运行时组件|通用 Windows 平台应用，而不考虑编程语言编写应用程序可以使用的 Windows 运行时组件项目。|
|Windows 应用程序打包项目|创建 UWP 包的项目使桌面应用程序端加载或分布式通过 Microsoft 应用商店。|

## <a name="todo-comments"></a>TODO 注释

许多由项目模板生成的文件都包含 TODO 注释，这些注释可帮助你标识提供自己的源代码的位置。 有关如何添加代码的详细信息，请参阅[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)和[使用资源文件](../windows/working-with-resource-files.md)。

## <a name="see-also"></a>请参阅

[使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
