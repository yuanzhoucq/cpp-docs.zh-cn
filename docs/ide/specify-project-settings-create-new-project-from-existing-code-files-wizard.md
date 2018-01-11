---
title: "指定项目设置，从现有代码文件向导创建新项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.importwiz.appsettings
dev_langs: C++
helpviewer_keywords: Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2cf1e8eba11063f7f2e46f836cd2ef84cc70dfe8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>“从现有代码文件创建新项目”向导 ->“指定项目设置”
从现有代码文件创建新项目向导的此页用于指定：  
  
-   新项目的生成环境  
  
-   生成设置以匹配特定类型的新项目以生成  
  
## <a name="task-list"></a>任务列表  
 [如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 列表  
 **使用 Visual Studio**  
 指定要使用了包含在 Visual Studio 中生成新项目的生成工具。 默认情况下选择此选项。  
  
 **项目类型**  
 指定此向导将生成的项目的类型。  
  
 **Windows 应用程序项目**  
 指示此向导将生成可执行文件的 Windows 应用程序的项目。 此选项才可用从**项目类型**下拉列表框。  
  
 **控制台应用程序项目**  
 指示此向导将生成一个控制台应用程序的项目。 此选项才可用从**项目类型**下拉列表框。  
  
 **动态链接的库 (DLL) 项目**  
 指示此向导将生成空的动态链接库应用程序的项目。 此选项才可用从**项目类型**下拉列表框。  
  
 **静态库 (LIB) 项目**  
 指示此向导将生成为静态库应用程序项目。 此选项才可用从**项目类型**下拉列表框。  
  
 **添加 ATL 支持**  
 为新项目添加 ATL 支持。  
  
 **添加 mfc 支持**  
 将 MFC 支持添加到新项目。  
  
 **添加对公共语言运行时的支持**  
 添加 CLR 编程到新项目的支持。  
  
 **公共语言运行时**  
 指定要符合 CLR 功能的新项目。  
  
 **公共语言运行时 （旧语法）**  
 指定要符合有关 c + + 语法，这是在 Visual c + + 2005年之前的 CLR 编程语法的托管扩展的新项目。  
  
 **使用外部生成系统**  
 指定要使用了不包含在 Visual Studio 中生成新项目的生成工具。 选中此选项后，你可以指定生成命令行上**指定调试配置设置**和**指定发布配置设置**页。  
  
> [!NOTE]
>  当**使用外部生成系统**选项已选中，则 IDE 不会生成新项目中，因此 /D，/ 我、 /FI、 /AI 或 /FU 选项不需要的编译。 但是，这些选项必须正确设置使 IntelliSense 正常工作。  
  
## <a name="see-also"></a>请参阅  
 [指定调试配置设置、 从现有代码文件向导创建新项目](../ide/specify-debug-configuration-settings.md)   
 [指定发布配置设置，“从现有代码文件创建新项目”向导](../ide/specify-release-configuration.md)