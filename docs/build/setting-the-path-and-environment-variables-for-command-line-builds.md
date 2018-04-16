---
title: 为命令行生成设置路径和环境变量 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: get-started-article
f1_keywords:
- include
- Lib
- Path
dev_langs:
- C++
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
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76fa1a14b4fd60f249ab015f6618e386bda7c86f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>为命令行生成设置路径和环境变量

Visual c + + 命令行生成工具需要你安装和生成的配置的自定义的多个环境变量。 C + + 工作负荷通过在安装时[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安装程序中，而是创建自定义的命令文件或设置所需的环境变量的批处理文件。 安装然后使用这些命令文件创建的 Windows 开始菜单打开开发人员命令提示符窗口快捷方式。 这些设置特定的环境变量的快捷方式生成配置。 如果你想要使用命令行工具，你可以运行这些快捷方式，之一或可以打开纯命令提示符窗口，然后运行要自行设置生成配置环境的自定义命令文件之一。 有关详细信息，请参阅[命令行上生成 C/c + + 代码](building-on-the-command-line.md)。  
  
Visual c + + 命令行工具使用的路径、 TMP、 INCLUDE、 LIB 和 LIBPATH 环境变量，并还使用特定于你已安装的工具、 平台和 Sdk 其他环境变量。 即使一个简单[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安装可能设置二十个或多个环境变量。 由于这些环境变量的值特定于你的安装和你选择的生成配置，并且可以通过产品更新或升级更改，我们强烈建议你使用的开发人员命令提示符快捷方式或之一若要设置它们，而不是自行设置它们在 Windows 环境中的自定义的命令文件。 

若要查看哪些环境变量设置的开发人员命令提示符快捷方式，可以使用 SET 命令。 打开一个普通命令提示符窗口，并捕获的基线的 SET 命令的输出。 打开开发人员命令提示符窗口，并捕获比较 SET 命令的输出。 Visual Studio IDE 中内置的一个之类的差异工具可用于比较的环境变量并查看内容将由开发人员命令提示。 有关使用编译器和链接器的特定环境变量的信息，请参阅[CL 环境变量](../build/reference/cl-environment-variables.md)和[LINK 环境变量](../build/reference/link-environment-variables.md)。  
  
> [!NOTE]
>  多个命令行工具或工具选项可能需要管理员权限。 如果你有权限问题，使用它们时，我们建议使用打开开发人员命令提示符窗口，**以管理员身份运行**选项。 在 Windows 10 中，右键单击以打开命令提示符窗口的快捷菜单，然后选择**详细**，**以管理员身份运行**。  
  
## <a name="see-also"></a>请参阅  

[在命令行上生成 C/c + + 代码](../build/building-on-the-command-line.md)   
[链接](../build/reference/linking.md)   
[链接器选项](../build/reference/linker-options.md)   
[编译 C/c + + 程序](../build/reference/compiling-a-c-cpp-program.md)   
[编译器选项](../build/reference/compiler-options.md)