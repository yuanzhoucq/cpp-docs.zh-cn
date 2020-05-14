---
title: tasks.vs.json 架构参考 (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: cc6b2983d3cc3d40449357a554df5feee38c21d9
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556651"
---
# <a name="tasksvsjson-schema-reference-c"></a>tasks.vs.json 架构参考 (C++)

若要告知 Visual Studio 如何在打开文件夹项目中生成源代码，请添加 tasks.vs.json  文件。 可以在其中定义任意任务，然后从“解决方案资源管理器”上下文菜单调用它  。 CMake 项目不使用此文件，因为所有生成命令都在 CMakeLists.txt  中指定。 对于 CMake 以外的生成系统，可在 tasks.vs.json  中指定生成命令和调用生成脚本。 有关使用 tasks.vs.json  的常规信息，请参阅[为“打开文件夹”开发自定义生成和调试任务](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio)。

任务具有一个 `type` 属性，该属性可能具有以下四个值之一：`default`、`launch`、`remote` 或 `msbuild`。 大多数任务应使用 `launch`，除非需要远程连接。

## <a name="default-properties"></a>默认属性

默认属性可用于所有类型的任务：

||||
|-|-|-|
|**Property**|**Type**|**说明**|
|`taskLabel`|string| （必选。）指定在用户界面中使用的任务标签。|
|`appliesTo`|string| （必选。）指定可对其执行命令的文件。 支持使用通配符，例如：“ *”、“* .cpp”、“/*.txt”|
|`contextType`|string| 允许的值：“custom”、“build”、“clean”、“rebuild”。 确定在上下文菜单中显示任务的位置。 默认值为“custom”。|
|`output`|string| 指定任务的输出标记。|
|`inheritEnvironments`|array| 指定从多个源继承的一组环境变量。 可以在 CMakeSettings.json  或 CppProperties.json  等文件中定义变量，并使它们可用于任务上下文。 Visual Studio 16.4  ：使用 `env.VARIABLE_NAME` 语法，根据每个任务指定环境变量。 若要取消设置某个变量，请将它设置为“null”。|
|`passEnvVars`|boolean| 指定是否在任务上下文中包含其他环境变量。 这些变量与使用 `envVars` 属性定义的变量不同。 默认为“true”。|

## <a name="launch-properties"></a>启动属性

任务类型为 `launch` 时，可以使用以下属性：

||||
|-|-|-|
|**Property**|**Type**|**说明**|
|`command`|string| 指定要启动的进程或脚本的完整路径。|
|`args`|array| 指定传递给命令的参数的逗号分隔列表。|
|`launchOption`|string| 允许的值：“None”、“ContinueOnError”、“IgnoreError”。 指定在出现错误时如何继续执行命令。|
|`workingDirectory`|string| 指定要在其中运行命令的目录。 默认为项目当前的工作目录。|
|`customLaunchCommand`|string| 指定执行命令之前要应用的全局范围自定义。 用于设置环境变量，如 %PATH%。|
|`customLaunchCommandArgs`|string| 指定 customLaunchCommand 的参数。 （需要 `customLaunchCommand`。）|
 `env`| 指定自定义环境变量的键值列表。 例如 "myEnv": "myVal"|
|`commands`|array| 指定要按顺序调用的命令的列表。|

### <a name="example"></a>示例

当在文件夹中提供了生成文件，并且在 CppProperties.json  中定义了 `Mingw64` 环境时，以下任务调用 make.exe  ，如 [CppProperties.json 架构参考](cppproperties-schema-reference.md#user_defined_environments)中所示：

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

在“解决方案资源管理器”  中右键单击某个 .cpp  文件时，可以从上下文菜单中调用这些任务。

## <a name="remote-properties"></a>远程属性

当使用 Visual Studio 连接管理器安装“使用 C++ 的 Linux 开发”工作负载并添加到远程计算机的连接时，会启用远程任务。 远程任务在远程系统上运行命令，还可以将文件复制到其中。

任务类型为 `remote` 时，可以使用以下属性：

||||
|-|-|-|
|**Property**|**Type**|**说明**|
|`remoteMachineName`|string|远程计算机的名称。 必须与“连接管理器”  中的计算机名称匹配。|
|`command`|string|要发送到远程计算机的命令。 默认情况下，将在远程系统上的 $HOME 目录中执行命令。|
|`remoteWorkingDirectory`|string|远程计算机上的当前工作目录。|
|`localCopyDirectory`|string|要复制到远程计算机的本地目录。 默认为当前工作目录。|
|`remoteCopyDirectory`|string|远程计算机上要将 `localCopyDirectory` 复制到其中的目录。|
|`remoteCopyMethod`|string| 要用于复制的方法。 允许的值：“none”、“sftp”、“rsync”。 对于大型项目，建议使用 rsync。|
|`remoteCopySourcesOutputVerbosity`|string| 允许的值：“Normal”、“Verbose”、“Diagnostic”。|
|`rsyncCommandArgs`|string|默认为“-t --delete”。|
|`remoteCopyExclusionList`|array|`localCopyDirectory` 中要从复制操作中排除的文件的逗号分隔列表。|

### <a name="example"></a>示例

在“解决方案资源管理器”  中右键单击 main.cpp  时，以下任务会出现在上下文菜单中。 这取决于“连接管理器”  中名为 `ubuntu` 的远程计算机。 该任务将 Visual Studio 中当前打开文件夹复制到远程计算机上的 `sample` 目录中，然后调用 g++ 以生成程序。

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

任务类型为 `msbuild` 时，可以使用以下属性：

||||
|-|-|-|
|**Property**|**Type**|**说明**|
|`verbosity`|string| 指定 MSBuild 项目生成输出 verbosityAllowed 值：“Quiet”、“Minimal”、“Normal”、“Detailed”、“Diagnostic”。|
|`toolsVersion`|string| 指定用于生成项目的工具集版本，例如“2.0”、“3.5”、“4.0”、“Current”。 默认为“Current”。|
|`globalProperties`|对象 (object)|指定要传递到项目中的全局属性的键值列表，例如 "Configuration":"Release"|
|`properties`|对象 (object)| 指定其他仅项目属性的键值列表。|
|`targets`|array| 指定要对项目按顺序调用的目标的列表。 如果未指定，则使用项目的默认目标。|
