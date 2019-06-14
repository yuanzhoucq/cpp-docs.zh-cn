---
title: CMakeSettings.json 架构引用
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 0dcd05833af005807d874d71e8f6a07d4e738e8c
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042593"
---
# <a name="cmakesettingsjson-schema-reference"></a>CMakeSettings.json 架构引用

Cmakesettings.json 文件提供用于指定 Visual Studio 应如何与 CMake 交互以为指定平台生成项目的信息  。 此文件存储 cmake.exe 环境的环境变量或参数等信息。 可以直接进行编辑，或者使用 CMake 设置编辑器（Visual Studio 2019 及更高版本）  。 有关编辑器的详细信息，请参阅[在 Visual Studio 中自定义 CMake 生成设置](customize-cmake-settings.md)。

## <a name="environments"></a>环境

`environments` 数组包含 `object` 类型的 `items` 列表，该类型用于定义编译器工具集“环境”。 环境可用于将一组变量应用到 `configuration`。 `environments` 数组中的每一项都包含以下内容：

- `namespace`：为环境命令，以便可从窗体 `namespace.variable` 中的配置中引用其变量。 默认环境对象称为 `env` 并由某种包括 `%USERPROFILE%` 的系统环境变量填充。
- `environment`：唯一标识此组变量。 允许稍后在 `inheritEnvironments` 输入中继承该组。
- `groupPriority`：评估变量时指定这些变量的优先级的整数。 优先评估数字较大的项。
- `inheritEnvironments`：指定由该组继承的一组环境的数组值。 使用该功能可以继承默认环境，以及创建在运行时传递给 CMake.exe 的自定义环境变量。

   ```json
   "inheritEnvironments": [ "msvc_x64_x64" ]
   ```

   上面的示例与运行带有“-arch=amd64 -host_arch=amd64”参数的“适用于 VS 2017 的开发人员命令提示”或“适用于 VS 2019 的开发人员命令提示”一样    。 可使用的任何自定义环境，或者这些预定义环境：
 
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
  
  **仅限 Visual Studio 2019：**
  - Visual Studio 16 2019
  - Visual Studio 16 2019 Win64
  - Visual Studio 16 2019 ARM

  **Visual Studio 2017 及更高版本：**
  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Unix 生成文件
  - Ninja

由于 Ninja 旨在加快生成速度，而不是为了提高灵活性和功能，因此它被设为默认生成器。 但是，某些 CMake 项目可能无法使用 Ninja 正确地进行生成。 如果发生这种情况，可以指示 CMake 改为生成 Visual Studio 项目。

要指定 Visual Studio 2017 中的 Visual Studio 生成器，请通过选择“CMake”|“更改 CMake 设置”，从主菜单打开 `CMakeSettings.json`  。 删除“Ninja”并键入“V”。 这可激活 IntelliSense，从而可让用户选择所需生成器。

要指定 Visual Studio 2019 中的 Visual Studio 生成器，请右键单击解决方案资源管理器中的 CMakeLists.txt 文件，并选择“项目的 CMake 设置” > “显示高级设置” > “CMake 生成器”     。

当活动配置指定一个 Visual Studio 生成器时，默认情况下使用 `-m -v:minimal` 参数调用 MSBuild.exe。 要自定义生成，可在 `CMakeSettings.json` 文件中指定要通过 `buildCommandArgs` 属性传递到生成系统的其他 [MSBuild 命令行参数](../build/reference/msbuild-visual-cpp-overview.md)：

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `configurationType`：为选定的生成器指定生成类型配置。 可能是以下其中之一：
 
  - 调试
  - Release
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`：指定此配置依赖的一个或多个编译器环境。 可以是任何自定义环境或预定义环境之一。
- `buildRoot`：指定 CMake 生成器要在其中为所选生成器生成脚本的目录。  映射到“-DCMAKE_BINARY_DIR”开关，并指定要创建 CMake 缓存的位置  。 如果文件夹不存在，则会创建该文件夹。支持的宏包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}` 和 `${env.VARIABLE}`。
- `installRoot`：指定 CMake 生成器要在其中为所选生成器安装目标的目录。 支持的宏包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `cmakeCommandArgs`：指定为生成缓存而调用时传递给 CMake 的附加命令行选项。
- `cmakeToolchain`：指定工具链文件。 这通过 -DCMAKE_TOOLCHAIN_FILE 传递到 CMake。
- `buildCommandArgs`：指定在“生成”后传递给 CMake 的本机生成开关。 例如，使用 Ninja 生成器强制输出命令行使用 Ninja 时，传递 -v。 请参阅 [Ninja 命令行参数](#ninja)，详细了解 Ninja 命令。
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

### <a name="additional-settings-for-cmake-linux-projects"></a>适用于 CMake Linux 项目的其他设置。 

- `remoteMachineName`：指定托管 CMake、生成和调试程序的远程 Linux 计算机的名称。 使用连接管理器添加新的 Linux 计算机。 支持的宏包括 `${defaultRemoteMachineName}`。
- `remoteCopySourcesOutputVerbosity`：指定将源复制到远程计算机的操作的详细级别。 可以是“常规”、“详细”或“诊断”其中之一。
- `remoteCopySourcesConcurrentCopies`： 指定在远程计算机 (仅 sftp) 到源的同步过程中使用的并发副本数。
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
- `variables`：包含将作为 -D name=value 传递到 CMake 的 CMake 变量的名称/值对    。 如果 CMake 项目生成指令指定将任何变量直接添加到 CMake 缓存文件，那么建议改为在这里添加它们。 下面的示例演示如何为 14.14.26428 MSVC 工具集指定名称/值对：

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    }
  ]
```

请注意，如果未定义 `"type"`，则默认采用“STRING”类型。

## <a name="environment-variables"></a>环境变量

`CMakeSettings.json` 还支持使用上述其任何属性中的环境变量。 所使用的语法为 `${env.FOO}`，用于展开环境变量 %FOO%。

此外，还可以使用此文件中内置的宏：

- `${workspaceRoot}`：提供工作区文件夹的完整路径
- `${workspaceHash}`：工作区位置的哈希；可用于创建当前工作区的唯一标识符（例如用于文件路径）
- `${projectFile}`：根 CMakeLists.txt 文件的完整路径
- `${projectDir}`：根 CMakeLists.txt 文件的文件夹完整路径
- `${thisFile}` - `CMakeSettings.json` 文件的完整路径
- `${name}`：配置的名称
- `${generator}`：配置中使用的 CMake 生成器的名称


### <a name="custom-environment-variables"></a>自定义环境变量

在 `CMakeSettings.json` 中，可在“环境”属性中以全局形式或按配置自定义环境变量  。 下面的示例定义一个全局变量“BuildDir”，该变量在 x86-Debug 和 x64-Debug 配置中继承  。 每个配置都使用该变量来指定配置的“buildRoot”属性值  。 也请注意每个配置如何使用“inheritEnvironments”属性来指定仅应用于该配置的值  。

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

在下一个示例中，x86-Debug 配置为 BuildDir 属性定义其自己的值  。 此值替代由全局 BuildDir 属性设置的值，以便 BuildRoot 评估为 `D:\custom-builddir\x86-Debug`   。

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir"
          // This environment does not specify a namespace, hence by default "env" will be assumed.
          // "namespace" : "name" would require that this variable be referenced with "${name.BuildDir}".
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ],
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="ninja"></a> Ninja 命令行参数

如果未指定目标，则生成“默认”目标。

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|选项|描述|
|--------------|------------|
| --version  | 打印 ninja 版本（“1.7.1”）|
|   -C DIR   | 在执行任何其他操作前更改为 DIR|
|   -f FILE  | 指定输入生成文件（默认值为 build.ninja）|
|   -j N     | 以并行方式运行 N 个作业（默认值为 14，派生自可用 CPU）|
|   -k N     | 持续操作，直到 N 个作业失败（默认值为 1）|
|   -l N     | 如果加载平均值大于 N，则不要启动新的作业|
|   -n       | 试运行（不运行命令但像命令行运行成功了一样操作）|
|   -v       | 在生成过程中显示所有命令行|
|   -d MODE  | 启用调试（使用 -d 列表列出模式）|
|   -t TOOL  | 运行次级工具（使用 -t 列表列出次级工具）。 终止顶级选项；有更多标志传递给工具|
|   -w FLAG  | 调整警告（使用-w 列表列出警告）|




