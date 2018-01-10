---
title: "Visual c + + 中的 CMake 项目 |Microsoft 文档"
ms.custom: 
ms.date: 08/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d38538ce929410782eee7a0a6540bb62a05b7669
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmake-projects-in-visual-c"></a>Visual c + + 中的 CMake 项目
本文假定你熟悉 CMake，用于定义在多个平台运行的生成过程的跨平台的开源工具。  

Visual Studio 用户在不久之前，可以使用 CMake 生成 MSBuild 项目文件，然后情况下，IDE 所消耗的 IntelliSense，浏览，和编译。 从 Visual Studio 2017， **CMake 的 Visual c + + 工具**组件使用"打开文件夹"功能以使 IDE 使用 CMake 项目文件 （如 CMakeLists.txt) 直接为 IntelliSense 和浏览的目的。 如果你使用 Visual Studio 生成器，临时项目文件生成，而且传递到 msbuild.exe，但永远不会为智能感知或浏览目的加载。 

**Visual Studio 2017 版本 15.3**： 忍者和 Visual Studio 生成器提供了支持。

**Visual Studio 2017 版本 15.4**： 有关在 Linux 上的 CMake 添加支持。 有关详细信息，请参阅[配置 Linux CMake 项目](../linux/cmake-linux-project.md)。

## <a name="installing"></a>安装
默认情况下，使用 c + + 工作负荷桌面开发的一部分安装 CMake 的 visual c + + 工具。

![在 c + + 桌面工作负荷的 CMake 组件](media/cmake-install.png)
 
## <a name="ide-integration"></a>IDE 集成
当你选择**文件 |打开 |文件夹**若要打开包含 CMakeLists.txt 文件的文件夹，都会发生以下情况：
- Visual Studio 将添加**CMake**到主菜单中，使用用于查看和编辑 CMake 脚本的命令的菜单项。 
- **解决方案资源管理器**显示的文件夹结构和文件。 
- Visual Studio 运行 CMake.exe 并生成默认值的 CMake 缓存*配置*，这是 x86 调试。 CMake 命令行将显示在**输出窗口**，同时还有其他输出从 CMake。
- 在后台，Visual Studio 启动索引源代码文件，以启用 IntelliSense，浏览信息、 重构，依次类推。 随着工作的同时，Visual Studio 将监视在编辑器中并且也将在磁盘，以使其索引与源同步的更改。 你可以打开包含任意数量的 CMake 项目的文件夹。 Visual Studio 检测，并在工作区中配置所有"root"CMakeLists.txt 文件。 CMake 操作 （配置、 生成、 调试） 以及 c + + IntelliSense 和浏览是适用于你的工作区中的所有 CMake 项目。

![包含多个根 CMake 项目](media/cmake-multiple-roots.png) 

## <a name="building-cmake-projects"></a>生成 CMake 项目
若要生成 CMake 项目，你可选择以下选项：
1. 中的调试下拉菜单中和按选择目标**F5**或单击"运行"按钮。 项目将自动生成第一次，就像与 Visual Studio 解决方案。
2.  CMakeLists.txt 右键单击并从上下文菜单中选择一个生成。 如果您的文件夹结构中有多个目标，你可以选择生成所有或只有一个特定目标，或
  
3. 从主菜单中，选择**生成 |生成解决方案**(**F7**或**Ctrl + Shift + B**) (请确保已选中 CMake 目标状态中**启动项**中下拉列表**常规**工具栏)。

![CMake 生成菜单命令](media/cmake-build-menu.png) 
 
当针对活动配置选择 Visual Studio 生成器时，使用调用 MSBuild.exe`-m -v:minimal`自变量。 若要自定义的生成、 放在 CMakeSettings.json 文件中，可以指定其他命令行自变量传递给生成系统通过`buildCommandArgs`属性：

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```
如你所料，生成结果所示**输出窗口**和**错误列表**。
 
![CMake 生成错误](media/cmake-build-errors.png)

在包含多个生成目标文件夹中，你可以选择上 CMake 菜单或 CMakeLists.txt 上下文菜单，以指定哪些 CMake 目标中，以便生成的生成项目。 按**Ctrl + Shift + B** CMake 生成当前活动文档项目。 

## <a name="debugging-the-project"></a>调试项目
若要调试 CMake 项目，选择所需的配置和按**F5**，或在工具栏中按运行按钮。 如果运行按钮显示"选择启动项"，单击向下箭头并选择你想要运行的目标。 (在 CMake 项目中，"当前文档"选项才的.cpp 文件有效。) 

 ![CMake 运行按钮](media/cmake-run-button.png)

 按**F5**将第一次生成项目，如果前一生成后进行了更改。

## <a name="configuring-cmake-debugging-sessions"></a>配置调试会话的 CMake
常规的工具栏中的启动项目下拉列表中显示了所有可执行 CMake 目标。 若要启动调试会话，只需选择一个，然后启动调试器。

 ![CMake 启动项下拉列表中](media/cmake-startup-item-dropdown.png)

您也可以通过 CMake 菜单启动调试会话。

要自定义项目中任何可执行 CMake 目标的调试器设置，右键单击特定的 CMakeLists.txt 文件，并选择**调试和启动设置**，当您在子菜单中，名为的文件选择 CMake 目标创建 launch.vs.json。 此文件预先填充了 CMake 目标选择了有关的信息，并允许您指定其他参数，如程序自变量或调试器类型。 若要引用 CMakeSettings.json 文件中的任意键，必须使用"cmake。" 在 launch.vs.json。 下面的示例演示当前所选的配置的 CMakeSettings.json 文件中的"remoteCopySources"键的值中提取的简单 launch.vs.json 文件：

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
一旦保存 launch.vs.json 文件，请使用新名称的启动项目下拉列表中创建一个条目。 通过编辑 launch.vs.json 文件，您可以创建许多调试配置，根据需要任意数量的 CMake 目标。

**Visual Studio 2017 版本 15.4**: Launch.vs.json 支持声明的变量中 CMakeSettings.json （见下文）。 它还具有"currentDir"，都将被设置为启动应用程序的当前目录的概念：

```json
{
"type": "default",
"project": "CMakeLists.txt",
"projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```
当你运行应用程序中的值`currentDir`是 

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```
 

## <a name="editing-cmakeliststxt-files"></a>编辑 CMakeLists.txt 文件
若要编辑 CMakeLists.txt 文件，右键单击中的文件**解决方案资源管理器**选择**打开**。 如果对文件进行更改，一个黄色的状态栏将会出现，并且会通知你，IntelliSense 将更新，并提供你取消更新操作的机会。 CMakeLists.txt 有关的信息，请参阅[CMake 文档](https://cmake.org/documentation/)。

  ![CMakeLists.txt 文件编辑](media/cmake-cmakelists.png)

一旦保存该文件，配置步骤将自动再次运行，并在输出窗口中显示信息。 在错误列表或输出窗口中显示了错误和警告。 双击要导航到在 CMakeLists.txt 有问题的行的错误列表中的错误。

  ![CMakeLists.txt 文件错误](media/cmake-cmakelists-error.png)
 
## <a name="cmake_settings"></a>CMake 设置和自定义配置
默认情况下，Visual Studio 提供了六个默认 CMake 配置 （"x86 调试"、"x86 版本"、"x64 调试"、"x64-版"，"Linux 调试"和"Linux 发行版"）。 这些配置定义如何调用 CMake.exe 来创建给定项目的 CMake 缓存。 若要修改这些配置，或创建新的自定义配置，请选择**CMake |更改 CMake 设置**，，然后选择的设置将适用于 CMakeLists.txt 文件。 更改 CMake 设置，还可以在中的文件的上下文菜单**解决方案资源管理器**。 此命令在项目文件夹中创建 CMakeSettings.json 文件。 此文件用于重新创建 CMake 缓存文件，例如后的"清理"操作。 

  ![更改设置的 CMake 主菜单命令](media/cmake-change-settings.png)
 
JSON IntelliSense 可帮助您编辑 CMakeSettings.json 文件：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png)

下面的示例演示可以用作起始点来创建自己的 CMakeSettings.json 中的示例配置：
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
1.  名称： 在 c + + 配置下拉列表中将出现的名称。 此属性的值还用作宏`${name}`指定其他属性值。 有关示例，请参阅 CMakeSettings.json 中的"buildRoot"定义。
2.  生成器： 映射到-G 开关，并指定要使用的生成器。 此属性还可为宏`${generator}`帮助指定其他属性值。 Visual Studio 当前支持以下 CMake 生成器：
    - "忍者"
    - "Visual Studio 14 2015年"
    - "Visual Studio 14 2015 ARM"
    - "Visual Studio 14 2015 Win64"
    - "Visual Studio 15 2017年"
    - "Visual Studio 15 2017 ARM"
    - "Visual Studio 15 2017 Win64"
    - 
忍者旨在实现快速生成的速度，而不是灵活性和函数，因为它被设置为默认值。 但是，某些 CMake 项目可能无法正确构建使用忍者。 如果发生这种情况，你可以指示 CMake 改为生成的 Visual Studio 项目。 

若要指定 Visual Studio 生成器中，打开 CMakeSettings.json 从主菜单中，请选择**CMake |更改 CMake 设置**。 删除"忍者"并键入"V"。 这将激活 IntelliSense，这使您能够选择所需的生成器。
3.  buildRoot： 映射到-DCMAKE_BINARY_DIR 交换机，并指定将在其中创建 CMake 缓存。 如果文件夹不存在，将创建它。
4.  变量： 包含将作为-Dname 获取传递的 CMake 变量的名称和值对 = CMake 的值。 如果你 CMake 项目构建说明指定的任何变量将直接添加到 CMake 缓存文件，建议你添加他们此处相反。
5.  cmakeCommandArgs： 指定你想要将传递给 CMake.exe 任何附加开关。
6.  configurationType： 定义所选的生成器的生成配置类型。 当前支持的值为"调试"、"MinSizeRel"、"发布"和"RelWithDebInfo"。

### <a name="environment-variables"></a>环境变量
CMakeSettings.json 还支持使用环境变量中的任何上述属性。 若要使用的语法是`${env.FOO}`以展开环境变量 %FOO%。
此外可以访问内置宏在此文件中：
- `${workspaceRoot}`– 提供的工作区文件夹的完整路径
- `${workspaceHash}`– 哈希的工作区位置;可用于创建当前工作区 （例如，若要在文件夹路径中使用） 的唯一标识符
- `${projectFile}`– 根 CMakeLists.txt 文件的完整路径
- `${projectDir}`– 根 CMakeLists.txt 文件的文件夹的完整路径
- `${thisFile}`– CMakeSettings.json 文件的完整路径
- `${name}`– 配置的名称
- `${generator}`– 此配置中使用的 CMake 生成器的名称

### <a name="ninja-command-line-arguments"></a>忍者命令行参数

如果未指定目标，生成的默认目标 （请参阅手动）。

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|选项|描述|  
|--------------|------------|  
| -版本  | 打印忍者版本 ("1.7.1")| 
|   -C DIR   | 在执行任何其他操作前更改为 DIR| 
|   -f 文件  | 指定输入的生成文件 [default=build.ninja]| 
|   -j N     | 以并行方式运行 N 作业 [默认值 = 14 中，从可用的 Cpu 派生]| 
|   -k N     | 继续操作直到 N 作业失败 [默认值 = 1]| 
|   -l N     | 如果负载平均值大于 N 无法启动新作业| 
|   -n      | 干运行 （请勿运行命令，但成为成功）| 
|   -v       | 显示在生成过程中的所有命令行| 
|   -d 模式  | 启用调试 （使用-d 列表添加到列表模式）| 
|   -t 工具  | 运行 subtool （使用-t 列表间子工具）。 终止顶级选项;进一步将标志传递给该工具| 
|   -w 标志  | 调整警告 （使用-w 列表间警告）| 


### <a name="inherited-environments-visual-studio-2017-version-155"></a>继承的环境 (Visual Studio 2017 版本 15.5)

CmakeSettings.json 现在支持 inherted 环境。 此功能使您可以创建自定义变量：

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

此字段设置了运行时自动传递到 CMake.exe 的变量。 上面的示例是运行"VS 2017 为开发人员命令提示"一样使用`-arch=amd64 -host_arch=amd64`自变量。

下表显示支持的值和它们的命令行等效项：

|上下文名称|描述|  
|-----------|-----------------|
|vsdev|默认 Visual Studio 环境|
|msvc_x86|编译为 x86 使用 x86 工具|
|msvc_arm| 编译 arm 使用 x86 工具|
|msvc_arm64|针对 ARM64 编译使用 x86 工具|
|msvc_x86_x64|针对 AMD64 编译使用 x86 工具|
|msvc_x64_x64|针对 AMD64 编译使用 64 位工具|
|msvc_arm_x64|为 ARM 使用 64 位工具编译|
|msvc_arm64_x64|针对 ARM64 编译使用 64 位工具|


如果进行了重大更改到 CMakeSettings.json 或 CMakeLists.txt 文件，Visual Studio 自动重新运行 CMake 配置步骤。 如果配置步骤完成且未发生错误，收集的信息将可在 c + + IntelliSense 和语言服务以及在生成和调试操作。

当多个 CMake 项目使用相同的 CMake 配置名称 （例如，x86 调试） 时，所有这些配置并生成 （自己生成根文件夹中） 时选择该配置。 你可以调试来自所有参与该 CMake 配置 CMake 项目的目标。

   ![仅生成 CMake 菜单项](media/cmake-build-only.png)

若要限制生成和调试会话保存到工作区中的项目的子集，替换 CMakeSettings.json 文件中的唯一名称创建新的配置，并将其应用于仅限这些项目。 该配置时选择，IntelliSense，生成，并且调试将仅为那些指定的项目时，才启用。

## <a name="troubleshooting-cmake-cache-errors"></a>CMake 缓存错误故障排除
如果你需要有关 CMake 缓存来诊断问题的状态的详细信息，请打开 CMake 主菜单或 CMakeLists.txt 上下文菜单中的**解决方案资源管理器**运行以下命令之一：
- **查看缓存**在编辑器中的生成根文件夹中打开 CMakeCache.txt 文件。 （对 CMakeCache.txt 此处所做的任何编辑都将被清除如果清除缓存。 若要进行缓存清除后保留的更改，请参阅[CMake 设置和自定义配置](#cmake_settings)本文前面。)
- **打开缓存文件夹**将打开到生成根文件夹资源管理器窗口。  
- **清除缓存**删除生成根文件夹，以便下一步 CMake 配置从清理缓存的步骤开始。
- **生成缓存**强制运行即使 Visual Studio 会将环境最新生成步骤。

