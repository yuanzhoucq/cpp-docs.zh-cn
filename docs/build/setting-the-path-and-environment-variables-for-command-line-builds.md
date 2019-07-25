---
title: 为命令行生成设置路径和环境变量
ms.custom: conceptual
ms.date: 07/24/2019
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
ms.openlocfilehash: 6e7882b169805e3c62596341986a83d476ac5ec1
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492152"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>为命令行生成设置路径和环境变量

Microsoft C++ (MSVC) 命令行生成工具需要为你的安装和生成配置自定义的多个环境变量。 当通过C++ Visual Studio 安装程序安装工作负荷时, 它会创建自定义的命令文件或批处理文件, 用于设置所需的环境变量。 然后, 安装程序将使用这些命令文件为 Windows "开始" 菜单创建快捷方式, 以打开 "开发人员命令提示" 窗口。 这些快捷方式为特定的生成配置设置环境变量。 如果要使用命令行工具, 你可以运行其中一个快捷方式, 也可以打开一个纯命令提示符窗口, 然后运行一个自定义命令文件来自行设置生成配置环境。 有关详细信息, 请参阅[从命令行使用 MSVC 工具集](building-on-the-command-line.md)。 若要将命令文件与纯命令提示符一起使用, 请参阅 "[开发人员命令文件位置](building-on-the-command-line.md#developer_command_file_locations)" 一节。

MSVC 命令行工具使用 PATH、TMP、INCLUDE、LIB 和 LIBPATH 环境变量, 并使用特定于已安装的工具、平台和 Sdk 的其他环境变量。 即使是简单的 Visual Studio 安装, 也可以设置二十个或更多的环境变量。 由于这些环境变量的值特定于你的安装和你选择的生成配置, 并且可以通过产品更新或升级进行更改, 因此强烈建议你使用开发人员命令提示快捷方式或自定义的命令文件, 用于设置这些文件, 而不是自己在 Windows 环境中设置它们。

若要查看由开发人员命令提示快捷方式设置的环境变量, 可以使用 SET 命令。 打开普通的命令提示符窗口, 并捕获基线的 SET 命令的输出。 打开 "开发人员命令提示" 窗口, 并捕获 SET 命令的输出以进行比较。 在 Visual Studio IDE 中内置的比较工具可用于比较环境变量并查看由开发人员命令提示设置的内容。 有关编译器和链接器使用的特定环境变量的信息, 请参阅[CL 环境变量](reference/cl-environment-variables.md)。

> [!NOTE]
>  几个命令行工具或工具选项可能需要管理员权限。 如果你在使用权限时遇到权限问题, 我们建议你使用 "以**管理员身份运行**" 选项打开 "开发人员命令提示" 窗口。 在 Windows 10 上, 右键单击以打开 "命令提示符" 窗口的快捷菜单, 然后选择 "**更多**, 以**管理员身份运行**"。

## <a name="see-also"></a>请参阅

[通过命令行使用 MSVC 工具集](building-on-the-command-line.md)<br/>
[MSVC 链接器参考](reference/linking.md)<br/>
[MSVC 链接器选项](reference/linker-options.md)<br/>
[MSVC 编译器参考](reference/compiling-a-c-cpp-program.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)
