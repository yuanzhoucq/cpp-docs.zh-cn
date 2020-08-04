---
title: 在 Visual Studio 中配置 CMake 调试会话
description: 介绍如何使用 Visual Studio 配置 CMake 调试器设置。
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: cc80827458ba7cb61339ec3a36f227747780a47c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224079"
---
# <a name="configure-cmake-debugging-sessions"></a>配置 CMake 调试会话

::: moniker range="vs-2015"

本机 CMake 支持在 Visual Studio 2017 及更高版本中提供。 若要查看这些版本的文档，请将本文的 Visual Studio“版本”选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面上目录表的顶部。

::: moniker-end

::: moniker range=">=vs-2017"

所有可执行的 CMake 目标都显示在“常规”工具栏的“启动项”下拉列表中 。 选择一个以启动调试会话并启动调试器。

![CMake 启动项下拉菜单](media/cmake-startup-item-dropdown.png "CMake 启动项下拉菜单")

还可以从解决方案资源管理器启动调试会话。 首先，切换到“解决方案资源管理器”窗口中的“CMake 目标视图”。

![“CMake 目标视图”按钮](media/cmake-targets-view.png  "CMake 目标视图菜单项")

然后，右键单击一个可执行文件并选择“调试”。 此命令基于活动配置自动开始调试所选目标。

## <a name="customize-debugger-settings"></a>自定义调试器设置

可以为项目中的任何可执行 CMake 目标自定义调试器设置。 它们位于名为 launch.vs.json 的配置文件中，该文件位于项目根的 `.vs` 文件夹中。 启动配置文件在大多数调试方案中非常有用，因为你可以配置和保存调试设置详细信息。 此文件有三个入口点：

- “调试”菜单：从主菜单中选择“调试”>“${activeDebugTarget} 的调试和启动设置”，以自定义特定于活动调试目标的调试配置。 如果尚未选择调试目标，则此选项将灰显。

![“调试”菜单入口点](media/cmake-debug-menu.png "“调试”菜单入口点")

- 目标视图：在解决方案资源管理器，导航到“目标视图”。 然后，右键单击一个调试目标并选择“添加调试配置”以自定义特定于所选目标的调试配置。

![目标视图入口点](media/cmake-targets-add-debug-configuration.png "目标视图入口点")

- 根 CMakeLists.txt：右键单击根 CMakeLists.txt，然后选择“添加调试配置”以打开“选择调试程序”对话框。 此对话框使你可以添加任何类型的调试配置，但必须手动指定要通过 `projectTarget` 属性调用的 CMake 目标。

![“选择调试程序”对话框](media/cmake-select-a-debugger.png "“选择调试程序”对话框")

可以编辑 launch.vs.json 文件，为任意数量的 CMake 目标创建调试配置。 保存该文件时，Visual Studio 会在“启动项”下拉菜单中为每个新配置创建一个条目。

## <a name="reference-keys-in-cmakesettingsjson"></a>引用 CMakeSettings.json 中的键

若要引用 CMakeSettings.json 文件中的任何键，请在 launch.vs.json 中将 `cmake.` 追加到该键前面。 下面的示例演示了一个简单的 launch.vs.json 文件，该文件从当前所选配置的 CMakeSettings.json 文件拉取 `remoteCopySources` 键的值：

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

CMakeSettings.json 中定义的环境变量也可以通过语法 `${env.VARIABLE_NAME}` 在 launch.vs.json 中使用。 在 Visual Studio 2019 版本 16.4 及更高版本中，调试目标将使用在 CMakeSettings.json 中指定的环境自动启动。 可以通过将环境变量设置为 null 来取消设置该变量。

## <a name="launchvsjson-reference"></a>Launch.vs.json 参考

有许多 launch.vs.json 属性可支持所有调试方案。 以下属性是所有调试配置（远程和本地）的通用属性：

- `projectTarget`：指定在生成项目时要调用的 CMake 目标。 如果从“调试菜单”或“目标视图”输入 launch.vs.json，则 Visual Studio 会自动填充此属性。 此值必须与“启动项”下拉菜单中列出的现有调试目标的名称匹配。

- `env`：要使用以下语法添加的其他环境变量：

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`：传递给要调试的程序的命令行参数。

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>针对远程项目和 WSL 的 Launch.vs.json 参考

在 Visual Studio 2019 版本 16.6 中，我们添加了一个 `type: cppgdb` 的新调试配置，用于在远程系统和 WSL 上简化调试。 仍支持 `type: cppdbg` 的旧调试配置。

### <a name="configuration-type-cppgdb"></a>配置类型 `cppgdb`

- `name`：用于在“启动项”下拉菜单中标识配置的易记名称。
- `project`：指定项目文件的相对路径。 通常，调试 CMake 项目时不需要更改此路径。
- `projectTarget`：指定在生成项目时要调用的 CMake 目标。 如果从“调试菜单”或“目标视图”输入 launch.vs.json，则 Visual Studio 会自动填充此属性。 此目标值必须与“启动项”下拉菜单中列出的现有调试目标的名称匹配。
- `debuggerConfiguration`：指示要使用的一组调试默认值。 在 Visual Studio 2019 版本 16.6 中，唯一有效的选项是 `gdb`。 Visual Studio 2019 版本 16.7 或更高版本也支持 `gdbserver`。
- `args`：在启动时传递给所调试的程序的命令行参数。
- `env`：传递给所调试的程序的其他环境变量。 例如 `{"DISPLAY": "0.0"}`。
- `processID`：要附加到的 Linux 进程 ID。 仅当附加到远程进程时才使用。 有关详细信息，请参阅[有关使用 GDB 附加到进程的疑难解答](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

#### <a name="additional-options-for-the-gdb-configuration"></a>`gdb` 配置的其他选项

- `program`：默认为 `"${debugInfo.fullTargetPath}"`。 要调试的应用程序的 Unix 路径。 仅当与生成或部署位置中的目标可执行文件不同时才需要。
- `remoteMachineName`：默认为 `"${debugInfo.remoteMachineName}"`。 承载要调试的程序的远程系统的名称。 仅当与生成系统不同时才需要。 必须在[连接管理器](../linux/connect-to-your-remote-linux-computer.md)中具有现有条目。 按 Ctrl+空格键可查看所有现有远程连接的列表。
- `cwd`：默认为 `"${debugInfo.defaultWorkingDirectory}"`。 远程系统上运行 `program` 的目录的 Unix 路径。 该目录必须存在。
- `gdbpath`：默认为 `/usr/bin/gdb`。 用于调试的 `gdb` 的完整 Unix 路径。 仅当使用 `gdb` 的自定义版本时才需要。
- `preDebugCommand`：恰好在调用 `gdb` 之前运行的 Linux 命令。 `gdb` 在该命令完成之前不会启动。 可以使用该选项在执行 `gdb` 之前运行脚本。

#### <a name="additional-options-allowed-with-the-gdbserver-configuration-167-or-later"></a>允许与 `gdbserver` 配置一起使用的其他选项（16.7 或更高版本）

- `program`：默认为 `"${debugInfo.fullTargetPath}"`。 要调试的应用程序的 Unix 路径。 仅当与生成或部署位置中的目标可执行文件不同时才需要。
- `remoteMachineName`：默认为 `"${debugInfo.remoteMachineName}"`。 承载要调试的程序的远程系统的名称。 仅当与生成系统不同时才需要。 必须在[连接管理器](../linux/connect-to-your-remote-linux-computer.md)中具有现有条目。 按 Ctrl+空格键可查看所有现有远程连接的列表。
- `cwd`：默认为 `"${debugInfo.defaultWorkingDirectory}"`。 远程系统上运行 `program` 的目录的完整 Unix 路径。 该目录必须存在。
- `gdbPath`：默认为 `${debugInfo.vsInstalledGdb}`。 用于调试的 `gdb` 的完整 Windows 路径。 默认为与“使用 C/C++ 的 Linux 开发”工作负载一起安装的 `gdb`。
- `gdbserverPath`：默认为 `usr/bin/gdbserver`。 用于调试的 `gdbserver` 的完整 Unix 路径。
- `preDebugCommand`：紧接在启动 `gdbserver` 之前运行的 Linux 命令。 `gdbserver` 在该命令完成之前不会启动。

#### <a name="deployment-options"></a>部署选项

使用以下选项可将生成计算机（在 CMakeSettings.json 中定义）与远程调试计算机分隔开来。

- `remoteMachineName`：远程调试计算机。 仅当与生成计算机不同时才需要。 必须在[连接管理器](../linux/connect-to-your-remote-linux-computer.md)中具有现有条目。 按 Ctrl+空格键可查看所有现有远程连接的列表。
- `disableDeploy`：默认为 `false`。 指示是否禁用生成/调试分隔。 如果为 `false`，此选项允许在两台不同的计算机上进行生成和调试。
- `deployDirectory`：`remoteMachineName` 上将可执行文件复制到其中的目录的完整 Unix 路径。
- `deploy`：高级部署设置数组。 仅当要对部署过程进行更精细的控制时，才需要配置这些设置。 默认情况下，只会将要调试的进程所需的文件部署到远程调试计算机。
  - `sourceMachine`：从中复制文件或目录的计算机。 按 Ctrl+空格键可查看连接管理器中存储的所有远程连接的列表。 在 WSL 上进行本机生成时，将忽略此选项。
  - `targetMachine`：将文件或目录复制到其中的计算机。 按 Ctrl+空格键可查看连接管理器中存储的所有远程连接的列表。
  - `sourcePath`：`sourceMachine` 上的文件或目录位置。
  - `targetPath`：`targetMachine` 上的文件或目录位置。
  - `deploymentType`：部署类型的说明。 `LocalRemote` 和 `RemoteRemote` 受支持。 `LocalRemote` 表示从本地文件系统复制到 launch.vs.json 中的 `remoteMachineName` 指定的远程系统。 `RemoteRemote` 表示从 CMakeSettings.json 中指定的远程生成系统复制到 launch.vs.json 中指定的不同远程系统。
  - `executable`：指示部署的文件是否为可执行文件。

### <a name="execute-custom-gdb-commands"></a>执行自定义 `gdb` 命令

Visual Studio 支持执行自定义 `gdb` 命令，以便直接与底层调试器交互。 有关详细信息，请参阅[执行自定义 `gdb` lldb 命令](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)。

### <a name="enable-logging"></a>启用日志记录

启用 MIEngine 日志记录，以查看发送到 `gdb` 的命令、`gdb` 返回的输出以及每个命令所花费的时间。 [了解更多信息](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>配置类型 `cppdbg`

使用 `cppdbg` 配置类型在远程系统或 WSL 上进行调试时，可以使用以下选项。 在 Visual Studio 2019 版本 16.6 或更高版本中，建议使用配置类型 `cppgdb`。

- `name`：用于在“启动项”下拉菜单中标识配置的易记名称。

- `project`：指定项目文件的相对路径。 通常，调试 CMake 项目时不需要更改此值。

- `projectTarget`：指定在生成项目时要调用的 CMake 目标。 如果从“调试菜单”或“目标视图”输入 launch.vs.json，则 Visual Studio 会自动填充此属性。 此值必须与“启动项”下拉菜单中列出的现有调试目标的名称匹配。

- `args`：在启动时传递给所调试的程序的命令行参数。

- `processID`：要附加到的 Linux 进程 ID。 仅当附加到远程进程时才使用。 有关详细信息，请参阅[有关使用 GDB 附加到进程的疑难解答](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

- `program`：默认为 `"${debugInfo.fullTargetPath}"`。 要调试的应用程序的 Unix 路径。 仅当与生成或部署位置中的目标可执行文件不同时才需要。

- `remoteMachineName`：默认为 `"${debugInfo.remoteMachineName}"`。 承载要调试的程序的远程系统的名称。 仅当与生成系统不同时才需要。 必须在[连接管理器](../linux/connect-to-your-remote-linux-computer.md)中具有现有条目。 按 Ctrl+空格键可查看所有现有远程连接的列表。

- `cwd`：默认为 `"${debugInfo.defaultWorkingDirectory}"`。 远程系统上运行 `program` 的目录的完整 Unix 路径。 该目录必须存在。

- `environment`：传递给所调试的程序的其他环境变量。 例如，应用于对象的

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

- `pipeArgs`：传递给管道程序配置连接的命令行参数数组。 管道程序用于在 Visual Studio 与 `gdb` 之间中继标准输入/输出。 调试 CMake 项目时，此数组中的大部分内容不需要自定义。 例外情况是 `${debuggerCommand}`，它会在远程系统上启动 `gdb`。 可以为实现以下目的而修改它：

  - 导出 Linux 系统上的环境变量 DISPLAY 的值。 在下面的示例中，此值为 `:1`。

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

  - 在执行 `gdb` 之前运行脚本。 确保对脚本设置了执行权限。

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

- `visualizerFile`：调试此进程时要使用的 [.natvis 文件](/visualstudio/debugger/create-custom-views-of-native-objects)。 此选项与 `gdb` 整齐打印不兼容。 设置此属性时，还需设置 `showDisplayString`。

- `showDisplayString`：一个布尔值，在指定 `visualizerFile` 时启用显示字符串。 将此选项设置为 `true` 可能会导致调试期间性能下降。

- `setupCommands`：要执行的一个或多个 `gdb` 命令，用于设置底层调试器。

- `miDebuggerPath`：`gdb` 的完整路径。 未指定时，Visual Studio 会首先对调试器搜索 PATH。

- 最后，`cppdbg` 配置类型也可以使用为 `cppgdb` 配置类型定义的所有部署选项。

### <a name="debug-using-gdbserver"></a>使用 `gdbserver` 进行调试

可以配置 `cppdbg` 配置以便使用 `gdbserver` 进行调试。 可以在 Microsoft C++ 团队博客文章[使用 `gdbserver` 调试 Linux CMake 项目](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/)中找到更多详细信息和示例启动配置。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>请参阅

[Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)\
[配置 Linux CMake 项目](../linux/cmake-linux-project.md)\
[连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)\
[自定义 CMake 生成设置](customize-cmake-settings.md)\
[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)\
\[部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)
[CMake 预定义配置引用](cmake-predefined-configuration-reference.md)

::: moniker-end
