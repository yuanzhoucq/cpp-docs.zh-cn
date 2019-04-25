---
title: CMakeSettings.json 架构引用
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 893bc5c8efe3fdae80a4a0de8204d391baa63d07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195376"
---
# <a name="cmakesettingsjson-schema-reference"></a>CMakeSettings.json 架构引用

**Cmakesettings.json**文件包含用于指定 Visual Studio 应该如何与 CMake 以生成用于指定平台的项目交互的信息。 可使用此文件来存储 cmake.exe 环境的环境变量或参数等信息。

## <a name="environments"></a>环境

`environments` 数组包含类型 `object` 的 `items` 列表，该类型用于定义“环境”。 环境可用于将一组变量应用到 `configuration`。 `environments` 数组中的每一项都包含以下内容：

- `namespace`：为环境命令，以便可从窗体 `namespace.variable` 中的配置中引用其变量。 默认环境对象称为 `env` 并由某种包括 `%USERPROFILE%` 的系统环境变量填充。
- `environment`：唯一标识此组变量。 允许稍后在 `inheritEnvironments` 输入中继承该组。
- `groupPriority`：评估变量时指定这些变量的优先级的整数。 优先评估数字较大的项。
- `inheritEnvironments`：指定由该组继承的一组环境的数组值。 可使用的任何自定义环境，或者这些预定义环境：
 
  - linux_arm：远程将 ARM Linux 设为目标。
  - linux_x64：远程将 x64 Linux 设为目标。
  - linux_x86：远程将 x86 Linux 设为目标。
  - msvc_arm：将具有 MSVC 编译器的 ARM Windows 设为目标。
  - msvc_arm_x64：将具有 64 位 MSVC 编译器的 ARM Windows 设为目标。
  - msvc_arm64：将具有 MSVC 编译器的 ARM64 Windows 设为目标。
  - msvc_arm64_x64：将具有 64 位 MSVC 编译器的 ARM64 Windows 设为目标。
  - msvc_x64：将具有 MSVC 编译器的 x64 Windows 设为目标。
  - msvc_x64_x64：将具有 64 位 MSVC 编译器的 x64 Windows 设为目标。
  - msvc_x86：将具有 MSVC 编译器的 x86 Windows 设为目标。
  - msvc_x86_x64：将具有 64 位 MSVC 编译器的 x86 Windows 设为目标。

## <a name="configurations"></a>配置

`configurations` 数组由应用于同一文件夹中 CMakeLists.txt 文件的 CMake 配置对象组成。 可以使用这些对象定义多个生成配置，并在 IDE 中方便地在它们之间进行切换。 

`configuration` 具有以下属性：
- `name`：为配置命名。
- `description`：将在菜单中显示的此配置的说明。
- `generator`：指定将在此配置中使用的 CMake 生成器。 可能是以下其中之一：

  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Unix 生成文件
  - Ninja

- `configurationType`：为选定的生成器指定生成类型配置。 可能是以下其中之一：
 
  - 调试
  - Release
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`：指定此配置依赖的一个或多个环境。 可以是任何自定义环境或预定义环境之一。
- `buildRoot`：指定 CMake 生成器要在其中为所选生成器生成脚本的目录。 支持的宏包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `installRoot`：指定 CMake 生成器要在其中为所选生成器安装目标的目录。 支持的宏包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `cmakeCommandArgs`：指定为生成缓存而调用时传递给 CMake 的附加命令行选项。
- `cmakeToolchain`：指定工具链文件。 这通过 -DCMAKE_TOOLCHAIN_FILE 传递到 CMake。
- `buildCommandArgs`：指定在“生成”后传递给 CMake 的本机生成开关。
- `ctestCommandArgs`：指定运行测试时传递给 CTest 的其他命令行选项。
- `codeAnalysisRuleset`：指定运行代码分析时要使用的规则集。 这可以是完整路径或由 Visual Studio 安装的规则集文件的文件名。
- `intelliSenseMode`：指定用于计算 IntelliSense 信息的模式。 可能是以下其中之一：
 
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
  - linux-gcc-arm”

- `cacheRoot`：指定 CMake 缓存的路径。 此目录应包含现有 CMakeCache.txt 文件。
- `remoteMachineName`：指定托管 CMake、生成和调试程序的远程 Linux 计算机的名称。 使用连接管理器添加新的 Linux 计算机。 支持的宏包括 `${defaultRemoteMachineName}`。
- `remoteCopySourcesOutputVerbosity`：指定将源复制到远程计算机的操作的详细级别。 可以是“常规”、“详细”或“诊断”其中之一。
- `remoteCopySourcesConcurrentCopies`：指定将源同步到远程计算机时使用的并发副本数。
- `remoteCopySourcesMethod`：指定将文件复制到远程计算机的方法。 可以是“rsync”或“sftp”。
- `remoteCMakeListsRoot`：指定包含 CMake 项目的远程计算机上的目录。 支持的宏包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteBuildRoot`：指定 CMake 生成器要在其中为所选生成器生成脚本的远程计算机上的目录。 支持的宏包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteInstallRoot`：指定 CMake 生成器要在其中为所选生成器安装目标的远程计算机上的目录。 支持的宏包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}` 和 `${env.VARIABLE}`，其中最后一项的环境变量为 `VARIABLE`且已在系统、用户或会话级别进行定义。
- `remoteCopySources`：`boolean`，指定 Visual Studio 是否应将源文件复制到远程计算机。 默认值为 true。 如果自行管理文件同步，则设置为 false。
- `remoteCopyBuildOutput`：`boolean`，指定是否要从远程计算机复制生成输出。
- `rsyncCommandArgs`：指定传递给 rsync 的附加命令行选项集。
- `remoteCopySourcesExclusionList`：指定复制源文件时要排除的路径列表的 `array`：路径可以是文件/目录的名称，或副本根目录的相对路径。 可使用通配符“\\\"*\\\"”和“\\\"?\\\"”进行 glob 模式匹配。
- `cmakeExecutable`：指定 CMake 程序可执行文件的完整路径，包括文件名和扩展名。
- `remotePreGenerateCommand`：指定在运行 CMake 以分析 CMakeLists.txt 文件之前要运行的命令。
- `remotePrebuildCommand`：指定生成前要在远程计算机上运行的命令。
- `remotePostbuildCommand`：指定生成后要在远程计算机上运行的命令。
- `variables`：`array`：指定作为 -Dname1=value1 -Dname2=value2 等传递到 CMake 的变量。 


