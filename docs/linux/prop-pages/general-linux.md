---
title: 常规属性（Linux C++ 项目）
description: 介绍了可在 Visual Studio 的“常规属性”页面中设置的 Linux 项目属性。
ms.date: 01/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: 832f10ca2c95e40ff7ece23462105fa49014aa5d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446168"
---
# <a name="general-properties-linux-c"></a>常规属性 (Linux C++)

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

::: moniker range=">=vs-2017"

| Property | 描述 | 选项 |
|--|--|--|
| 输出目录 | 指定输出文件目录的相对路径。 它可包括环境变量。 |
| 中间目录 | 指定中间文件目录的相对路径。 它可包括环境变量。 |
| Target Name | 指定此项目生成的文件名称。 |
| 目标扩展名 | 指定此项目生成的文件名称（例如 `.a`）。 |
| 清除时要删除的扩展名 | 分号分隔的通配符规范，指定在清除或重新生成时要删除中间目录中的哪些文件。 |
| 生成日志文件 | 指定启用生成日志时要写入的生成日志文件。 |
| 平台工具集 | 指定用于生成当前配置的工具集。 如果未设置，则使用默认工具集。 |
| 远程生成计算机 | 显示用于远程生成、部署和调试的目标计算机或设备。 可通过使用“工具” > “选项” > “跨平台” > “连接管理器”，添加或编辑目标计算机连接     。<br /> Visual Studio 2019 版本 16.1：可在[调试](debugging-linux.md)页面中指定其他用于调试的计算机  。 |
| 远程生成根目录 | 指定远程计算机或设备上目录的路径。 |
| 远程生成项目目录 | 指定远程计算机或设备上项目的目录路径。 |
| 远程部署目录 | Visual Studio 2019 版本 16.1：指定远程计算机或设备上的目录路径以部署项目  。 |
| 远程副本包含目录 | Visual Studio 2019 版本 16.5：要以递归方式从 Linux 目标复制的目录列表  。 此属性会影响 IntelliSense 的远程标头副本，但不影响生成。 可在“IntelliSense 使用编译器默认值”设置为 false 时使用它  。 使用“C/C++ 常规”选项卡下的“其他包含目录”来指定要同时对 IntelliSense 和生成使用的其他包含目录  。 |
| 远程副本排除目录 | Visual Studio 2019 版本 16.5：不从 Linux 目标复制的目录列表   。 通常，此属性用于删除包含目录的子目录。 |
| IntelliSense 使用编译器默认值 | Visual Studio 2019 版本 16.5：是否要在此项目引用的编译器中查询其包含目录的默认列表  。 这些位置会自动添加到要复制的远程目录列表中。 仅当编译器不支持类似 gcc 的参数时，才将此属性设置为 false。 gcc 和 clang 编译器都支持查询包含目录（例如 `g++ -x c++ -E -v -std=c++11`）。 |
| 配置类型 | 指定此配置生成的输出类型。 | 动态库 (.so) <br/><br/>静态库 (.a) <br/><br/>应用程序 (.out) <br/><br/>生成文件  |
| STL 的使用 | 指定要用于此配置的 C++ 标准库。 | **共享 GNU 标准 C++ 库**<br/><br/>**静态 GNU 标准 C++ 库 (-static)** |

::: moniker-end
