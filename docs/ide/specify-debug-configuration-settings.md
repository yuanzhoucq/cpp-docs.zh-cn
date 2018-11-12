---
title: 从现有代码调试设置新建项目 (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.importwiz.debugsettings
ms.assetid: 607339a8-9d33-458b-8095-dc73f374e29d
ms.openlocfilehash: 9c43e86bedd08667c67427e69e12b21c59492fba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565056"
---
# <a name="specify-debug-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>“从现有代码文件创建新项目”向导 ->“指定调试配置设置”

使用“从现有代码文件创建新项目”向导的此页指定“调试”配置项目设置。

## <a name="task-list"></a>任务列表

[如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>UIElement 列表

- **生成命令行**

   指定生成新项目的命令行。 例如，输入编译器的名称（以及任何开关和参数）或要用于生成新项目的生成脚本。 如果在“指定项目设置”页中选择了“使用外部生成系统”选项，则启用此选项；否则它不可用。

- **重新生成命令行**

   指定重新生成新项目的命令行。 如果在“指定项目设置”页中选择了“使用外部生成系统”选项，则启用此选项；否则它不可用。

- **清除命令行**

   指定命令行以删除由新项目的生成工具所生成的支持文件。 如果在“指定项目设置”页中选择了“使用外部生成系统”选项，则启用此选项；否则它不可用。

- **输出(用于调试)**

   指定新项目“调试”配置的输出文件的目录路径。 如果在“指定项目设置”页中选择了“使用外部生成系统”选项，则启用此选项；否则它不可用。

- **预处理器定义(/D)**

   为新项目定义预处理器符号。 有关详细信息，请参阅 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)。

- **包含搜索路径(/I)**

   指定要添加到目录列表中的目录路径，编译器将搜索该路径以解析传递给新项目中预处理器指令的文件引用。 有关详细信息，请参阅 [/I（附加包含目录）](../build/reference/i-additional-include-directories.md)。

- **强制包含的文件(/FI)**

   指定生成新项目时要处理的头文件。 有关详细信息，请参阅 [/FI（命名强制包含文件）](../build/reference/fi-name-forced-include-file.md)。

- **.NET 程序集搜索路径(/AI)**

   指定编译器将搜索的目录路径，用以解析传递给新项目中预处理器指令的 .NET 程序集引用。 有关详细信息，请参阅 [/AI（指定元数据目录）](../build/reference/ai-specify-metadata-directories.md)。

- **强制使用 .NET 程序集(/FU)**

   指定生成新项目时要处理的 .NET 程序集。 有关详细信息，请参阅 [/FU（命名强制 #using 文件）](../build/reference/fu-name-forced-hash-using-file.md)。

## <a name="see-also"></a>请参阅

[指定项目设置，“从现有代码文件创建新项目”向导](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)
