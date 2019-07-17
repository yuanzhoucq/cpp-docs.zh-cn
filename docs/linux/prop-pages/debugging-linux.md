---
title: 调试程序属性 (Linux C++) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: d76e398d648db7c5cf65e4ca2bb1665aef4359ad
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821396"
---
# <a name="c-debugging-properties-linux-c"></a>C++ 调试属性 (Linux C++)

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

::: moniker range=">=vs-2017"

Property | 说明 | 选项
--- | ---| ---
远程调试计算机 | Visual Studio 2019 版本 16.1：  指定要在其上调试程序的计算机。 可以与[常规](general-linux.md)页上指定的远程生成计算机不同。
启动前命令 | 在调试程序启动之前，在 shell 上运行的可用于调试环境的命令。
计划 | 要在远程系统上调试的程序的完整路径。 如果将其留空或不进行更改，则默认为当前项目的输出路径。
程序参数 | 要传递到正在进行调试的程序的命令行参数。
工作目录 | 远程应用程序的工作目录。 默认情况下，为用户主目录。
其他调试程序命令 | 启动调试前要运行的调试程序的其他 `gdb` 命令。
调试程序端口号 | 调试程序与远程调试程序通信的端口号。 该端口不得是本地正在使用的端口。 该值必须是介于 1 到 65535 之间的正数。 如果未提供，则会使用空闲端口号。
远程调试程序端口号 | 远程系统上远程调试程序服务器 `gdbserver` 正在侦听的端口号。 该端口不得是远程系统上正在使用的端口。 该值必须是介于 1 到 65535 之间的正数。 如果未提供，则将使用从 4444 开始的空闲端口号。
调试模式 | 指定调试程序如何与 `gdb` 交互。 在 gdb 模式下，调试程序在远程系统上通过 shell 驱动 `gdb`  。 在 gdbserver 模式下，`gdb` 在本地运行并连接到远程运行的 `gdbserver`  。 | **gdbserver**<br/>**gdb**
其他符号搜索路径 | 调试符号的其他搜索路径 (solib-search-path)。
调试子进程 | 指定是否启用子进程调试。
启用 Python 优质打印 | 启用优质打印公式值。 仅支持在 gdb 调试模式下受支持。
可视化文件 | 包含 SLT 类型的可视化指令的默认本机可视化文件(.natvis)。 将自动加载属于当前解决方案的其他 .natvis 文件。
其他源文件路径映射 | 调试程序用于将 Windows 源文件名映射到 Linux 源文件名的其他路径等效项。 格式为“\<windows-path> =\<linux-path>;...”。 将引用 Windows 路径下找到的源文件名，如同在 Linux 路径下的同一相对位置找到该文件名。 本地项目中找到的文件不需要其他映射。

::: moniker-end
