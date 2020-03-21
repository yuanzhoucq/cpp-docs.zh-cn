---
title: 生成浏览信息文件：概述
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 94cb5865e56e12f51ef4a8598a5df3fcbe69fa0f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078355"
---
# <a name="building-browse-information-files-overview"></a>生成浏览信息文件：概述

> [!WARNING]
> 虽然安装 Visual Studio 时仍会安装 BSCMAKE，但 IDE 将不再使用它。 从 Visual Studio 2008 起，浏览信息和符号信息自动存储在解决方案文件夹的 SQL Server .sdf 文件中。

若要为符号浏览创建浏览信息，编译器会为项目中的每个源文件创建一个 .sbr 文件，然后创建 BSCMAKE。EXE 将 .sbr 文件连接到一个 .bsc 文件中。

生成 .sbr 和 .bsc 文件会耗费时间，因此 Visual Studio 默认关闭这些功能。 如果要浏览当前信息，必须打开上的 "浏览" 选项，然后重新生成项目。

使用[/fr](fr-fr-create-dot-sbr-file.md)或[/fr](fr-fr-create-dot-sbr-file.md)告诉编译器创建 .sbr 文件。 若要创建 .bsc 文件，可以从命令行调用[BSCMAKE](bscmake-command-line.md) 。 使用命令行中的 BSCMAKE 使你可以更精确地控制浏览信息文件的操作。 有关详细信息，请参阅[BSCMAKE 参考](bscmake-reference.md)。

> [!TIP]
>  可以启用 .sbr 文件生成，但会关闭 .bsc 文件生成功能。 这可提供快速生成，还可让你通过打开 .bsc 文件生成和生成项目来快速创建新的 .bsc 文件。

可以通过减少 .bsc 文件的大小来减少生成 .bsc 文件所需的时间、内存和磁盘空间。

有关如何在开发环境中生成浏览器文件的信息，请参阅[常规属性页（项目）](general-property-page-project.md) 。

### <a name="to-create-a-smaller-bsc-file"></a>创建更小的 .bsc 文件

1. 使用[BSCMAKE 命令行选项](bscmake-options.md)排除浏览信息文件中的信息。

1. 编译或组装时，忽略一个或多个 .sbr 文件中的本地符号。

1. 如果对象文件不包含当前调试阶段所需的信息，请在重新生成浏览信息文件时省略 BSCMAKE 命令中的 .sbr 文件。

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>将多个项目中的浏览信息合并到一个浏览器文件（.bsc）中

1. 请勿在项目级别生成 .bsc 文件或使用/n 开关阻止 .sbr 文件被截断。

1. 生成所有项目后，运行 BSCMAKE 并将所有 .sbr 文件作为输入。 可以使用通配符。 例如，如果你的项目目录 C:\X、C:\Y 和 C:\Z 中包含 .sbr 文件，并且你想要将它们全部合并为 .bsc 文件，则使用 BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\\*/o c：\ 来构建组合 .bsc 文件。

## <a name="see-also"></a>另请参阅

[其他 MSVC 生成工具](c-cpp-build-tools.md)<br/>
[BSCMAKE 参考](bscmake-reference.md)
