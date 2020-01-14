---
title: 在 Visual Studio 中配置 CMake 调试会话
description: 介绍如何使用 Visual Studio 配置 CMake 调试器设置
ms.date: 01/13/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: ff1de8241c2489e675f82f469f1cf697a72f5034
ms.sourcegitcommit: 275b71219d2a8bd5d78f87e21dd909e9968c2f44
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75946814"
---
# <a name="configure-cmake-debugging-sessions"></a>配置 CMake 调试会话

::: moniker range="vs-2015"

Visual Studio 2017 及更高版本中提供了本机 CMake 支持。

::: moniker-end

::: moniker range=">=vs-2017"

所有可执行的 CMake 目标都显示在“常规”工具栏的“启动项”下拉列表中。 要启动调试会话，只需选择一个调试会话并启动调试程序。

![CMake 启动项下拉列表](media/cmake-startup-item-dropdown.png "CMake 启动项下拉列表")

还可以从解决方案资源管理器启动调试会话。 首先，切换到 "**解决方案资源管理器**" 窗口中的 " **CMake 目标" 视图**。

![CMake 目标视图按钮](media/cmake-targets-view.png  "CMake 目标视图菜单项")

然后，右键单击任何可执行文件，然后选择 "**调试**" 或 "**调试和启动设置**"。 **调试**基于活动配置自动开始调试所选目标。 "**调试" 和 "启动设置**" 将打开 "*启动*" 文件，并为所选目标添加新的 "调试" 配置。

## <a name="customize-debugger-settings"></a>自定义调试器设置

可以*在名为*CMake 的文件中为项目中的任何可执行目标自定义调试器设置。 此文件有三个入口点：

- 从主菜单中选择 **$ {activeDebugTarget} 的 "调试" > 调试和启动设置**，以编辑特定于活动调试目标的调试配置。 如果未选择活动目标，此选项将灰显。

- 在解决方案资源管理器中导航到 "**目标" 视图**。 然后，右键单击调试目标，然后选择 "**调试和启动设置**"，以编辑特定于所选目标的调试配置。

- 右键单击根 Cmakelists.txt，并选择 "**调试和启动设置**"，打开 "**选择调试器**" 对话框。 此对话框允许你添加任何调试配置，但必须手动指定要通过 `projectTarget` 属性调用的 CMake 目标。

若要引用*CMakeSettings*文件中的任何密钥，*请在该*文件的开头加上 `cmake.`。 下面的示例显示一个简单的*启动*文件，该文件将在*CMakeSettings*文件中提取当前所选配置的 `remoteCopySources` 项的值：

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

保存*启动. vs json*文件时，Visual Studio 会在 "**启动项**" 下拉列表中为新名称创建一个条目。 对于任意数量的 CMake 目标，你都可以编辑 "*启动" 和 "json* " 文件来创建多个 "调试" 配置。

## <a name="launchvsjson-reference"></a>启动. 与 json 引用

有很多*启动和 json*属性可支持所有调试方案。 以下属性是所有调试配置（远程和本地）的通用属性：

- `projectTarget`：指定生成项目时要调用的 CMake 目标。 如果在 "**调试" > 调试和启动设置 "$ {activeDebugTarget}** " 或 "**目标" 视图***中输入 "* autopopulates"，则 Visual Studio 会将此属性设置为 ""。

- `program`：远程系统上的程序可执行文件的完整路径。 可在此处使用宏 `${debugInfo.fullTargetPath}`。

- `args`：传递到要调试的程序的命令行参数。

## <a name="launchvsjson-reference-for-remote-linux-projects"></a>对于远程 Linux 项目，启动和 json 引用

以下属性特定于**远程调试配置**。 你还可以[将命令直接发送到 gdb](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)并[启用 MIEngine 日志记录](https://github.com/microsoft/MIEngine/wiki/Logging)。 这些属性使你可以查看发送到 gdb 的命令、执行的输出 gdb 以及每个命令所花费的时间。

- `cwd`：用于查找远程计算机上的依赖项和其他文件的当前工作目录。 可以使用宏 `${debugInfo.defaultWorkingDirectory}`。 除非在*cmakelists.txt*中重写，否则默认值为远程工作区根目录。 此属性仅用于远程配置;`currentDir` 用于为本地项目设置启动应用程序的当前目录。

- `environment`：要添加到具有以下语法的程序的环境的其他环境变量：

```json
  "environment": [
      {
        "name": "ENV1",
        "value": "envvalue1"
      },
      {
        "name": "ENV2",
        "value": "envvalue2"
      }
    ]
```

- `pipeArgs`：传递给管道程序配置连接的命令行参数。 管道程序用于在 Visual Studio 和 gdb 之间中继标准输入/输出。 命令 `${debuggerCommand}` 在远程系统上启动 gdb，并可修改为：

  - 导出 Linux 系统上的环境变量显示值。 在下面的示例中，此值为 `:1`。

  ```json
  "pipeArgs": [
      "/s",
      "${debugInfo.remoteMachineId}",
      "/p",
      "${debugInfo.parentProcessId}",
      "/c",
      "export DISPLAY=:1;${debuggerCommand}",
      "--tty=${debugInfo.tty}"
    ],
  ```

  - 在执行 gdb 之前运行脚本。 确保对脚本设置了 "执行" 权限。

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "/path/to/script.sh;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

- `stopOnEntry`：一个布尔值，指定在启动进程后是否立即中断。 默认值为 false。

- `visualizerFile`：调试此进程时要使用的[natvis 文件](/visualstudio/debugger/create-custom-views-of-native-objects)。 此选项与 gdb 整齐打印不兼容。 设置此属性时，还可以设置 `showDisplayString`。

- `showDisplayString`：指定 `visualizerFile` 时启用显示字符串的布尔值。 将此选项设置为 "`true` 可能会导致调试过程中的性能降低。

- `setupCommands`：要执行的一个或多个 gdb 命令，以设置基础调试器。

- `externalConsole`：一个布尔值，指定是否为调试对象启动控制台。

- `miDebuggerPath`： gdb 的完整路径。 如果未指定，Visual Studio 会首先搜索调试器的路径。

::: moniker-end

::: moniker range="vs-2017"

- `remoteMachineName`：托管 gdb 的远程 Linux 系统和要调试的程序。

::: moniker-end

::: moniker range="vs-2019"

以下属性可用于将**远程生成系统**与**远程调试系统**隔开。 有关详细信息，请参阅[指定用于生成和调试的不同计算机](../linux/deploy-run-and-debug-your-linux-project.md#cmake-projects)。

- `remoteMachineName`：托管 gdb 的远程 Linux 系统和要调试的程序。 此项不需要与*CMakeSettings*中指定的用于生成的远程 Linux 系统匹配。 按**Ctrl + 空格键**以查看[连接管理器](../linux/connect-to-your-remote-linux-computer.md)中存储的所有远程连接的列表。

- `disableDeploy`：指示生成/调试分离是否处于禁用状态。 启用后，此功能允许在两个不同的计算机上进行生成和调试。

- `deployDirectory`：远程调试计算机上的目录（由 `remoteMachineName`指定），可执行文件将复制到该目录。

- `deploy`：高级部署设置的数组。 仅当希望对部署过程进行更精细的控制时，才需要配置这些设置。 默认情况下，只会将调试过程所需的文件部署到远程调试计算机。

  - `sourceMachine`：将从中复制文件或目录的计算机。 按**Ctrl + 空格键**以查看连接管理器中存储的所有远程连接的列表。

  - `targetMachine`：文件或目录将复制到的计算机。 按**Ctrl + 空格键**以查看连接管理器中存储的所有远程连接的列表。

  - `sourcePath`： `sourceMachine`上的文件或目录位置。

  - `targetPath`： `targetMachine`上的文件或目录位置。

  - `deploymentType`：部署类型的说明。 支持 `LocalRemote` 和 `RemoteRemote`。 `LocalRemote` 意味着从本地文件系统复制到*启动*时 `remoteMachineName` 指定的远程系统。 `RemoteRemote` 表示从*CMakeSettings*中指定的远程生成系统复制到在*启动*时指定的不同远程系统。

  - `executable`：指示已部署的文件是否为可执行文件。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="attach-to-a-remote-process"></a>附加到远程进程

可以通过将 `processId` 设置为要将调试器附加到的进程 ID，附加到在 Linux 系统上运行的进程。 有关详细信息，请参阅[使用 GDB 附加到进程疑难解答](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

::: moniker-end

::: moniker range="vs-2019"

## <a name="debug-on-linux-using-gdbserver"></a>使用 gdbserver 在 Linux 上调试

Visual Studio 2019 版本 16.5 Preview 1 或更高版本支持通过 gdbserver 远程调试 CMake 项目。 有关详细信息，请参阅[通过 gdbserver 调试 Linux CMake 项目](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/)。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>另请参阅

[Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)\
[配置 Linux CMake 项目](../linux/cmake-linux-project.md)\
[连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)\
[自定义 CMake 生成设置](customize-cmake-settings.md)\
[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)\
\[部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)
[CMake 预定义配置引用](cmake-predefined-configuration-reference.md)

::: moniker-end
