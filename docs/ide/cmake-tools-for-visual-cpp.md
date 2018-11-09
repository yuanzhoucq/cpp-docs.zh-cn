---
title: Visual C++ 中的 CMake 项目
ms.date: 10/18/2018
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 07c32e30aa36d6e59122340da0b1026e7025780d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612493"
---
# <a name="cmake-projects-in-visual-c"></a>Visual C++ 中的 CMake 项目

本文假定你熟悉 CMake，CMake 是一种跨平台开源工具，用于定义在多个平台上运行的生成过程。

在 Visual Studio 2015 中，Visual Studio 用户可使用 [CMake 生成器](https://cmake.org/cmake/help/v3.9/manual/cmake-generators.7.html)生成 MSBuild 项目文件，IDE 之后可将该项目文件用于 IntelliSense、浏览和编译。

从 Visual Studio 2017 开始，“用于 CMake 的 Visual C++ 工具”组件使用“打开文件夹”功能，让 IDE 能够直接将 CMake 项目文件（例如 CMakeLists.txt）用于 IntelliSense 和浏览。 如果使用 Visual Studio 生成器，则会生成一个临时项目文件并将该文件传递给 msbuild.exe，但是绝不会出于 IntelliSense 或浏览目的加载它。

**Visual Studio 2017 版本 15.3**：提供了对 Ninja 和 Visual Studio 生成器的支持。

**Visual Studio 2017 版本 15.4**：添加了对 Linux 版 CMake 的支持。 有关详细信息，请参阅[配置 Linux CMake 项目](../linux/cmake-linux-project.md)。

**Visual Studio 2017 版本 15.5**：添加了对导入现有 CMake 缓存的支持。 Visual Studio 自动提取自定义的变量，并创建一个预填充的 CMakeSettings.json 文件。

Visual Studio 2017 版本 15.7：添加了对禁用自动缓存生成、解决方案资源管理器中的目标视图和单个文件编译的支持。

## <a name="installation"></a>安装

默认情况下，“用于 CMake 的 Visual C++ 工具”作为“使用 C++ 的桌面开发”工作负载的一部分安装。

![C++ 桌面工作负载中的 CMake 组件](media/cmake-install.png)

## <a name="ide-integration"></a>IDE 集成

选择“文件”|“打开”|“文件夹”，打开一个包含 CMakeLists.txt 文件的文件夹时，将发生以下情况：

- Visual Studio 将“CMake”菜单项添加到主菜单，其中包含用于查看和编辑 CMake 脚本的命令。
- 解决方案资源管理器显示文件夹结构和文件。
- Visual Studio 运行 CMake.exe 并生成默认配置的 CMake 缓存，即 x86 调试。 输出窗口中显示 CMake 命令行以及 CMake 的其他输出。  Visual Studio 2017 版本 15.7 及更高版本：可在“工具”|“选项”|“CMake”|“常规”对话框中禁用自动缓存生成。
- 在后台，Visual Studio 开始对源文件编制索引，以启用 IntelliSense、浏览信息和重构等等。 随着工作进行，Visual Studio 监视器在编辑器和磁盘中随之发生变化，以保持其索引与源同步。

可以打开包含任意数量 CMake 项目的文件夹。 Visual Studio 检测并配置工作区中的所有“根”CMakeLists.txt 文件。 CMake 操作（配置、生成、调试）以及 C++ IntelliSense 和浏览可用于工作区中的所有 CMake 项目。

![包含多个根的 CMake 项目](media/cmake-multiple-roots.png)

Visual Studio 2017 版本 15.7 及更高版本：还可以按目标查看经过逻辑组织的项目。 在“解决方案资源管理器”工具栏中，从下拉列表中选择“目标视图”：

![CMake“目标视图”按钮](media/cmake-targets-view.png)

## <a name="import-an-existing-cache"></a>导入现有缓存

导入现有 CMakeCache.txt 文件时，Visual Studio 自动提取自定义的变量，并基于这些变量创建一个预填充的 [CMakeSettings.json](#cmake_settings) 文件。 不会以任何方式修改原始缓存，并且仍可从命令行或者借助用于生成原始缓存的工具或 IDE 使用该原始缓存。 新的 CMakeSettings.json 文件与项目的根 CMakeLists.txt 放在一起。 Visual Studio 基于设置文件生成新的缓存。

Visual Studio 2017 版本 15.7 及更高版本：可在“工具”|“选项”|“CMake”|“常规”对话框中替代自动缓存生成。

并非缓存中的所有内容都会被导入。  生成器和编译器的位置等属性替换为已知适合用于 IDE 的默认值。

### <a name="to-import-an-existing-cache"></a>导入现有缓存

1. 从主菜单中选择“文件”|“打开”|“CMake”：

   ![打开 CMake](media/cmake-file-open.png "“文件”>“打开”>“CMake”")

   “从缓存导入 CMake”向导随即显示。

2. 导航到要导入的 CMakeCache.txt 文件，然后单击“确定”。 “从缓存导入 CMake 项目”向导随即显示：

   ![导入 CMake 缓存](media/cmake-import-wizard.png "打开 CMake 导入缓存向导")

   在向导完成时，可在解决方案资源管理器中看到新的 CMakeCache.txt 文件，位于项目中的根 CMakeLists.txt 文件旁边。

## <a name="building-cmake-projects"></a>生成 CMake 项目

要生成 CMake 项目，可选择执行以下操作：

1. 在“调试”下拉列表中选择目标，并按 F5 或单击“运行”（绿色三角形）按钮。 项目首先自动生成，就像 Visual Studio 解决方案一样。
1. 右键单击 CMakeLists.txt，并从上下文菜单中选择“生成”。 如果在文件夹结构中有多个目标，可以选择生成所有目标或仅生成某个特定目标。
1. 从主菜单中选择“生成”|“生成解决方案”（F7 或 Ctrl+Shift+B）。 请确保已在“常规”工具栏的“启动项”下拉列表中选择了 CMake 目标。

![CMake 生成菜单命令](media/cmake-build-menu.png "CMake 生成命令菜单")

为活动配置选择 Visual Studio 生成器时，可使用 `-m -v:minimal` 参数调用 MSBuild.exe。 要自定义生成，可在 CMakeSettings.json 文件中指定要通过 `buildCommandArgs` 属性传递到生成系统的其他命令行参数：

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```

生成结果按预期显示在“输出窗口”和“错误列表”中。

![CMake 生成错误](media/cmake-build-errors.png "CMake 生成错误")

在包含多个生成目标的文件夹中，可以在“CMake”菜单或“CMakeLists.txt”上下文菜单上选择“生成”项，指定要生成的 CMake 目标。 在 CMake 项目中按 Ctrl+Shift+B 可生成当前活动文档。

## <a name="debug-the-project"></a>调试项目

要调试 CMake 项目，请选择所需配置并按 F5，或按工具栏中的“运行”按钮。 如果“运行”按钮提示“选择启动项”，请选择向下箭头并选择要运行的目标。 （在 CMake 项目中，“当前文档”选项只对 .cpp 文件有效。）

![CMake“运行”按钮](media/cmake-run-button.png "CMake“运行”按钮")

如果在上次生成后进行了更改，则“运行”或“F5”命令会先生成项目。

## <a name="configure-cmake-debugging-sessions"></a>配置 CMake 调试会话

所有可执行的 CMake 目标都显示在“常规”工具栏的“启动项”下拉列表中。 要启动调试会话，只需选择一个调试会话并启动调试程序。

![CMake“启动项”下拉列表](media/cmake-startup-item-dropdown.png "CMake“启动项”下拉列表")

也可以从 CMake 菜单启动调试会话。

要自定义项目中任何可执行 CMake 目标的调试程序设置，请右键单击特定 CMakeLists.txt 文件，并选择“调试和启动设置”。 在子菜单中选择 CMake 目标时，会创建一个名为 launch.vs.json 的文件。 此文件预填充了所选 CMake 目标的相关信息，且允许指定程序参数或调试程序类型等其他参数。 要引用 CMakeSettings.json 文件中的任何键，只需在 launch.vs.json 中 在该键前加上“cmake.”。 下面的示例演示了一个简单的 launch.vs.json 文件，该文件从当前所选配置的 CMakeSettings.json 文件拉取“remoteCopySources”键的值：

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

保存 launch.vs.json 文件后，会立即使用新的名称在“启动项”下拉列表中创建一个条目。 通过编辑 launch.vs.json 文件，可为任意数量的 CMake 目标创建任意数量的调试配置。

**Visual Studio 2017 版本 15.4**：Launch.vs.json 支持在 CMakeSettings.json 中声明的变量（见下文）以及适用于当前所选配置的变量。 它还具有一个名为“currentDir”的键，该键可设置启动的应用的当前目录：

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

运行应用时，`currentDir` 的值类似于以下形式

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

## <a name="editing-cmakeliststxt-files"></a>编辑 CMakeLists.txt 文件

要编辑 CMakeLists.txt 文件，请右键单击“解决方案资源管理器”中的文件，并选择“打开”。 如果对文件进行更改，会显示一个黄色的状态栏，通知用户 IntelliSense 将更新，并且用户可以选择取消该更新操作。 有关 CMakeLists.txt 的详细信息，请参阅 [CMake 文档](https://cmake.org/documentation/)。

   ![CMakeLists.txt 文件编辑](media/cmake-cmakelists.png "CMakeLists.txt 文件编辑")

保存文件后，配置步骤立即自动再次运行，并在“输出”窗口中显示信息。 错误和警告显示在“错误列表”或“输出”窗口中。 双击“错误列表”中的错误可导航到 CMakeLists.txt 中出现问题的行。

   ![CMakeLists.txt 文件错误](media/cmake-cmakelists-error.png "CMakeLists.txt 文件错误")

## <a name="cmake_settings"></a> CMake 设置和自定义配置

默认情况下，Visual Studio 提供六种默认 CMake 配置（“x86-Debug”、“x86-Release”、“x64-Debug”、“x64-Release”、“Linux-Debug”和“Linux-Release”）。 这些配置定义如何调用 CMake.exe 来创建给定项目的 CMake 缓存。 要修改这些配置或新建自定义配置，请选择“CMake”|“更改 CMake 设置”，然后选择要应用设置的 CMakeLists.txt 文件。 还可在“解决方案资源管理器”中的文件上下文菜单上使用“更改 CMake 设置”命令。 此命令在项目文件夹中创建 CMakeSettings.json 文件。 此文件用于重新创建 CMake 缓存文件，例如，在“清除”操作后重新创建。

   ![更改设置的 CMake 主菜单命令](media/cmake-change-settings.png)

JSON IntelliSense 可帮助编辑 CMakeSettings.json 文件：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

下面的示例演示了一个示例配置，可将该配置用作起点，在 CMakeSettings.json 中创建自己的配置：

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```

1. **name**：显示在 C++ 配置下拉列表中的配置名称。 此属性值也可用作宏 `${name}`，用于指定其他属性值。 有关示例，请参阅 CMakeSettings.json 中的 **buildRoot** 定义。

1. **generator**：映射到 -G 开关并指定要使用的生成器。 此属性也可用作宏 `${generator}`，帮助指定其他属性值。 Visual Studio 当前支持下列 CMake 生成器：

    - "Ninja"
    - "Visual Studio 14 2015"
    - "Visual Studio 14 2015 ARM"
    - "Visual Studio 14 2015 Win64"
    - "Visual Studio 15 2017"
    - "Visual Studio 15 2017 ARM"
    - "Visual Studio 15 2017 Win64"

由于 Ninja 旨在加快生成速度，而不是为了提高灵活性和功能，因此它被设为默认生成器。 但是，某些 CMake 项目可能无法使用 Ninja 正确地进行生成。 如果发生这种情况，可以指示 CMake 改为生成 Visual Studio 项目。

要指定一个 Visual Studio 生成器，请通过选择“CMake”|“更改 CMake 设置”从主菜单打开 CMakeSettings.json。 删除“Ninja”并键入“V”。 这可激活 IntelliSense，从而可让用户选择所需生成器。

1. **buildRoot**：映射到 -DCMAKE_BINARY_DIR 开关，并指定要创建 CMake 的位置。 如果文件夹不存在，则会创建一个。

1. **variables**：包含将作为 -D name=value 传递到 CMake 的 CMake 变量的名称/值对。 如果 CMake 项目生成指令指定将任何变量直接添加到 CMake 缓存文件，那么建议改为在这里添加它们。 下面的示例演示如何指定名称/值对：

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    }
  ]
```

1. **cmakeCommandArgs**：指定任何要传递到 CMake.exe 的其他开关。

2. **configurationType**：定义所选生成器的生成配置类型。 当前支持的值为“Debug”、“MinSizeRel”、“Release”和“RelWithDebInfo”。

3. ctestCommandArgs：指定运行测试时传递给 CTest 的其他开关。

4. buildCommandArgs：指定传递给基础生成系统的其他开关。 例如，使用 Ninja 生成器强制输出命令行使用 Ninja 时，传递 -v。

### <a name="environment-variables"></a>环境变量

CMakeSettings.json 还支持使用上述所有属性中的环境变量。 所使用的语法为 `${env.FOO}`，用于展开环境变量 %FOO%。
此外，还可以使用此文件中内置的宏：

- `${workspaceRoot}`：提供工作区文件夹的完整路径
- `${workspaceHash}`：工作区位置的哈希；可用于创建当前工作区的唯一标识符（例如用于文件路径）
- `${projectFile}`：根 CMakeLists.txt 文件的完整路径
- `${projectDir}`：根 CMakeLists.txt 文件的文件夹完整路径
- `${thisFile}`：CMakeSettings.json 文件的完整路径
- `${name}`：配置的名称
- `${generator}`：配置中使用的 CMake 生成器的名称

### <a name="ninja-command-line-arguments"></a>Ninja 命令行参数

如果未指定目标，则生成“默认”目标（请参阅手册）。

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

### <a name="inherited-environments-visual-studio-2017-version-155"></a>继承环境（Visual Studio 2017 版本 15.5）

CMakeSettings.json 现在支持继承环境。 此功能支持：(1) 继承默认环境，以及 (2) 创建在运行时传递给 CMake.exe 的自定义环境变量。

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

上面的示例与运行带有“-arch=amd64 -host_arch=amd64”参数的“适用于 VS 2017 的开发人员命令提示”一样。

下表显示默认值：

|上下文名称|描述|
|-----------|-----------------|
|vsdev|默认的 Visual Studio 环境|
|msvc_x86|使用 x86 工具为 x86 编译|
|msvc_arm| 使用 x86 工具为 ARM 编译|
|msvc_arm64|使用 x86 工具为 ARM64 编译|
|msvc_x86_x64|使用 x86 工具为 AMD64 编译|
|msvc_x64_x64|使用 64 位工具为 AMD64 编译|
|msvc_arm_x64|使用 64 位工具为 ARM 编译|
|msvc_arm64_x64|使用 64 位工具为 ARM64 编译|

### <a name="custom-environment-variables"></a>自定义环境变量

在 CMakeSettings.json 中，可在“环境”属性中以全局形式或按配置自定义环境变量。 下面的示例定义一个全局变量“BuildDir”，该变量在 x86-Debug 和 x64-Debug 配置中继承。 每个配置都使用该变量来指定配置的“buildRoot”属性值。 也请注意每个配置如何使用“inheritEnvironments”属性来指定仅应用于该配置的值。

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

在下一个示例中，x86-Debug 配置定义自己的“BuildDir”属性值，并且该值会替代由全局“BuildDir”属性设置的值，因此“BuildRoot”的计算结果为 `D:\custom-builddir\x86-Debug`。

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
          "BuildDir": "D:\\custom-builddir",
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

## <a name="cmake-configure-step"></a>CMake 配置步骤

如果对 CMakeSettings.json 或 CMakeLists.txt 文件进行了重大更改，Visual Studio 会自动重新运行 CMake 配置步骤。 如果配置步骤正确完成，则可在 C++ IntelliSense 和语言服务以及生成和调试操作中使用所收集的信息。

如果多个 CMake 项目使用相同的 CMake 配置名称（例如 x86-Debug），那么在选择该配置时会配置并生成所有这些项目（在其自己的生成根文件夹中）。 可以调试参与该 CMake 配置的所有 CMake 项目中的目标。

   ![CMake“仅生成”菜单项](media/cmake-build-only.png "CMake“仅生成”菜单项")

要将生成和调试会话限制在工作区中的项目子集内，请在 CMakeSettings.json 文件中用唯一名称新建一个配置，并仅将该配置应用于这些项目。 如果选择了该配置，则仅为这些特定项目启用 IntelliSense 以及生成和调试命令。

## <a name="troubleshooting-cmake-cache-errors"></a>排查 CMake 缓存错误

如果需要有关 CMake 缓存状态的详细信息来诊断问题，请打开“CMake”主菜单或“解决方案资源管理器”中的“CMakeLists.txt”上下文菜单，运行下面的某个命令：

- **查看缓存**：从编辑器中的生成根文件夹打开 CMakeCache.txt 文件。 （如果清除缓存，则将擦除在此处对 CMakeCache.txt 进行的任何编辑。 要在清除缓存后依然保留更改，请参阅本文前面所述的 [CMake 设置和自定义配置](#cmake_settings)。）

- **打开缓存文件夹**：打开生成根文件夹的资源管理器窗口。

- **清理缓存**：删除生成根文件夹，使下一个 CMake 配置步骤从清理缓存开始。

- **生成缓存**：即使 Visual Studio 认为环境是最新的，也强制运行生成步骤。

Visual Studio 2017 版本 15.7 及更高版本：可在“工具”|“选项”|“CMake”|“常规”对话框中禁用自动缓存生成。

## <a name="single-file-compilation"></a>单个文件编译

Visual Studio 2017 版本 15.7 及更高版本：要在 CMake 项目中编译单个文件，可在解决方案资源管理器中右键单击该文件，然后选择“编译”。 通过使用 CMake 主菜单，还可编译当前在编辑器中打开的文件：

![CMake 单个文件编译](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>从命令行运行 CMake
如果已从 Visual Studio 安装程序安装 CMake，可以通过执行以下步骤从命令行运行它：

1. 运行适当的 vsdevcmd.bat (x86/x64)。 有关详细信息，请参阅[基于命令行生成](../build/building-on-the-command-line.md)。
1. 切换到输出文件夹。
1. 运行 CMake 以生成/配置应用程序。

