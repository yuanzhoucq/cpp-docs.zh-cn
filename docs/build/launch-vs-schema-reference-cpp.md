---
title: 启动.vs.json 架构参考 （C++）
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: ff4713642ab95a9bbc31f1a06236de459e53f9c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323054"
---
# <a name="launchvsjson-schema-reference-c"></a>启动.vs.json 架构参考 （C++）

使用*启动.vs.json*文件配置调试参数。 创建文件。 右键单击**解决方案资源管理器**中的可执行文件，然后选择**调试和启动设置**。 选择与项目最匹配的选项，然后根据需要使用以下属性修改配置。 有关调试 CMake 项目的详细信息，请参阅[配置 CMake 调试会话](/cpp/build/configure-cmake-debugging-sessions)。

## <a name="default-properties"></a>默认属性

||||
|-|-|-|
|**属性**|**Type**|**说明**|
|`name`|字符串|在调试目标下拉列表中指定条目的名称。|
|`type`|字符串|指定项目是 dll 还是 .exe（默认值为 .exe）|
|`project`|字符串|指定项目文件的相对路径。|
|`projectTarget`|字符串|指定生成`project`时调用的可选目标。 这`projectTarget`必须已经存在，并且与**调试目标**下拉列表中的名称匹配。|
|`debugType`|字符串|根据代码类型（本机、托管或混合）指定调试模式。 除非设置了此参数，否则将自动检测到此参数。 允许的值："本机"、"托管"、"混合"。|
|`inheritEnvironments`|array|指定从多个源继承的一组环境变量。 您可以在文件（如*CMakeSettings.json 或* *CppProperties.json）* 中定义一些变量，并使它们可用于调试上下文。  **Visual Studio 16.4：**： 使用`env.VARIABLE_NAME`语法根据每个目标指定环境变量。 要取消设置变量，将其设置为"null"。|
|`args`|array|指定传递给启动程序的命令行参数。|
|`currentDir`|字符串|指定生成目标的完整目录路径。 除非设置了此参数，否则将自动检测到此参数。|
|`noDebug`|boolean|指定是否调试启动的程序。 如果未指定此参数`false`的默认值。|
|`stopOnEntry`|boolean|指定在启动进程并附加调试器时是否立即中断。 此参数的默认值为`false`。|
|`remoteMachine`|字符串|指定启动程序的远程计算机的名称。|
|`env`|array| 指定自定义环境变量的键值列表。 env：{"我的恩夫"："米瓦尔"。|
|`portName`|字符串|指定附加到正在运行的进程时的端口名称。|
|`buildConfigurations`|array| 指定要应用配置的生成模式的名称的键值对。 例如，`Debug`或`Release`和根据所选生成模式要使用的配置。

## <a name="c-linux-properties"></a>C++ Linux 属性

||||
|-|-|-|
|**属性**|**Type**|**说明**|
|`program`|字符串|远程计算机上程序可执行的完整路径。 使用 CMake 时，`${debugInfo.fullTargetPath}`宏可用作此字段的值。|
|`processId`|integer|将调试器附加到的可选进程 ID。|
|`sourceFileMap`|对象 (object)|传递给调试引擎的可选源文件映射。 格式： `{ "\<Compiler source location>": "\<Editor source location>" }` `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`或 。 示例：`{ "/home/user/foo": "C:\\foo" }` 或 `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`。 请参阅[源文件映射选项](#source_file_map_options)。|
|`additionalProperties`|字符串|源文件映射选项之一。 （请参阅下文。）|
|`MIMode`|字符串|指示 MIDebugEngine 将连接到的启用 MI 控制台调试器的类型。 允许的值是"gdb"，"lldb"。|
|`args`|array|传递给程序的命令行参数。|
|`environment`|array|要添加到程序环境的环境变量。 示例： [ " 名称"："鱿鱼" " 值"："clam" = [ ]|
|`targetArchitecture`|字符串|调试器的体系结构。 除非设置了此参数，否则将自动检测到此参数。 允许的值是 x86、手臂、臂 64、哑剧、x64、amd64、x86_64。|
|`visualizerFile`|字符串|.natvis 文件，用于调试此过程时。 此选项与 GDB 漂亮打印不兼容。 如果使用此设置，请参阅"显示显示字符串"。|
|`showDisplayString`|boolean|指定可视化工具文件时，ShowDisplayString 将启用显示字符串。 启用此选项可能会导致调试期间性能降低。|
|`remoteMachineName`|字符串|承载 gdb 和要调试的程序的远程 Linux 计算机。 使用连接管理器添加新的 Linux 计算机。 使用 CMake 时，`${debugInfo.remoteMachineName}`宏可用作此字段的值。|
|`cwd`|字符串|远程计算机上的目标的工作目录。 使用 CMake 时，`${debugInfo.defaultWorkingDirectory}`宏可用作此字段的值。 默认值是远程工作区根，除非在*CMakelists.txt*文件中重写。|
|`miDebuggerPath`|字符串|启用 MI 调试器（如 gdb）的路径。 未指定时，它将首先搜索 PATH 以查找调试器。|
|`miDebuggerServerAddress`|字符串|要连接到的启用 MI 的调试器服务器的网络地址。 示例：本地主机：1234。|
|`setupCommands`|array|要执行一个或多个 GDB/LLDB 命令，以便设置基础调试器。 示例：`"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`。 请参阅[启动设置命令](#launch_setup_commands)。|
|`customLaunchSetupCommands`|array|如果提供，这将用一些其他命令替换用于启动目标的默认命令。 例如，这可以是"目标附加"，以便附加到目标进程。 空命令列表将启动命令替换为任何内容，如果调试器作为命令行选项提供启动选项，则该命令非常有用。 示例：`"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`。|
|`launchCompleteCommand`|字符串|完全设置调试器后要执行的命令，以便使目标进程运行。 允许的值是"执行运行"、"执行-继续"、"无"。 默认值为"执行运行"。|
|`debugServerPath`|字符串|调试要启动的服务器的可选完整路径。 默认值为 null。|
|`debugServerArgs`|字符串|可选调试服务器 args。 默认值为 null。|
|`filterStderr`|boolean|搜索服务器启动的模式和日志稳占器以调试输出的稳稳流流。 默认为 `false`。|
|`coreDumpPath`|字符串|指定程序的核心转储文件的可选完整路径。 默认值为 null。|
外部控制台|boolean|如果为 true，则为调试器启动控制台。 如果未`false`启动控制台。 默认为 `false`。 注： 在某些情况下，由于技术原因，此选项将被忽略。|
|`pipeTransport`|字符串|如果存在，这将告诉调试器使用另一个可执行文件连接到远程计算机，作为管道，它将在 Visual Studio 和启用 MI 的调试器（如 gdb）之间中继标准输入/输出。 允许的值：一个或多个[管道传输选项](#pipe_transport_options)。|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>启动设置命令

与`setupCommands`属性一起使用：

||||
|-|-|-|
|`text`|字符串|要执行的调试器命令。|
|`description`|字符串|命令的可选说明。|
|`ignoreFailures`|boolean|如果为 true，则应忽略命令中的失败。 默认为 `false`。|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>管道运输选项

与`pipeTransport`属性一起使用：

||||
|-|-|-|
|`pipeCwd`|字符串|管道程序工作目录的完全限定路径。|
|`pipeProgram`|字符串|要执行的完全限定的管道命令。|
|`pipeArgs`|array|传递给管道程序的命令行参数以配置连接。|
|`debuggerPath`|字符串|目标计算机上的调试器的完整路径，例如 /usr/bin/gdb。|
|`pipeEnv`|对象 (object)|传递给管道程序的环境变量。|
|`quoteArgs`|boolean|如果单个参数包含字符（如空格或制表符），是否应引用它？ 如果`false`，调试器命令将不再自动引用。 默认为 `true`。|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>源文件映射选项

与属性一`sourceFileMap`起使用：

||||
|-|-|-|
|`editorPath`|字符串|要查找的源代码的位置。|
|`useForBreakpoints`|boolean|设置断点时，应使用此源映射。 如果`false`，则仅使用文件名和行号来设置断点。 如果`true`，只有在使用此源映射时，才会使用文件和行号的完整路径设置断点。 否则，在设置断点时将只使用文件名和行号。 默认为 `true`。|
