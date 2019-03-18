---
title: 生成浏览信息文件：概述
ms.date: 11/04/2016
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 4f12bd25ca3ab718a845dbb04aba3169cc6d4b19
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820597"
---
# <a name="building-browse-information-files-overview"></a>生成浏览信息文件：概述

若要创建符号浏览的浏览信息，编译器在项目中，然后 BSCMAKE 创建每个源文件的.sbr 文件。EXE 串联到一个.bsc 文件中的.sbr 文件。

生成.sbr 和.bsc 文件需要时间，因此 Visual c + + 将关闭默认情况下的这些函数。 如果你想要浏览当前信息，必须开启浏览选项，并再次生成项目。

使用[/FR](fr-fr-create-dot-sbr-file.md)或[/Fr](fr-fr-create-dot-sbr-file.md)以告知编译器创建.sbr 文件。 若要创建.bsc 文件，可以调用[BSCMAKE](bscmake-command-line.md)从命令行。 从命令行使用 BSCMAKE 可以更加精确地控制浏览信息文件的操作。 请参阅[BSCMAKE 参考](bscmake-reference.md)有关详细信息。

> [!TIP]
>  您可以打开.sbr 文件生成，但保留.bsc 文件生成处于关闭状态。 这提供了快速生成，但还可以通过打开生成.bsc 文件并生成项目快速创建新的.bsc 文件。

您可以减少时间、 内存和生成.bsc 文件的大小减少的.bsc 文件所需的磁盘空间。

请参阅[常规属性页 （项目）](general-property-page-project.md)有关如何构建开发环境中的浏览器文件的信息。

### <a name="to-create-a-smaller-bsc-file"></a>若要创建较小的.bsc 文件

1. 使用[BSCMAKE 命令行选项](bscmake-options.md)从浏览信息文件中排除的信息。

1. 忽略一个或多个.sbr 文件编译或汇编时中的本地符号。

1. 如果对象文件不包含所需的调试在当前阶段的信息，在重新生成浏览信息文件时省略 BSCMAKE 命令从其.sbr 文件。

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>若要合并到一个浏览器文件 (.bsc) 从多个项目的浏览信息

1. 通过不生成.bsc 文件，在项目级别或使用 /n 开关可防止.sbr 文件被截断。

1. 生成所有项目后，作为输入使用所有的.sbr 文件运行 BSCMAKE。 使用通配符。 例如，如果你有与在它们和你想要将它们合并到一个.bsc 文件中所有.sbr 文件的项目目录 C:\X、 C:\Y 和 C:\Z，然后使用 BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\\*.sbr /o c:\whatever_directory\combined.bsc 构建组合的.bsc 文件。

## <a name="see-also"></a>请参阅

[其他 MSVC 生成工具](c-cpp-build-tools.md)<br/>
[BSCMAKE 参考](bscmake-reference.md)
