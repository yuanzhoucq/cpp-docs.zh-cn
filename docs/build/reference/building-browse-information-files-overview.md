---
title: 生成浏览信息文件：概述
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: ffacb7aaf9ac1f7ad6fc4cf12ab479099dc57725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320675"
---
# <a name="building-browse-information-files-overview"></a>生成浏览信息文件：概述

> [!WARNING]
> 虽然安装 Visual Studio 时仍会安装 BSCMAKE，但 IDE 将不再使用它。 从 Visual Studio 2008 起，浏览信息和符号信息自动存储在解决方案文件夹的 SQL Server .sdf 文件中。

要为符号浏览创建浏览信息，编译器会为项目中的每个源文件创建一个 .sbr 文件，然后为 BSCMAKE 创建。EXE 将 .sbr 文件串联到一个 .bsc 文件中。

生成 .sbr 和 .bsc 文件需要时间，因此 Visual Studio 默认关闭这些功能。 如果要浏览当前信息，则必须打开浏览选项并再次生成项目。

使用[/FR](fr-fr-create-dot-sbr-file.md)或[/Fr](fr-fr-create-dot-sbr-file.md)告诉编译器创建 .sbr 文件。 要创建 .bsc 文件，可以从命令行调用[BSCMAKE。](bscmake-command-line.md) 使用命令行中的 BSCMAKE 可以更精确地控制浏览信息文件的操作。 有关详细信息，请参阅[BSCMAKE 参考](bscmake-reference.md)。

> [!TIP]
> 您可以打开 .sbr 文件生成，但关闭 .bsc 文件生成。 这提供了快速的生成，但也使您能够通过打开 .bsc 文件生成和生成项目快速创建新的 .bsc 文件。

您可以通过减小 .bsc 文件的大小来减少生成 .bsc 文件所需的时间、内存和磁盘空间。

有关如何在开发环境中生成浏览器文件的信息，请参阅[常规属性页（项目）。](general-property-page-project.md)

### <a name="to-create-a-smaller-bsc-file"></a>创建较小的 .bsc 文件

1. 使用[BSCMAKE 命令行选项](bscmake-options.md)从浏览信息文件中排除信息。

1. 编译或组装时，在一个或多个 .sbr 文件中省略本地符号。

1. 如果对象文件不包含当前调试阶段所需的信息，则在重新生成浏览信息文件时，请从 BSCMAKE 命令省略其 .sbr 文件。

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>将多个项目的浏览信息合并到一个浏览器文件 （.bsc）

1. 要么不要在项目级别生成 .bsc 文件，或者使用 .n 开关来防止 .sbr 文件被截断。

1. 生成所有项目后，使用所有 .sbr 文件作为输入运行 BSCMAKE。 可以使用通配符。 例如，如果项目目录 C：\X、C：_Y 和 C：Z 包含 .sbr 文件，并且希望将它们全部合并到一个 .bsc 文件中，则使用\\\*BSCMAKE C：\X .sbr\\\*C：Y .sbr\\\*C：\Z .sbr /o c：\whatever_directory\s.bsc 来构建组合的 .bsc 文件。

## <a name="see-also"></a>另请参阅

[其他 MSVC 构建工具](c-cpp-build-tools.md)<br/>
[BSCMAKE 参考](bscmake-reference.md)
