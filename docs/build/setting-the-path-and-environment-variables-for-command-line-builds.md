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
ms.openlocfilehash: aeafe806e5d29b89c243586974814aa7cfc16d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335587"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>为命令行生成设置路径和环境变量

Microsoft C++ (MSVC) 命令行生成工具需要多个为安装和生成配置自定义的环境变量。 当通过 Visual Studio 安装程序安装 C++ 工作负载时，它会创建用于设置所需环境变量的自定义命令文件或批处理文件。 安装程序随后使用这些命令文件为 Windows“开始”菜单创建快捷方式，用于打开开发人员命令提示窗口。 这些快捷方式为特定生成配置设置环境变量。 当你要使用命令行工具时，可以运行这些快捷方式之一，也可以打开纯命令提示窗口，然后运行自定义命令文件之一来自己设置生成配置环境。 有关详细信息，请参阅[通过命令行使用 MSVC 工具集](building-on-the-command-line.md)。 若要通过纯命令提示符使用命令文件，请参阅标题为[开发人员命令文件位置](building-on-the-command-line.md#developer_command_file_locations)一节。

MSVC 命令行工具使用 PATH、TMP、INCLUDE、LIB 和 LIBPATH 环境变量，还使用特定于已安装工具、平台和 SDK 的其他环境变量。 即使是简单 Visual Studio 安装，也可以设置二十或更多个环境变量。 由于这些环境变量的值特定于安装和生成配置选择，并且可能因产品更新或升级而进行更改，因此强烈建议使用开发人员命令提示快捷方式或自定义命令文件之一来设置它们，而不是自己在 Windows 环境中设置它们。

若要查看通过开发人员命令提示快捷方式设置的环境变量，可以使用 SET 命令。 打开纯命令提示窗口，并捕获 SET 命令输出以用作基线。 打开开发人员命令提示窗口，并捕获 SET 命令输出以用于比较。 差异工具（如 Visual Studio IDE 中内置的工具）可用于比较环境变量并查看通过开发人员命令提示设置的内容。 有关由编译器和链接器使用的特定环境变量的信息，请参阅 [CL 环境变量](reference/cl-environment-variables.md)。

> [!NOTE]
> 多个命令行工具或工具选项可能需要管理员权限。 如果在使用它们时遇到权限问题，则建议使用“以管理员身份运行”选项打开开发人员命令提示窗口  。 在 Windows 10 上，右键单击以打开命令提示窗口的快捷菜单，然后依次选择“更多”  、“以管理员身份运行”  。

## <a name="see-also"></a>请参阅

[通过命令行使用 MSVC 工具集](building-on-the-command-line.md)<br/>
[MSVC 链接器参考](reference/linking.md)<br/>
[MSVC 链接器选项](reference/linker-options.md)<br/>
[MSVC 编译器参考](reference/compiling-a-c-cpp-program.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)
