---
title: Launch.vs.json 架构参考 (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: 0410f22a680d5bfc12270ff686938a54e2e8a8fd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223949"
---
# <a name="launchvsjson-schema-reference-c"></a>Launch.vs.json 架构参考 (C++)

使用 launch.vs.json 文件配置调试参数  。 若要创建文件， 在“解决方案资源管理器”中右键单击可执行文件，然后选择“调试和启动设置”   。 选择与项目最匹配的选项，然后根据需要使用以下属性修改配置。 有关调试 CMake 项目的详细信息，请参阅[配置 CMake 调试会话](/cpp/build/configure-cmake-debugging-sessions)。

## <a name="default-properties"></a>默认属性

||||
|-|-|-|
|**Property**|**Type**|**说明**|
|`name`|string|指定调试目标下拉列表中条目的名称。|
|`type`|string|指定项目是 dll 还是 .exe（默认为 .exe）|
|`project`|string|指定项目文件的相对路径。|
|`projectTarget`|string|指定生成 `project` 时调用的可选目标。 此 `projectTarget` 必须已经存在并且与“调试目标”下拉列表中的名称匹配  。|
|`debugType`|string|根据代码类型指定调试模式（本机、托管或混合）。 除非设置了此参数，否则将自动对此进行检测。 允许的值：“native”、“managed”、“mixed”。|
|`inheritEnvironments`|array|指定从多个源继承的一组环境变量。 可以在 CMakeSettings.json 或 CppProperties.json 等文件中定义一些变量，并使它们可用于调试上下文   。  Visual Studio 16.4  ：使用 `env.VARIABLE_NAME` 语法，根据每个目标指定环境变量。 若要取消设置某个变量，请将它设置为“null”。|
|`args`|array|指定传递给已启动程序的命令行参数。|
|`currentDir`|string|指定生成目标的完整目录路径。 除非设置了此参数，否则将自动对此进行检测。|
|`noDebug`|boolean|指定是否调试已启动程序。 如果没有指定，则此参数的默认值为 `false`。|
|`stopOnEntry`|boolean|指定在启动进程并附加调试程序后是否立即中断。 此参数的默认值为 `false`。|
|`remoteMachine`|string|指定启动程序的远程计算机的名称。|
|`env`|array| 指定自定义环境变量的键值列表。 env:{"myEnv":"myVal"}。|
|`portName`|string|指定附加到正在运行的进程时的端口名称。|
|`buildConfigurations`|array| 一个键值对，指定要应用配置的生成模式的名称。 例如，`Debug` 或 `Release`，且要使用的配置根据所选生成模式确定。

## <a name="c-linux-properties"></a>C++ Linux 属性

||||
|-|-|-|
|**Property**|**Type**|**说明**|
|`program`|string|远程计算机上的程序可执行文件的完整路径。 使用 CMake 时，宏 `${debugInfo.fullTargetPath}` 可用作此字段的值。|
|`processId`|integer|要将调试程序附加到的可选进程 ID。|
|`sourceFileMap`|对象 (object)|传递给调试引擎的可选源文件映射。 格式：`{ "\<Compiler source location>": "\<Editor source location>" }` 或 `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`。 示例：`{ "/home/user/foo": "C:\\foo" }` 或 `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`。 请参阅[源文件映射选项](#source_file_map_options)。|
|`additionalProperties`|string|其中一个 sourceFileMapOptions。 （请参阅下文。）|
|`MIMode`|string|指示 MIDebugEngine 将连接到的已启用 MI 的控制台调试程序的类型。 允许的值为“gdb”、“lldb”。|
|`args`|array|传递给程序的命令行参数。|
|`environment`|array|要添加到程序环境的环境变量。 示例：[ { "name": "squid", "value": "clam" } ]。|
|`targetArchitecture`|string|调试对象的体系结构。 除非设置了此参数，否则将自动对此进行检测。 允许的值为 x86、arm、arm64、mips、x64、amd64、x86_64。|
|`visualizerFile`|string|调试此进程时要使用的 .natvis 文件。 此选项与 GDB 整齐打印不兼容。 如果使用此设置，请参阅“showDisplayString”。|
|`showDisplayString`|boolean|指定 visualizerFile 时，showDisplayString 将启用显示字符串。 启用此选项可能导致调试期间性能降低。|
|`remoteMachineName`|string|托管 gdb 和要调试的程序的远程 Linux 计算机。 使用连接管理器添加新的 Linux 计算机。 使用 CMake 时，宏 `${debugInfo.remoteMachineName}` 可用作此字段的值。|
|`cwd`|string|远程计算机上的目标的工作目录。 使用 CMake 时，宏 `${debugInfo.defaultWorkingDirectory}` 可用作此字段的值。 除非在 CMakeLists.txt 文件中被替代，否则默认值为远程工作区根目录  。|
|`miDebuggerPath`|string|启用 MI 的调试程序（例如 gdb）的路径。 如果未指定，它将首先搜索调试程序的路径。|
|`miDebuggerServerAddress`|string|要连接到的已启用 MI 的调试程序服务器的网络地址。 示例：localhost:1234。|
|`setupCommands`|array|为了设置基础调试程序而需要执行的一个或多个 GDB/LLDB 命令。 示例：`"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`。 请参阅[启动安装程序命令](#launch_setup_commands)。|
|`customLaunchSetupCommands`|array|如果提供，则会使用一些其他命令替换用于启动目标的默认命令。 例如，为了附加到目标进程，可以是“-target-attach”。 空命令列表将启动命令替换为空内容，这在将启动选项作为命令行选项提供给调试程序时很有用。 示例：`"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`。|
|`launchCompleteCommand`|string|调试程序完全设置好以后要执行的命令，用于使目标进程运行。 允许的值为“exec-run”、“exec-continue”、“None”。 默认值为“exec-run”。|
|`debugServerPath`|string|要启动的调试服务器的可选完整路径。 默认为“null”。|
|`debugServerArgs`|string|可选的调试服务器参数。 默认为“null”。|
|`filterStderr`|boolean|在 stderr 流中搜索服务器启动模式，并将 stderr 记录到调试输出。 默认为 `false`。|
|`coreDumpPath`|string|指定程序的核心转储文件的可选完整路径。 默认为“null”。|
externalConsole|boolean|如果为 true，则为调试对象启动控制台。 如果为 `false`，则不会启动任何控制台。 默认为 `false`。 注意：由于技术原因，此选项在某些情况下被忽略。|
|`pipeTransport`|string|如果存在，则会告知调试程序使用其他可执行文件作为管道连接到远程计算机，此管道将在 Visual Studio 和已启用 MI 的调试程序（例如 gdb）之间中继标准输入/输出。 允许的值：一个或多个[管道传输选项](#pipe_transport_options)。|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>启动安装程序命令

与 `setupCommands` 属性配合使用：

||||
|-|-|-|
|`text`|string|要执行的调试程序命令。|
|`description`|string|命令的可选说明。|
|`ignoreFailures`|boolean|如果为 true，则应忽略命令的失败。 默认为 `false`。|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>管道传输选项

与 `pipeTransport` 属性配合使用：

||||
|-|-|-|
|`pipeCwd`|string|管道程序工作目录的完全限定的路径。|
|`pipeProgram`|string|要执行的完全限定的管道命令。|
|`pipeArgs`|array|传递给管道程序用于配置连接的命令行参数。|
|`debuggerPath`|string|目标计算机上调试程序的完整路径，例如，/usr/bin/gdb。|
|`pipeEnv`|对象 (object)|传递给管道程序的环境变量。|
|`quoteArgs`|boolean|如果各个参数包含字符（例如空格或制表符），是否应将其加引号？ 如果为 `false`，则调试器命令将不再被自动引用。 默认为 `true`。|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>源文件映射选项

与 `sourceFileMap` 属性配合使用：

||||
|-|-|-|
|`editorPath`|string|编辑器要查找的源代码的位置。|
|`useForBreakpoints`|boolean|设置断点时，应使用此源映射。 如果为 `false`，则只有文件名和行号用于设置断点。 如果为 `true`，则只有在使用此源映射时，才会使用文件的完整路径和行号设置断点。 否则，设置断点时将仅使用文件名和行号。 默认为 `true`。|
