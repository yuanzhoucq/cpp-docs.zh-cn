---
title: 创建生成文件项目 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2018
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
ms.openlocfilehash: dc854f96f1c41baf28a5af4ca1f253e47d9a8914
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336773"
---
# <a name="creating-a-makefile-project"></a>创建生成文件项目

如果有通过使用生成文件从命令行生成的现有源代码项目，Visual Studio 开发环境有多种方法可以将其转变为可以充分利用 Visual Studio IDE 功能的项目。 本文介绍如何在 Visual Studio 中创建这样的生成文件项目，它使用现有生成文件在 IDE 中生成代码。 或者可以使用“从现有代码文件新建项目”向导来，从源代码创建本机 MSBuild 项目。 有关详细信息，请参阅[如何：通过现有代码创建 C++ 项目](how-to-create-a-cpp-project-from-existing-code.md)。 从 Visual Studio 2017 开始，还可以使用“打开文件夹”功能，该功能可以将多个现有生成系统用作本机 Visual Studio 项目。 有关详细信息，请参阅 [Visual C++ 中的“打开文件夹”项目](non-msbuild-projects.md)。

若要借助 Visual Studio 使用你的现有生成文件打开或生成源代码，请先选择生成文件项目模板来新建一个项目。 向导将帮助你指定用于生成文件的命令和环境。 然后可以在 Visual Studio 开发环境中使用该项目生成代码。

默认情况下，在解决方案资源管理器中，生成文件项目不显示文件。 生成文件项目指定生成设置，这些设置反映在项目的属性页中。

在项目中指定的输出文件对生成脚本生成的名称无效；它仅声明意图。 生成文件仍控制生成过程并指定生成目标。

## <a name="to-create-a-makefile-project"></a>创建生成文件项目

1. 请按帮助主题[使用 Visual C++ 应用程序向导创建项目](../ide/creating-desktop-projects-by-using-application-wizards.md)中的说明进行操作。

1. 在“新建项目”对话框中，展开“Visual C++” > “常规”，然后选择“模板”窗格中的“生成文件项目”以打开项目向导。

1. 在[应用程序设置](../ide/application-settings-makefile-project-wizard.md)页中，提供用于调试和传播生成的命令、输出、清除和重新生成信息。

1. 单击“完成”关闭向导并在解决方案资源管理器中打开新创建的项目。

可以在项目的属性页中查看和编辑项目的属性。 有关如何显示属性页的信息，请参阅[设置 Visual C++ 项目属性](../ide/working-with-project-properties.md)。

## <a name="see-also"></a>请参阅

[生成文件项目向导](../ide/makefile-project-wizard.md)<br/>
[生成文件中的特殊字符](../build/special-characters-in-a-makefile.md)<br/>
[生成文件的内容](../build/contents-of-a-makefile.md)<br/>
