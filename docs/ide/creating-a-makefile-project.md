---
title: 创建 C++ 生成文件项目 | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f937c11b2453bd296468c5f153b7c9495eba290
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990238"
---
# <a name="creating-a-c-makefile-project"></a>创建 C++ 生成文件项目

生成文件是一种说明如何编译和链接（或生成）一组 C++ 源代码文件的文本文件。 生成程序会读取生成文件并调用编译器、链接器和其他程序来生成可执行文件。 Microsoft 实现生成程序的过程被称为 NMAKE。 （Visual Studio 在默认情况下使用基于 .vcxproj 文件的 MSBuild 系统；这是通过“文件 | 新建 | 项目”创建的。）

如果你有现有生成文件项目，则当你想要在 Visual Studio IDE 中编码和/或对其进行调试时，你有以下选择：

- 在 Visual Studio 中创建这样的生成文件项目：它使用现有生成文件在 IDE 中生成代码。 （你将不会具有在本机 MSBuild 项目中获得的所有 IDE 功能。）请参阅下面的[创建生成文件项目](#create_a_makefile_project)。
- 使用“从现有代码文件新建项目”向导来从源代码创建本机 MSBuild 项目。 有关详细信息，请参阅[如何：通过现有代码创建 C++ 项目](how-to-create-a-cpp-project-from-existing-code.md)。
- Visual Studio 2017 和更高版本：使用“打开文件夹”功能打开生成文件项目，但不将其转换为 MSBuild。 有关详细信息，请参阅 [Visual C++ 中的“打开文件夹”项目](non-msbuild-projects.md)。

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> 使用生成文件项目模板创建生成文件项目

在 Visual Studio 2017 和更高版本中，生成项目模板在安装 C++ 桌面开发工作负载后可用。

按照向导来指定用于生成文件的命令和环境。 然后可以在 Visual Studio 开发环境中使用该项目生成代码。

默认情况下，在解决方案资源管理器中，生成文件项目不显示文件。 生成文件项目指定生成设置，这些设置反映在项目的属性页中。

在项目中指定的输出文件对生成脚本生成的名称无效；它仅声明意图。 生成文件仍控制生成过程并指定生成目标。

1. 从 Visual Studio 起始页上，在“新建项目”搜索框中键入“生成文件”。 或者，在“新建项目”对话框中，展开“Visual C++” > “常规” (Visual Studio 2015) 或“其他”(Visual Studio 2017)，然后选择“模板”窗格中的“生成文件项目”以打开项目向导。

1. 在[应用程序设置](../ide/application-settings-makefile-project-wizard.md)页中，提供用于调试和传播生成的命令、输出、清除和重新生成信息。

1. 单击“完成”关闭向导并在解决方案资源管理器中打开新创建的项目。

可以在项目的属性页中查看和编辑项目的属性。 有关如何显示属性页的信息，请参阅[设置 Visual C++ 项目属性](../ide/working-with-project-properties.md)。

## <a name="see-also"></a>请参阅

[生成文件项目向导](../ide/makefile-project-wizard.md)<br/>
[生成文件中的特殊字符](../build/special-characters-in-a-makefile.md)<br/>
[生成文件的内容](../build/contents-of-a-makefile.md)<br/>
