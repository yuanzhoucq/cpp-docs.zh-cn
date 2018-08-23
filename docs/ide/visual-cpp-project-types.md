---
title: Visual C++ 项目类型 | Microsoft Docs
ms.custom: ''
ms.date: 10/30/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80ac3479338dcb7f6be9e7e5f3f150cc8e15a9a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339977"
---
# <a name="visual-c-project-types"></a>Visual C++ 项目类型

可以使用项目模板来创建基本程序结构、菜单、工具栏、图标、引用以及适合要创建的项目类型的 `#include` 语句。 Visual Studio 包括多种类型的 Visual C++ 项目模板并为其中许多项目模板提供了向导，以便可以在创建项目时对其进行自定义。 在创建项目之后，可以立即生成它并运行应用程序；在开发应用程序时最好间歇性生成该项目。

不必使用模板来创建项目，但在大多数情况下这样做会更为高效，因为修改提供的项目文件和结构比从头创建它们更为简单。  
  
> [!NOTE]
> 你可以使用 C++ 项目模板来创建 C 语言项目。 在生成的项目中，找到文件扩展名为 .cpp 的文件并将它更改为 .c。 然后，在该项目（而非解决方案）的“项目属性”  页上，依次展开“配置属性” 和“C/C++”  ，然后选择“高级” 。 将“编译为”  设置更改为“编译为 C 代码 (/TC)” 。

## <a name="project-templates"></a>项目模板

Visual Studio 中包含的项目模板取决于安装的产品版本和工作负载。 如果安装的是具有 C++ 工作负载的桌面开发，则 Visual Studio 具有这些 Visual C++ 项目模板。

### <a name="windows-desktop"></a>Windows 桌面

|项目模板|描述|  
|----------------------|-----------------------------| 
|[Windows 控制台应用程序](../windows/creating-a-console-application.md)|用于创建 Windows 控制台应用程序的项目。|
|[Windows 桌面应用程序](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|用于创建 Windows 桌面 (Win32) 应用程序的项目。|
|[动态链接库](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|用于创建动态链接库 (DLL) 的项目。|
|[静态库](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|用于创建静态库 (LIB) 的项目。|
|Windows 桌面向导|用于通过其他选项创建 Windows 桌面应用程序和库的向导。|

### <a name="general"></a>常规

|项目模板|描述|
|----------------------|-----------------------------|
|空项目|用于创建应用程序、库和 DLL 的空项目。 必须添加任何必需的代码或资源。|
|[生成文件项目](../ide/creating-a-makefile-project.md)|用于使用外部生成系统的项目。|
|“共享项”项目|用于在多个项目之间共享文件的项目。|

### <a name="atl"></a>ATL

|项目模板|描述|
|----------------------|-----------------------------|
|[ATL 项目](../atl/reference/creating-an-atl-project.md)|使用活动模板库的项目。|

### <a name="test"></a>测试

|项目模板|描述|
|----------------------|-----------------------------|
|[本机单元测试项目](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|其中包含本机 C++ 单元测试的项目。|

### <a name="mfc"></a>MFC

如果将 MFC 和 ATL 支持组件添加到 Visual Studio 安装，则这些项目模板将添加到 Visual Studio。

|项目模板|描述|
|----------------------|-----------------------------|
|[MFC 应用程序](../mfc/reference/creating-an-mfc-application.md)|用于创建使用 Microsoft 基础类 (MFC) 库的应用程序的项目。|
|[MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)|用于创建使用 MFC 库的 ActiveX 控件的项目。|
|[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md)|用于创建使用 MFC 库的动态链接库的项目。|

### <a name="windows-universal-apps"></a>Windows 通用应用

如果将 C++ Windows 通用平台工具组件添加到 Visual Studio 安装，则这些项目模板将添加到 Visual Studio。

有关 C++ 中 Windows 通用应用的概述，请参阅[通用 Windows 应用 (C++)](../windows/universal-windows-apps-cpp.md)。

|项目模板|描述|
|----------------------|-----------------------------|
|空白应用程序|用于没有预定义控件或布局的单页通用 Windows 平台 (UWP) 应用的项目。|
|DirectX 11 应用|用于使用 DirectX 11 的通用 Windows 平台应用的项目。|
|DirectX 12 应用|用于使用 DirectX 12 的通用 Windows 平台应用的项目。|
|DirectX 11 和 XAML 应用|用于使用 DirectX 11 和 XAML 的通用 Windows 平台应用的项目。|
|单元测试应用|用于为通用 Windows 平台 (UWP) 应用创建单元测试应用的项目。|
|DLL|用于可由通用 Windows 平台应用或运行时组件使用的本机动态链接库 (DLL) 的项目。|
|静态库|用于可由通用 Windows 平台应用或运行时组件使用的本机静态链接库 (LIB) 的项目。|
|Windows 运行时组件|用于可由通用 Windows 平台应用使用的 Windows 运行时组件的项目，与编写应用所用的编程语言无关。|
|Windows 应用程序打包项目|用于创建 UWP 包的项目，该 UWP 包可使桌面应用程序进行侧加载或通过 Microsoft Store 进行分发。|

## <a name="todo-comments"></a>TODO 注释

许多由项目模板生成的文件都包含 TODO 注释，这些注释可帮助你标识提供自己的源代码的位置。 有关如何添加代码的详细信息，请参阅[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)和[使用资源文件](../windows/working-with-resource-files.md)。

## <a name="see-also"></a>请参阅

[使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
