---
title: MSVC C/C++编译器参考-Visual Studio
description: MSVC 编译器工具集选项。
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: c75176b139895d7b00d88aca1c58604b47386894
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077377"
---
# <a name="compiling-a-cc-project"></a>编译 C/C++项目

可在C++ VISUAL Studio IDE 或命令行中设置 C 和编译器选项。

## <a name="in-visual-studio"></a>在 Visual Studio 中

可以在其 "Visual Studio**属性页**" 对话框中为每个项目设置编译器选项。 在左窗格中，依次选择 "**配置属性**"、" **C/C++**  " 和 "编译器" 选项类别。 每个编译器选项的主题描述如何在开发环境中设置和查找它。 有关完整列表，请参阅[MSVC 编译器选项](compiler-options.md)。

## <a name="from-the-command-line"></a>从命令行

可在下列位置设置编译器 (CL.exe) 选项：

- [在命令行上](compiler-command-line-syntax.md)

- [在命令文件中](cl-command-files.md)

- [在 CL 环境变量中](cl-environment-variables.md)

每次调用 CL 时都会使用在 CL 环境变量中指定的选项。 如果在 CL 环境变量中或在命令行上指定了命令文件，则使用在此命令文件中指定的选项。 与命令行或 CL 环境变量不同，命令文件允许使用多行选项和文件名。

按照“从左到右”的顺序处理编译器选项，如果检测到冲突，则先处理最后（最右边）的选项。 CL 环境变量在命令行之前处理，因此，如果 CL 和命令行之间发生任何冲突，则优先处理命令行。

## <a name="additional-compiler-topics"></a>其他编译器主题

- [MSVC 编译器选项](compiler-options.md)

- [预编译的头文件](../creating-precompiled-header-files.md)

- [CL 调用链接器](cl-invokes-the-linker.md)

有关选择编译器主机和目标体系结构的信息，请[参阅C++为64位 x64 目标配置项目](../configuring-programs-for-64-bit-visual-cpp.md)。

## <a name="see-also"></a>另请参阅

[C/C++ 生成参考](c-cpp-building-reference.md)
