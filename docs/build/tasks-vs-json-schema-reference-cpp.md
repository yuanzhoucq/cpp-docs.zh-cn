---
title: 任务. 与 json 架构引用 (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 1e533babafad554e8f7413d2bc1a88933a6eca42
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69975906"
---
# <a name="tasksvsjson-schema-reference-c"></a>任务. 与 json 架构引用 (C++)

若要告诉 Visual Studio 如何在打开的文件夹项目中生成源代码, 请添加 "*任务" 和 "json* " 文件。 你可以在此处定义任意任意任务, 然后从**解决方案资源管理器**上下文菜单中调用它。 CMake 项目不使用此文件, 因为在*cmakelists.txt*中指定了所有生成命令。 对于 CMake 以外的生成系统,可在其中指定生成命令和调用生成脚本。 有关使用*任务*的常规信息, 请参阅为["打开文件夹" 开发自定义生成和调试任务](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio)。

任务`type`的属性可以是以下四个值之一: `default`、 `launch`、 `remote`或`msbuild`。 除非需要远程连接`launch` , 否则大多数任务应使用。

## <a name="default-properties"></a>默认属性

默认属性可用于所有类型的任务:

||||
|-|-|-|
|**Property**|类型|**说明**|
|`taskLabel`|string| （必选。）指定在用户界面中使用的任务标签。|
|`appliesTo`|string| （必选。）指定可对其执行命令的文件。 支持使用通配符, 例如: " *"、"* .cpp"、"/* .txt"|
|`contextType`|string| 允许的值: "自定义"、"生成"、"清理"、"重新生成"。 确定在上下文菜单中将显示任务的位置。 默认值为 "自定义"。|
|`output`|string| 指定任务的输出标记。|
|`inheritEnvironments`|array| 指定从多个源继承的一组环境变量。 可以在文件 (如*CMakeSettings*或*cppproperties.json* ) 中定义变量, 并将其提供给任务上下文使用。|
|`passEnvVars`|boolean| 指定是否在任务上下文中包含其他环境变量。 这些变量与使用`envVars`属性定义的变量不同。 默认值为 "true"。|

## <a name="launch-properties"></a>启动属性

如果任务类型为`launch`, 则可以使用以下属性:

||||
|-|-|-|
|**Property**|类型|**说明**|
|`command`|string| 指定要启动的进程或脚本的完整路径。|
|`args`|array| 指定传递给命令的以逗号分隔的参数列表。|
|`launchOption`|string| 允许的值:"None"、"ContinueOnError"、"IgnoreError"。 指定在出现错误时如何继续执行该命令。|
|`workingDirectory`|string| 指定要在其中运行命令的目录。 默认为项目的当前工作目录。|
|`customLaunchCommand`|string| 指定执行命令之前要应用的全局范围自定义。 用于设置环境变量, 如% PATH%。|
|`customLaunchCommandArgs`|string| 指定 customLaunchCommand 的参数。 (需要`customLaunchCommand`。)|
 `env`| 指定自定义环境变量的键值列表。 例如, "myEnv": "myVal"|
|`commands`|array| 指定要按顺序调用的命令的列表。|

### <a name="example"></a>示例

以下任务将在文件夹中提供生成文件并`Mingw64`在*cppproperties.json*中定义了环境时调用 setup.exe, 如[cppproperties.json 架构引用](cppproperties-schema-reference.md#user_defined_environments)中所示:

```json
 {
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "gcc make",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make"
    },
    {
      "taskLabel": "gcc clean",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make",
      "args": ["clean"]
    }
  ]
}
```

右键单击**解决方案资源管理器**中的 *.cpp*文件时, 可以从上下文菜单中调用这些任务。

## <a name="remote-properties"></a>远程属性

当你安装具有C++工作负荷的 Linux 开发并使用 Visual Studio 连接管理器添加到远程计算机的连接时, 将启用远程任务。 远程任务在远程系统上运行命令, 还可以将文件复制到其中。

如果任务类型为`remote`, 则可以使用以下属性:

||||
|-|-|-|
|**Property**|类型|**说明**|
|`remoteMachineName`|string|远程计算机的名称。 必须与**连接管理器**中的计算机名称匹配。|
|`command`|string|要发送到远程计算机的命令。 默认情况下, 将在远程系统上的 $HOME 目录中执行命令。|
|`remoteWorkingDirectory`|string|远程计算机上的当前工作目录。|
|`localCopyDirectory`|string|要复制到远程计算机的本地目录。 默认为当前工作目录。|
|`remoteCopyDirectory`|string|要`localCopyDirectory`复制到的远程计算机上的目录。|
|`remoteCopyMethod`|string| 要用于复制的方法。 允许的值: "none"、"sftp"、"rsync"。 对于大型项目, 建议使用 rsync。|
|`remoteCopySourcesOutputVerbosity`|string| 允许的值:"正常"、"详细"、"诊断"。|
|`rsyncCommandArgs`|string|默认值为 "-t--delete"。|
|`remoteCopyExclusionList`|array|要从复制操作中排除的`localCopyDirectory`中的文件列表 (以逗号分隔)。|

### <a name="example"></a>示例

在**解决方案资源管理器**中右键单击*main .cpp*时, 以下任务将显示在上下文菜单中。 它依赖于在`ubuntu` **连接管理器**中调用的远程计算机。 该任务将 Visual Studio 中当前打开的文件夹复制到`sample`远程计算机上的目录中, 然后调用 g + + 来生成程序。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Build",
      "appliesTo": "main.cpp",
      "type": "remote",
      "contextType": "build",
      "command": "g++ main.cpp",
      "remoteMachineName": "ubuntu",
      "remoteCopyDirectory": "~/sample",
      "remoteCopyMethod": "sftp",
      "remoteWorkingDirectory": "~/sample/hello",
      "remoteCopySourcesOutputVerbosity": "Verbose"
    }
  ]
}
```

## <a name="msbuild-properties"></a>MSBuild 属性

如果任务类型为`msbuild`, 则可以使用以下属性:

||||
|-|-|-|
|**Property**|类型|**说明**|
|`verbosity`|string| 指定 MSBuild 项目生成输出 verbosityAllowed 值:"Quiet"、"最小"、"正常"、"详细"、"诊断"。|
|`toolsVersion`|string| 指定用于生成项目的工具集版本, 例如 "2.0"、"3.5"、"4.0"、"当前"。 默认值为 "当前"。|
|`globalProperties`|对象 (object)|指定要传递到项目中的全局属性的键值列表, 例如 "配置": "Release"|
|`properties`|对象 (object)| 指定仅附加项目属性的键-值列表。|
|`targets`|array| 指定要在项目中按顺序调用的目标的列表。 如果未指定, 则使用项目的默认目标。|
