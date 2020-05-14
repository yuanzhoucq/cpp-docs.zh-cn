---
title: 如何：从现有代码创建 C++ 项目
ms.date: 05/06/2019
helpviewer_keywords:
- C++, creating projects from existing code
- Create New Project From Existing Code Files Wizard, project settings
f1_keywords:
- vc.appwiz.importwiz.location
- vc.appwiz.importwiz.appsettings
- vc.appwiz.importwiz.debugsettings
- vc.appwiz.importwiz.releasesettings
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: 5e59230186380b787c95dbe08914bcd9d3ca2407
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078550"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>如何：从现有代码创建 C++ 项目

在 Visual Studio 中，你可以使用“从现有代码文件创建新项目”向导将现有代码文件移植到 C++ 项目中  。 此向导创建使用 MSBuild 系统来管理源文件和生成配置的项目解决方案。 它最适用于没有复杂文件夹层次结构的相对简单的项目。 Visual Studio 的较旧 Express 版本中不提供该向导。

通过将现有代码文件移植到 C++ 项目，即可使用内置于 IDE 的本机 MSBuild 项目管理功能。 如果更想使用现有的生成系统（例如 nmake 生成文件、CMake 或其他生成系统），则可以改为使用“打开文件夹或 CMake”选项。 有关详细信息，请参阅 [C++ 的“打开文件夹”项目](open-folder-projects-cpp.md)或 [Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)。 通过这两个选项都可以使用 IDE 功能，例如 [IntelliSense](/visualstudio/ide/using-intellisense) 和 [项目属性](working-with-project-properties.md)。

### <a name="to-create-a-c-project-from-existing-code"></a>从现有代码创建 C++ 项目

1. 在“文件”菜单上，选择“新建” > “从现有代码创建项目”    。

1. 指定项目位置、源文件目录以及向导导入新项目的文件类型。 选择“下一步”  继续。

    | 设置 | 描述 |
    | --- | --- |
    | **项目文件位置** | 指定新项目的目录路径。 这是该向导放置所有新项目文件（和子目录）的位置。<br/><br/>选择“浏览”以显示“项目文件位置”对话框   。 导航到正确的文件夹并指定包含新项目的目录。 |
    | **项目名称** | 指定新项目的名称。 具有 .vcxproj 等文件扩展名的项目文件采用此名称，现有代码文件保留其原始名称。 |
    | **将文件从这些文件夹添加到项目中** | 选中以将向导设置为将现有代码文件从其原始目录（在此控件下的列表框中指定）复制到新项目中。<br/><br/>选中“添加子文件夹”以指定将所有子目录中的代码文件复制到项目中。  这些目录列在“文件夹”列中  。<br/>- 选择“添加”可显示“将文件从此文件夹添加到项目”对话框，以指定向导搜索现有代码文件的目录   。<br/>- 选择“删除”可删除列表框中选择的目录路径  。<br/><br/>在“要添加到项目中的文件类型”对话框中，指定向导将添加到基于给定文件扩展名的新项目的文件类型  。 文件扩展名前面带有星号通配符，并在文件扩展名列表中以分号隔开。 |
    | **在解决方案资源管理器中显示所有文件** | 指定新项目中的所有文件都可见并在“解决方案资源管理器”窗口中显示  。 默认情况下会启用此选项。 |

    ![项目位置](media/location.png)

1. 指定要使用的项目设置（例如新项目的生成环境），以及与要生成的特定类型的新项目匹配的生成设置。 选择“下一步”  继续。

    | 设置 | 描述 |
    | --- | --- |
    | **使用 Visual Studio** | 指定使用 Visual Studio 包含的生成工具来生成新项目。 默认情况下选择此选项。<br/><br/>选择“项目类型”以指定向导生成的项目类型  。 选择“Windows 应用程序项目”、“控制台应用程序项目”、“动态链接库 (DLL) 项目”或“静态库 (LIB) 项目”     。<br/><br/>检查“添加对 ATL 的支持”，以便为新项目添加 ATL 支持  。<br/><br/>检查“添加对 MFC 的支持”，以便为新项目添加 MFC 支持  。<br/><br/>检查“添加对公共语言运行时的支持”，以便为项目添加 CLR 编程支持  。 对于符合性类型，选择“公共语言运行时支持”，例如选择“公共语言运行时(旧语法)”以符合 Managed Extensions for C++ 语法（即 Visual Studio 2005 之前的 CLR 编程语法）的规定   。 |
    | **使用外部生成系统** | 指定使用未包含在 Visual Studio 中的生成工具来生成新项目。 如果选择此选项，可在“指定调试配置设置”页和“指定发布配置设置”页上指定生成命令行   。 |

    ![项目设置](media/settings.png)

    > [!NOTE]
    > 选中“使用外部生成系统”选项时，IDE 不会生成项目，因此在编译过程中不需要 /D、/I、/FI、/AI 或 /FU 选项  。 但是为了让 IntelliSense 正常工作，需要正确设置这些选项。

1. 指定要使用的调试配置设置。 选择“下一步”  继续。

    | 设置 | 描述 |
    | --- | --- |
    | **生成命令行** | 指定生成项目的命令行。 输入编译器的名称（以及任何开关和参数）或要用于生成项目的生成脚本。 |
    | **重新生成命令行** | 指定重新生成新项目的命令行。 |
    | **清除命令行** | 指定命令行以删除由项目的生成工具所生成的支持文件。 |
    | **输出(用于调试)** | 指定项目“调试”配置的输出文件的目录路径。 |
    | **预处理器定义(/D)** | 定义项目的预处理器符号，请参阅 [/D（预处理器定义）](../build/reference/d-preprocessor-definitions.md)。 |
    | **包含搜索路径(/I)** | 指定编译器搜索的目录路径，用以解析传递给项目中预处理器指令的文件引用，请参阅 [/I（其他包含目录）](../build/reference/i-additional-include-directories.md)。 |
    | **强制包含的文件(/FI)** | 指定生成项目时要处理的头文件，请参阅 [/FI（命名强制包含文件）](../build/reference/fi-name-forced-include-file.md)。 |
    | **.NET 程序集搜索路径(/AI)** | 指定编译器搜索的目录路径，用以解析传递给项目中预处理器指令的 .NET 程序集引用，请参阅 [/AI（指定元数据目录）](../build/reference/ai-specify-metadata-directories.md)。 |
    | **强制使用 .NET 程序集(/FU)** | 指定生成新项目时要处理的 .NET 程序集，请参阅 [/FU（命名强制 #using 文件）](../build/reference/fu-name-forced-hash-using-file.md)。 |

    ![项目配置](media/config.png)

    > [!NOTE]
    > 仅当“使用外部生成系统”选项在“制定项目设置”页中处于选中状态时，才启用“生成”、“重新生成”、“清理”命令行和“输出(用于调试)”设置       。

1. 指定要使用的发布配置设置，这些设置与调试配置设置相同。 单击“完成”以生成新项目  。

    > [!NOTE]
    > 此处可检查“与调试配置相同”，以指定向导将生成与调试配置项目设置相同的发布配置项目设置  。 默认情况下，此选项处于选中状态。 除非取消选中此框，否则此页上的所有其他选项都处于非活动状态。
