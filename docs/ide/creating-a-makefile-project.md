---
title: 创建生成文件项目 |Microsoft 文档
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-makefile-project"></a>创建生成文件项目

如果必须通过使用生成文件中的命令行生成的现有源代码项目，Visual Studio 开发环境都有多种方法可以将其转变为可以充分利用 Visual Studio IDE 功能的项目。 本文介绍如何使用你现有的生成文件来生成你在 IDE 中的代码的 Visual Studio 中创建生成文件项目。 或者，可以使用**从现有代码文件创建新项目**向导从源代码创建本机 MSBuild 项目。 有关详细信息，请参阅[如何：通过现有代码创建 C++ 项目](how-to-create-a-cpp-project-from-existing-code.md)。 从 Visual Studio 2017 年 1 开始，你还可以使用**打开文件夹**功能，可以使用多个现有的生成系统，就像它们是本机 Visual Studio 项目。 有关详细信息，请参阅 [Visual C++ 中的“打开文件夹”项目](non-msbuild-projects.md)。

若要使用 Visual Studio 打开并使用你现有的生成文件生成源代码，首先应通过选择生成文件项目模板创建新项目。 向导将帮助你指定的命令和使用你的生成文件的环境。 然后可以使用此项目以生成代码在 Visual Studio 开发环境中。

默认情况下，生成文件项目在解决方案资源管理器中显示任何文件。 生成文件项目指定生成设置，反映在项目的属性页。

在项目中指定的输出文件对生成脚本生成的名称无效；它仅声明意图。 你的生成文件仍控制生成过程，并指定生成目标。

## <a name="to-create-a-makefile-project"></a>创建生成文件项目

1. 按照帮助主题中的说明[使用 Visual c + + 应用程序向导创建项目](../ide/creating-desktop-projects-by-using-application-wizards.md)。

1. 在**新项目**对话框框中，展开**Visual c + +** > **常规**，然后选择**生成文件项目**中若要打开项目向导的模板窗格。

1. 在[应用程序设置](../ide/application-settings-makefile-project-wizard.md)页上，提供命令，输出中，清除和重新生成信息适用于调试和零售生成。

1. 单击**完成**要关闭向导并打开新创建的项目中**解决方案资源管理器**。

可以在项目的属性页中查看和编辑项目的属性。 请参阅[设置 Visual c + + 项目属性](../ide/working-with-project-properties.md)有关显示的属性页信息。

## <a name="see-also"></a>请参阅

[生成文件项目向导](../ide/makefile-project-wizard.md)<br/>
[生成文件中的特殊字符](../build/special-characters-in-a-makefile.md)<br/>
[生成文件的内容](../build/contents-of-a-makefile.md)<br/>
