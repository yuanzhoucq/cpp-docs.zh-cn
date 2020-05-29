---
title: 常规属性（Linux C++ 生成文件项目）| Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
ms.openlocfilehash: 72a7919bc94be80acdbf7a2cef5b4a9875595545
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446148"
---
# <a name="makefile-project-properties-linux-c"></a>生成文件项目属性 (Linux C++)

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

::: moniker range=">=vs-2017"

以下时 Linux 生成文件项目中可用属性的部分列表。 许多生成文件项目属性与 Linux C++ 控制台应用程序项目属性相同。

## <a name="general"></a>常规

| Property | 描述 | 选项 |
|--|--|--|
| 输出目录 | 指定输出文件目录的相对路径；可以包含环境变量。 |
| 中间目录 | 指定中间文件目录的相对路径；可以包含环境变量。 |
| 生成日志文件 | 指定启用生成日志时要写入的生成日志文件。 |
| 配置类型 | 指定此配置生成的输出类型。 | 动态库 (.so) - 动态库 (.so) <br>静态库 (.a) - 静态库 (.a) <br>应用程序 (.out) - 应用程序 (.out) <br>生成文件 - 生成文件 <br> |
| 远程生成计算机 | 要用于远程生成、部署和调试的目标计算机或设备。 |
| 远程生成根目录 | 指定远程计算机或设备上目录的路径。 |
| 远程生成项目目录 | 指定远程计算机或设备上项目的目录路径。 |

## <a name="debugging"></a>调试

请参阅[调试属性 (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>复制源文件

请参阅[复制源项目属性 (Linux C++)](copy-sources-project.md)。

## <a name="build-events"></a>生成事件

### <a name="pre-build-event"></a>预生成事件

| Property | 描述 |
|--|--|
| 命令行 | 指定让预生成事件工具运行的命令行。 |
| 描述 | 指定让预生成事件工具显示的说明。 |
| 在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。 |
| 要复制的其他文件 | 指定要复制到远程系统的其他文件。 根据需要，可使用类似 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2 的语法以本地到远程的映射对形式提供列表，其中可将本地文件复制到远程系统的指定远程位置。 |

### <a name="post-build-event"></a>后期生成事件

| Property | 描述 |
|--|--|
| 命令行 | 指定让后期生成事件工具运行的命令行。 |
| 描述 | 指定让后期生成事件工具显示的说明。 |
| 在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。 |
| 要复制的其他文件 | 指定要复制到远程系统的其他文件。 根据需要，可使用类似 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2 的语法以本地到远程的映射对形式提供列表，其中可将本地文件复制到远程系统的指定远程位置。 |

### <a name="remote-pre-build-event"></a>远程预先生成事件

| Property | 描述 |
|--|--|
| 命令行 | 指定让预生成事件工具在远程系统上运行的命令行。 |
| 描述 | 指定让预生成事件工具显示的说明。 |
| 在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。 |
| 要复制的其他文件 | 指定要从远程系统复制的其他文件。 根据需要，可使用类似 fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2 的语法以远程到本地的映射对形式提供列表，其中可将远程文件复制到本地计算机的指定位置。 |

### <a name="remote-post-build-event"></a>远程后期生成事件

| Property | 描述 |
|--|--|
| 命令行 | 指定让后期生成事件工具在远程系统上运行的命令行。 |
| 描述 | 指定让后期生成事件工具显示的说明。 |
| 在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。 |
| 要复制的其他文件 | 指定要从远程系统复制的其他文件。 根据需要，可使用类似 fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2 的语法以远程到本地的映射对形式提供列表，其中可将远程文件复制到本地计算机的指定位置。 |

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

可在项目或文件级别设置 IntelliSense 属性，提供 IntelliSense 引擎的一些线索。 它们不影响编译。

| Property | 描述 |
|--|--|
| 包含搜索路径 | 指定用于解析所含文件的包含搜索路径。 |
| 强制包含 | 指定强制包含的文件。 |
| 预处理器定义 | 指定源文件使用的预处理器定义。 |
| 取消定义预处理器定义 | 指定取消定义一个或多个预处理器。     (/U[macro]) |
| 附加选项 | 指定分析 C++ 文件时 IntelliSense 使用的附加编译器开关。 |

### <a name="build"></a>生成

| Property | 描述 |
|--|--|
| “生成”命令行 | 指定用于运行“生成”命令的命令行。 |
| “全部重新生成”命令行 | 指定用于运行“全部重新生成”命令的命令行。 |
| “清除”命令行 | 指定用于运行“清除”命令的命令行。 |

### <a name="remote-build"></a>远程生成

| Property | 描述 |
|--|--|
| “生成”命令行 | 指定用于运行“生成”命令的命令行。 这在远程系统上执行。 |
| “全部重新生成”命令行 | 指定用于运行“全部重新生成”命令的命令行。 这在远程系统上执行。 |
| “清除”命令行 | 指定用于运行“清除”命令的命令行。 这在远程系统上执行。 |
| 输出 | 指定远程系统上由远程生成所生成的输出。 |

::: moniker-end
