---
title: 如何：对生成文件项目启用 IntelliSense
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.IntelliSense
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
ms.openlocfilehash: 80a4696856fea46c7749cfeb120535dcdab86282
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434665"
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>如何：对生成文件项目启用 IntelliSense

错误设置某些项目设置或编译器操作时，IntelliSense 无法在 IDE 中针对 Visual C++ 生成文件项目运行。 使用此步骤配置 Visual C++ 生成文件项目，以便生成文件项目在 Visual Studio 开发环境中处于打开状态时，IntelliSense 能够运行。

### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>在 IDE 中对生成文件项目启用 IntelliSense

1. 打开“属性页”对话框。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 选择“NMake”属性页，然后在“IntelliSense”下适当修改属性。

   - 设置“预处理器定义”属性以定义生成文件项目中的任何预处理器符号。 请参阅 [/D （预处理器定义）](../build/reference/d-preprocessor-definitions.md)，获取详细信息。

   - 设置“包含搜索路径”属性，指定编译器将搜索的目录列表，以解析传递到生成文件项目中的预处理器指令的文件引用。 请参阅 [/I（附加包含目录）](../build/reference/i-additional-include-directories.md)，获取详细信息。

         For projects that are built using CL.EXE from a Command Window, set the **INCLUDE** environment variable to specify directories that the compiler will search to resolve file references that are passed to preprocessor directives in your makefile project.

   - 设置“强制包含”属性，指定生成生成文件时，要处理哪些头文件。 请参阅 [/FI（命名强制包含文件）](../build/reference/fi-name-forced-include-file.md)，获取详细信息。

   - 设置“程序集搜索路径”属性指定编译器将搜索的目录列表，以解析对项目中 .NET 程序集的引用。 请参阅 [/AI（指定元数据目录）](../build/reference/ai-specify-metadata-directories.md)，获取详细信息。

   - 设置“强制使用程序集”属性指定生成生成文件时，要处理哪些 .NET 程序集。 请参阅 [/FU（命名强制 #using 文件）](../build/reference/fu-name-forced-hash-using-file.md)，获取详细信息。

   - 设置“其他选项”属性，指定分析 C++ 文件时 IntelliSense 使用的附加编译器开关。

1. 单击“确定”关闭属性页。

1. 使用“全部保存”命令，保存已修改的项目设置。

下一次在 Visual Studio 开发环境中打开生成文件项目时，请在生成文件项目上依次运行“清理解决方案”命令和“生成解决方案”命令。 IntelliSense 应该会在 IDE 中正常运行。

## <a name="see-also"></a>请参阅

[使用 IntelliSense](/visualstudio/ide/using-intellisense)<br>
[NMAKE 参考](../build/nmake-reference.md)<br>
[如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)