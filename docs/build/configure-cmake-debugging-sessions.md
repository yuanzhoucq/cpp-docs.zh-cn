---
title: 在 Visual Studio 中配置 CMake 调试会话
description: 描述如何使用可视化工作室配置 CMake 调试器设置。
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 8364e5b3dd3316a4ed7e754a104a14373040aa6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328815"
---
# <a name="configure-cmake-debugging-sessions"></a>配置 CMake 调试会话

::: moniker range="vs-2015"

本机 CMake 支持可在 Visual Studio 2017 及更高版本提供。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end

::: moniker range=">=vs-2017"

所有可执行的 CMake 目标都显示在“常规”工具栏的“启动项”下拉列表中********。 选择一个启动调试会话并启动调试器。

![CMake 启动项下拉列表](media/cmake-startup-item-dropdown.png "CMake 启动项下拉列表")

您还可以从解决方案资源管理器启动调试会话。 首先，在**解决方案资源管理器**窗口中切换到 **"CMake 目标视图**"。

![CMake“目标视图”按钮](media/cmake-targets-view.png  "CMake 目标 查看菜单项")

然后，右键单击可执行文件并选择**调试**。 此命令根据活动配置自动开始调试所选目标。

## <a name="customize-debugger-settings"></a>自定义调试器设置

您可以自定义项目中任何可执行的 CMake 目标的调试器设置。 它们位于项目根目录的*`.vs`* 文件夹中，位于一个名为 *"启动.vs.json"* 的配置文件中。 启动配置文件在大多数调试方案中都很有用，因为您可以配置和保存调试设置详细信息。 此文件有三个入口点：

- **调试菜单：** 从主菜单**中选择"调试>调试和启动设置[活动调试目标]，** 以自定义特定于活动调试目标的调试配置。 如果未选择调试目标，则此选项将灰显。

![调试菜单入口点](media/cmake-debug-menu.png "调试菜单入口点")

- **目标视图：** 导航到解决方案资源管理器**中的目标视图**。 然后，右键单击调试目标并选择 **"添加调试配置**"以自定义特定于所选目标的调试配置。

![目标视图入口点](media/cmake-targets-add-debug-configuration.png "目标视图入口点")

- **根组列表.txt：** 右键单击根*CMakelists.txt*并选择 **"添加调试配置**"以打开 **"选择调试器"** 对话框。 该对话框允许您添加*任何类型的*调试配置，但您必须手动指定通过`projectTarget`属性调用的 CMake 目标。

![选择调试器对话框](media/cmake-select-a-debugger.png "选择调试器对话框")

您可以编辑*启动.vs.json*文件，为任意数量的 CMake 目标创建调试配置。 保存文件时，Visual Studio 会在 **"启动项目"** 下拉列表中为每个新配置创建一个条目。

## <a name="reference-keys-in-cmakesettingsjson"></a>CMakeSettings.json 中的参考键

要引用*CMakeSettings.json*文件中的任何键，在`cmake.`*启动*中准备它。 下面的示例显示了一个简单的*启动.vs.json*文件，该文件在`remoteCopySources`*CMakeSettings.json*文件中拉取当前所选配置的密钥的值：

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

*CMakeSettings.json*中定义的`${env.VARIABLE_NAME}`**环境变量**也可以用于启动. vs.json 使用语法 。 在 Visual Studio 2019 版本 16.4 及更高版本中，调试目标将使用您在*CMakeSettings.json*中指定的环境自动启动。 可以通过将环境变量设置为**null**来取消设置环境变量。

## <a name="launchvsjson-reference"></a>启动.vs.json 参考

有许多*启动.vs.json*属性来支持您的所有调试方案。 以下属性是所有调试配置（远程配置和本地配置）共有的：

- `projectTarget`：指定生成项目时要调用的 CMake 目标。 如果从**调试菜单**或**目标视图**输入*启动.vs.json，Visual* Studio 会自动填充此属性。 此值必须与**启动项**下拉列表中列出的现有调试目标的名称匹配。

- `env`：使用语法添加的其他环境变量：

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`：命令行参数传递给程序以进行调试。

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>启动.vs.json 远程项目和 WSL 参考

在 Visual Studio 2019 版本 16.6 中，`type: cppgdb`我们添加了新的调试配置，以简化远程系统和 WSL 上的调试。 仍然支持 的旧`type: cppdbg`调试配置。

### <a name="configuration-type-cppgdb"></a>配置类型`cppgdb`

- `name`：用于标识**启动项**下拉列表中的配置的友好名称。
- `project`：指定项目文件的相对路径。 通常，调试 CMake 项目时不需要更改此路径。
- `projectTarget`：指定生成项目时要调用的 CMake 目标。 如果从**调试菜单**或**目标视图**输入*启动.vs.json，Visual* Studio 会自动填充此属性。 此目标值必须与**启动项**下拉列表中列出的现有调试目标的名称匹配。
- `debuggerConfiguration`指示要使用的调试默认值集。 在 Visual Studio 2019 版 16.6`gdb`中，唯一有效的选项是 。 早期版本也支持`gdbserver`。
- `args`：在启动时将命令行参数传递给正在调试的程序。
- `env`：传递给正在调试的程序的其他环境变量。 例如，`{"DISPLAY": "0.0"}` 。
- `processID`：要附加到的 Linux 进程 ID。 仅在附加到远程进程时使用。 有关详细信息，请参阅使用[GDB 附加到进程的疑难解答](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

#### <a name="additional-options-for-the-gdb-configuration"></a>`gdb`配置的其他选项

- `program`：默认值为`"${debugInfo.fullTargetPath}"`。 要调试的应用程序的 Unix 路径。 仅当与生成或部署位置中的目标可执行文件不同时，才需要。
- `remoteMachineName`：默认值为`"${debugInfo.remoteMachineName}"`。 承载要调试的程序的远程系统的名称。 仅当与生成系统不同时才需要。 [连接管理器](../linux/connect-to-your-remote-linux-computer.md)中必须具有现有条目。 按**Ctrl+空间**以查看所有现有远程连接的列表。
- `cwd`：默认值为`"${debugInfo.defaultWorkingDirectory}"`。 运行远程系统上`program`目录的 Unix 路径。 该目录必须存在。
- `gdbpath`：默认值为`/usr/bin/gdb`。 用于调试的完整`gdb`Unix 路径。 仅当使用 的`gdb`自定义版本 时才需要 。
- `preDebugCommand`：在调用`gdb`之前立即运行的 Linux 命令。 `gdb`直到命令完成才能启动。 可以使用 选项在执行 之前运行脚本`gdb`。

#### <a name="deployment-options"></a>部署选项

使用以下选项将生成计算机（在 CMakeSettings.json 中定义）与远程调试计算机分开。

- `remoteMachineName`：远程调试机。 仅当与生成计算机不同时才需要。 [连接管理器](../linux/connect-to-your-remote-linux-computer.md)中必须具有现有条目。 按**Ctrl+空间**以查看所有现有远程连接的列表。
- `disableDeploy`：默认值为`false`。 指示是否禁用生成/调试分离。 当`false`时，此选项允许在两个单独的计算机上进行生成和调试。
- `deployDirectory`：可执行文件复制到的目录`remoteMachineName`的完整 Unix 路径。
- `deploy`：高级部署设置的数组。 仅当需要更精细地控制部署过程时，才需要配置这些设置。 默认情况下，只有调试过程所需的文件才会部署到远程调试计算机。
  - `sourceMachine`：从中复制文件或目录的计算机。 按**Ctrl_Space**以查看存储在连接管理器中的所有远程连接的列表。 在 WSL 上本机生成时，将忽略此选项。
  - `targetMachine`：将文件或目录复制到的计算机。 按**Ctrl_Space**以查看存储在连接管理器中的所有远程连接的列表。
  - `sourcePath`：上的文件`sourceMachine`或目录位置。
  - `targetPath`：上的文件`targetMachine`或目录位置。
  - `deploymentType`：部署类型的说明。 `LocalRemote`并且`RemoteRemote`受支持。 `LocalRemote`表示从本地文件系统复制到`remoteMachineName`*启动*中指定的远程系统。 `RemoteRemote`意味着从*CMakeSettings.json*中指定的远程生成系统复制到*启动*中指定的不同远程系统。
  - `executable`：指示部署的文件是否是可执行文件。

### <a name="execute-custom-gdb-commands"></a>执行自定义`gdb`命令

Visual Studio 支持执行`gdb`自定义命令，以便直接与基础调试器进行交互。 有关详细信息，请参阅[执行自定义`gdb`lldb 命令](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)。

### <a name="enable-logging"></a>启用日志记录

启用 MIEngine 日志记录以查看发送到哪些命令`gdb`，输出`gdb`返回什么，以及每个命令需要多长时间。 [了解详细信息](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>配置类型`cppdbg`

使用配置类型在远程系统或 WSL 上进行调试时，`cppdbg`可以使用以下选项。 在 Visual Studio 2019 版 16.6`cppgdb`或更高版本中，建议配置类型。

- `name`：用于标识**启动项**下拉列表中的配置的友好名称。

- `project`：指定项目文件的相对路径。 通常，调试 CMake 项目时不需要更改此值。

- `projectTarget`：指定生成项目时要调用的 CMake 目标。 如果从**调试菜单**或**目标视图**输入*启动.vs.json，Visual* Studio 会自动填充此属性。 此值必须与**启动项**下拉列表中列出的现有调试目标的名称匹配。

- `args`：在启动时将命令行参数传递给正在调试的程序。

- `processID`：要附加到的 Linux 进程 ID。 仅在附加到远程进程时使用。 有关详细信息，请参阅使用[GDB 附加到进程的疑难解答](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

- `program`：默认值为`"${debugInfo.fullTargetPath}"`。 要调试的应用程序的 Unix 路径。 仅当与生成或部署位置中的目标可执行文件不同时，才需要。

- `remoteMachineName`：默认值为`"${debugInfo.remoteMachineName}"`。 承载要调试的程序的远程系统的名称。 仅当与生成系统不同时才需要。 [连接管理器](../linux/connect-to-your-remote-linux-computer.md)中必须具有现有条目。 按**Ctrl+空间**以查看所有现有远程连接的列表。

- `cwd`：默认值为`"${debugInfo.defaultWorkingDirectory}"`。 运行远程系统上`program`目录的完整 Unix 路径。 该目录必须存在。

- `environment`：传递给正在调试的程序的其他环境变量。 例如，

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

- `pipeArgs`： 传递给管道程序以配置连接的命令行参数数组。 管道程序用于在 Visual Studio 和`gdb`之间中继标准输入/输出。 调试 CMake 项目时 **，不需要自定义**大多数此阵列。 例外情况是在远程系统上`${debuggerCommand}`启动`gdb`的 。 它可以修改为：

  - 在 Linux 系统上导出环境变量 DISPLAY 的值。 在下面的示例中，此值为`:1`。

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

  - 在执行 之前运行脚本`gdb`。 确保在脚本上设置了执行权限。

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

- `stopOnEntry`：指定在进程启动后立即是否中断的布尔。 默认值为 false。

- `visualizerFile`：调试此过程时要使用[.natvis 文件](/visualstudio/debugger/create-custom-views-of-native-objects)。 此选项与漂亮的打印不`gdb`兼容。 在设置`showDisplayString`此属性时也设置。

- `showDisplayString`：指定 时`visualizerFile`启用显示字符串的布尔。 将此选项设置为`true`可能会导致调试期间性能降低。

- `setupCommands`：要执行的`gdb`一个或多个命令，以设置基础调试器。

- `miDebuggerPath`： 到`gdb`的完整路径。 未指定时，可视化工作室将首先搜索 PATH 以搜索调试器。

- 最后，为`cppgdb`配置类型定义的所有部署选项也可以由`cppdbg`配置类型使用。

### <a name="debug-using-gdbserver"></a>使用调试`gdbserver`

您可以将`cppdbg`配置配置为使用`gdbserver`调试。 您可以在 Microsoft C++ 团队博客文章[使用 调试 Linux CMake 项目`gdbserver`](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/)中找到更多详细信息和启动配置示例。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>另请参阅

[在视觉工作室中制作项目](cmake-projects-in-visual-studio.md)\
[配置 Linux CMake 项目](../linux/cmake-linux-project.md)\
[连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)\
[自定义"制作"构建设置](customize-cmake-settings.md)\
[配置"制作"调试会话](configure-cmake-debugging-sessions.md)\
[部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 预定义配置引用](cmake-predefined-configuration-reference.md)

::: moniker-end
