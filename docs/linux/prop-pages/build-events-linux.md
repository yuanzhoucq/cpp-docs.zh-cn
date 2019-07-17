---
title: 远程生成事件 (Linux c + +)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 1e5c453da05fe65871fa7f6b0d4ca6528a96d4dd
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821473"
---
# <a name="build-event-properties-linux-c"></a>生成事件属性 (Linux C++)

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>预生成事件

Property | 说明
--- | ---
命令行 | 指定让预生成事件工具运行的命令行。
说明 | 指定让预生成事件工具显示的说明。
在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。
要复制的其他文件 | 指定要复制到远程系统的其他文件。 根据需要，可使用类似 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2 的语法以本地到远程的映射对形式提供列表，其中可将本地文件复制到远程系统的指定远程位置。

## <a name="pre-link-event"></a>预链接事件

Property | 说明
--- | ---
命令行 | 指定让预链接事件工具运行的命令行。
说明 | 指定让预链接事件工具显示的说明。
在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。
要复制的其他文件 | 指定要复制到远程系统的其他文件。 根据需要，可使用类似 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2 的语法以本地到远程的映射对形式提供列表，其中可将本地文件复制到远程系统的指定远程位置。

## <a name="post-build-event"></a>后期生成事件

Property | 说明
--- | ---
命令行 | 指定让后期生成事件工具运行的命令行。
说明 | 指定让后期生成事件工具显示的说明。
在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。
要复制的其他文件 | 指定要复制到远程系统的其他文件。 根据需要，可使用类似 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2 的语法以本地到远程的映射对形式提供列表，其中可将本地文件复制到远程系统的指定远程位置。

## <a name="remote-pre-build-event"></a>远程预先生成事件

Property | 说明
--- | ---
命令行 | 指定让预生成事件工具在远程系统上运行的命令行。
说明 | 指定让预生成事件工具显示的说明。
在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。
要复制的其他文件 | 指定要从远程系统复制的其他文件。 根据需要，可使用类似 fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2 的语法以远程到本地的映射对形式提供列表，其中可将远程文件复制到本地计算机的指定位置。

## <a name="remote-pre-link-event"></a>远程预链接事件

Property | 说明
--- | ---
命令行 | 指定让预链接事件工具在远程系统上运行的命令行。
说明 | 指定让预链接事件工具显示的说明。
在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。
要复制的其他文件 | 指定要从远程系统复制的其他文件。 根据需要，可使用类似 fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2 的语法以远程到本地的映射对形式提供列表，其中可将远程文件复制到本地计算机的指定位置。

## <a name="remote-post-build-event"></a>远程后期生成事件

Property | 说明
--- | ---
命令行 | 指定让后期生成事件工具在远程系统上运行的命令行。
说明 | 指定让后期生成事件工具显示的说明。
在生成中使用 | 指定是否将该生成事件从当前配置的生成中排除。
要复制的其他文件 | 指定要从远程系统复制的其他文件。 根据需要，可使用类似 fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2 的语法以远程到本地的映射对形式提供列表，其中可将远程文件复制到本地计算机的指定位置。

::: moniker-end


