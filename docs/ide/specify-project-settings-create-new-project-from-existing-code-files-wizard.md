---
title: “从现有代码文件创建新项目”向导 ->“指定项目设置”| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.appsettings
dev_langs:
- C++
helpviewer_keywords:
- Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0f59b802b5a24c1b449f78cccee4744538a5a0e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338941"
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>“从现有代码文件创建新项目”向导 ->“指定项目设置”
使用“从现有代码文件创建新项目文件”向导的此页指定：  
  
-   新项目的生成环境  
  
-   与要生成的特定类型的新项目匹配的生成设置  
  
## <a name="task-list"></a>任务列表  
 [如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 列表  
 **使用 Visual Studio**  
 指定使用 Visual Studio 包含的生成工具来生成新项目。 默认情况下选择此选项。  
  
 **项目类型**  
 指定向导生成的项目类型。  
  
 **Windows 应用程序项目**  
 指示向导将为可执行 Windows 应用程序生成项目。 可在“项目类型”下拉列表框中选择此选项。  
  
 **控制台应用程序项目**  
 指示向导将为控制台应用程序生成项目。 可在“项目类型”下拉列表框中选择此选项。  
  
 **动态链接库 (DLL) 项目**  
 指示向导将为空动态链接库应用程序生成项目。 可在“项目类型”下拉列表框中选择此选项。  
  
 **静态库 (LIB) 项目**  
 指示向导将为静态库应用程序生成项目。 可在“项目类型”下拉列表框中选择此选项。  
  
 **添加对 ATL 的支持**  
 为新项目添加 ATL 支持。  
  
 **添加对 MFC 的支持**  
 为新项目添加 MFC 支持。  
  
 **添加对公共语言运行时的支持**  
 为新项目添加 CLR 编程支持。  
  
 **公共语言运行时**  
 指定与 CLR 功能兼容的新项目。  
  
 **公共语言运行时（旧语法）**  
 指定与 Managed Extensions for C++ 语法（Visual C++ 2005 之前的 CLR 编程语法）兼容的新项目。  
  
 **使用外部生成系统**  
 指定使用未包含在 Visual Studio 中的生成工具来生成新项目。 如果选择此选项，可在“指定调试配置设置”页和“指定发布配置设置”页上指定生成命令行。  
  
> [!NOTE]
>  选中“使用外部生成系统”选项时，IDE 不会生成新项目，因此在编译过程中不需要 /D、/I、/FI、/AI 或 /FU 选项。 但是为了让 IntelliSense 正常工作，需要正确设置这些选项。  
  
## <a name="see-also"></a>请参阅  
 [“从现有代码文件创建新项目”向导 ->“指定调试配置设置”](../ide/specify-debug-configuration-settings.md)   
 [指定发布配置设置，“从现有代码文件创建新项目”向导](../ide/specify-release-configuration.md)