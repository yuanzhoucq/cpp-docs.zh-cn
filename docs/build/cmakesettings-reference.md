---
title: CMakeSettings.json 架构参考
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: d80829b1475e8718e1c4188ff4fb7d42a1d4b3b9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825105"
---
# <a name="cmakesettingsjson-schema-reference"></a>CMakeSettings.json 架构参考

`cmakesettings.json`文件包含用于指定 Visual Studio 应该如何与 CMake 以生成用于指定平台的项目交互的信息。 使用此文件来存储信息，例如环境变量或 cmake.exe 环境的自变量。

## <a name="environments"></a>环境

`environments`数组包含一系列`items`类型的`object`用于定义应用程序"环境"。 环境可用于将应用到的变量的一组`configuration`。 中的每项`environments`数组组成：

- `namespace`:，以便可以从窗体中的配置引用其变量名称在环境`namespace.variable`。 默认环境对象称为`env`并填入某些系统环境变量，包括`%USERPROFILE%`。
- `environment`： 唯一标识此组的变量。 允许组更高版本中继承`inheritEnvironments`条目。
- `groupPriority`：一个整数，指定时评估这些变量的优先级。 首先计算更高版本的项数。
- `inheritEnvironments`：指定由此组继承的环境的设置的值的数组。 可以使用任何自定义环境，或这些预定义的环境：
 
  - linux_arm:远程目标 ARM Linux。
  - linux_x64:面向 x64 Linux 远程。
  - linux_x86:面向 x86 Linux 远程。
  - msvc_arm:目标使用 MSVC 编译器的 ARM Windows。
  - msvc_arm_x64:目标使用 64 位 MSVC 编译器的 ARM Windows。
  - msvc_arm64:目标使用 MSVC 编译器的 ARM64 Windows。
  - msvc_arm64_x64:目标使用 64 位 MSVC 编译器的 ARM64 Windows。
  - msvc_x64:使用 MSVC 编译器面向 x64 Windows。
  - msvc_x64_x64:使用 64 位 MSVC 编译器面向 x64 Windows。
  - msvc_x86:使用 MSVC 编译器面向 x86 Windows。
  - msvc_x86_x64:使用 64 位 MSVC 编译器面向 x86 Windows。

## <a name="configurations"></a>配置

`configurations`数组包含表示应用于同一文件夹中 CMakeLists.txt 文件的 CMake 配置的对象。 这些对象可用于定义多个生成配置，并方便地在 IDE 中它们之间进行切换。 

一个`configuration`具有以下属性：
- `name`： 在配置的名称。
- `description`： 在菜单中将显示此配置的说明。
- `generator`： 指定要用于此配置的 CMake 生成器。 可能的一个：

  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Unix 生成文件
  - Ninja

- `configurationType`： 指定选定的生成器的生成类型配置。 可能的一个：
 
  - 调试
  - Release
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`： 指定此配置依赖的一个或多个环境。 可以是任何自定义环境或其中一个预定义的环境。
- `buildRoot`： 比较 directory CMake 在其中生成生成脚本的所选的生成器。 受支持的宏包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`， `${env.VARIABLE}`。"
- `installRoot`： 指定在其中 CMake 生成安装目标为所选的生成器的目录。 受支持的宏包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`， `${env.VARIABLE}`。"
- `cmakeCommandArgs`： 指定其他命令行选项传递给 CMake 调用时生成缓存。"
- `cmakeToolchain`： 指定工具链文件。 这将传递给 CMake 使用-DCMAKE_TOOLCHAIN_FILE。"
- `buildCommandArgs`： 指定-生成-后传递给 CMake 的本机生成开关。"
- `ctestCommandArgs`： 指定要运行测试时，其他命令行选项传递给 CTest。"
- `codeAnalysisRuleset`： 指定运行代码分析时要使用的规则集。 这可以是完整路径或由 Visual Studio 安装的规则集文件的文件名。"
- `intelliSenseMode`： 指定用于计算 intellisense 信息的模式"。 可能的一个：
 
  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-arm
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-arm
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - ios-clang-arm
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm"

- `cacheRoot`： 指定 CMake 缓存的路径。 此目录应包含现有 CMakeCache.txt 文件。
- `remoteMachineName`： 指定托管 CMake、 生成和调试程序的远程 Linux 计算机的名称。 用于连接管理器添加新的 Linux 计算机。 受支持的宏包括`${defaultRemoteMachineName}`。
- `remoteCopySourcesOutputVerbosity`： 指定将操作复制到远程计算机的源的详细级别。 可能是一个""Normal"、"详细"或"诊断"。
- `remoteCopySourcesConcurrentCopies`： 指定在对到远程计算机的源的同步过程中使用的并发副本数。
- `remoteCopySourcesMethod`： 指定要将文件复制到远程计算机的方法。 可能是"rsync"或"sftp"。
- `remoteCMakeListsRoot`： 指定包含 CMake 项目的远程计算机上的目录。 受支持的宏包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`， `${env.VARIABLE}`。
- `remoteBuildRoot`: CMake 在其中生成为选定生成器生成脚本在远程计算机上指定的目录。 受支持的宏包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`， `${env.VARIABLE}`。
- `remoteInstallRoot`: CMake 在其中生成安装目标为所选生成器在远程计算机上指定的目录。 受支持的宏包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`，并`${env.VARIABLE}`其中`VARIABLE`是具有一个环境变量已在系统、 用户或会话级别定义。
- `remoteCopySources`：一个`boolean`，它指定 Visual Studio 是否应将源文件复制到远程计算机。 默认值为 true。 如果你自行管理文件同步，则设置为 false。
- `remoteCopyBuildOutput`：一个`boolean`，指定是否要从远程系统复制生成输出。
- `rsyncCommandArgs`： 指定一组传递给 rsync 的附加命令行选项。
- `remoteCopySourcesExclusionList`：一个`array`，它指定要复制源文件时排除的路径的列表： 路径可以是文件/目录或相对于副本的根路径的名称。 通配符\\ \" * \\ \"并\\ \"？\\\"可用于 glob 模式匹配。
- `cmakeExecutable`： 指定 CMake 程序可执行文件，其中包括文件名和扩展名的完整路径。
- `remotePreGenerateCommand`： 指定要在运行 CMake 以分析 CMakeLists.txt 文件之前运行的命令。
- `remotePrebuildCommand`： 指定要生成前在远程计算机上运行的命令。
- `remotePostbuildCommand`： 指定要在远程计算机上运行生成后的命令。
- `variables`：一个`array`，它指定变量传递给 CMake 作为-Dname1 = value1-Dname2 = value2，等等。 


