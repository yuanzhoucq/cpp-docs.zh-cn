---
title: “NMake”属性页 (Windows C++)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
ms.openlocfilehash: c0dbe537635fe6698f814f3d8456f0caa9c8c796
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320599"
---
# <a name="nmake-property-page"></a>“NMake”属性页

借助“NMake”属性页，可以指定 NMake 项目的生成设置。 (NMAKE 是 Microsoft 的实现[使](https://wikipedia.org/wiki/Make_(software))。)

有关 NMake 项目的详细信息，请参阅[创建生成文件项目](creating-a-makefile-project.md)。 对于非 Windows 生成项目，请参阅[生成文件项目属性 (Linux C++)](../../linux/prop-pages/makefile-linux.md)，[常规项目属性 (AndroidC++生成文件)](/visualstudio/cross-platform/general-makefile-android-prop-page)或[NMake 属性 (AndroidC++)](/visualstudio/cross-platform/nmake-android-prop-page).

“NMake”属性页包含下列属性。

## <a name="uielement-list"></a>UIElement 列表

- **生成命令行**

   指定在“生成”菜单上单击“生成”时要运行的命令。

- **全部重新生成命令行**

   指定在“生成”菜单上单击“全部重新生成”时要运行的命令。

- **清除命令行**

   指定在“生成”菜单上单击“清除”时要运行的命令。

- **输出**

   指定将包含命令行输出的文件的名称。 默认情况下，此文件名称根据项目名称而定。

- **预处理器定义**

   指定源文件使用的任何预处理器定义。 默认值由当前平台和配置确定。

- **包含搜索路径**

   指定编译器将在其中搜索包含文件的目录。

- **强制包含**

   指定预处理器自动处理的文件，即使项目文件中未包含这些文件。

- **程序集搜索路径**

   指定 .NET Framework 尝试解析 .NET 程序集时将搜索的目录。

- **强制使用程序集**

   指定 .NET Framework 自动处理的程序集。

- **附加选项**

   指定在 IntelliSense C++ 分析文件时要使用的任何其他编译器开关。

有关如何访问信息**NMake**属性页中，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

有关如何以编程方式访问此对象的成员的信息，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>。

## <a name="see-also"></a>请参阅

[C++项目属性页引用](property-pages-visual-cpp.md)<br>
