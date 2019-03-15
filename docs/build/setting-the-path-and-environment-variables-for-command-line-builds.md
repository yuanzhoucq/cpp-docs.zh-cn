---
title: 为命令行生成设置路径和环境变量
ms.custom: conceptual
ms.date: 11/04/2016
f1_keywords:
- include
- Lib
- Path
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
ms.openlocfilehash: fed3360294bec724af09b87e5abd7c6bb22fa285
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811064"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>为命令行生成设置路径和环境变量

Visual c + + 命令行生成工具需要你安装和生成的配置进行自定义的多个环境变量。 通过 Visual Studio 安装程序安装 c + + 工作负荷时，它创建自定义的命令文件或设置所需的环境变量的批处理文件。 安装程序然后使用这些命令文件创建的 Windows 开始菜单打开开发人员命令提示窗口快捷方式。 这些设置特定的环境变量的快捷方式生成配置。 当你想要使用命令行工具时，可以运行一个这些快捷方式，或可以打开纯命令提示符窗口并运行要自行设置生成配置环境的自定义命令文件之一。 有关详细信息，请参阅[使用命令行中的 MSVC 工具集](building-on-the-command-line.md)。

Visual c + + 命令行工具使用 PATH、 TMP、 INCLUDE、 LIB 和 LIBPATH 环境变量，还使用其他环境变量特定于安装的工具、 平台和 Sdk。 甚至简单的 Visual Studio 安装可能会设置 20 个或多个环境变量。 因为这些环境变量的值是特定于您的安装和所选的生成配置，可以更改产品更新或升级，我们强烈建议使用开发人员命令提示符快捷方式或其中一个若要设置它们，而不是自行设置它们在 Windows 环境中的自定义的命令文件。

若要查看哪些环境变量设置由开发人员命令提示符快捷方式，可以使用 SET 命令。 打开纯命令提示符窗口，并捕获的基线的 SET 命令的输出。 打开开发人员命令提示窗口，并捕获比较 SET 命令的输出。 例如 Visual Studio IDE 中内置的差异分析工具可用于比较的环境变量，并请参阅什么由开发人员命令提示设置。 有关使用编译器和链接器的特定环境变量的信息，请参阅[CL 环境变量](reference/cl-environment-variables.md)。

> [!NOTE]
>  多个命令行工具或工具选项可能需要管理员权限。 如果使用它们时遇到权限问题，我们建议使用打开开发人员命令提示符窗口**以管理员身份运行**选项。 在 Windows 10 中，右键单击以打开命令提示符窗口的快捷菜单，然后选择**更多**，**以管理员身份运行**。

## <a name="see-also"></a>请参阅

[使用命令行中的 MSVC 工具集](building-on-the-command-line.md)<br/>
[MSVC 链接器引用](reference/linking.md)<br/>
[MSVC 链接器选项](reference/linker-options.md)<br/>
[MSVC 编译器的引用](reference/compiling-a-c-cpp-program.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)
