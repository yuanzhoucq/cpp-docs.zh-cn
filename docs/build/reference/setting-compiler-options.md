---
title: 设置编译器选项
ms.date: 11/04/2016
helpviewer_keywords:
- compiler options, setting
- cl.exe compiler, setting options
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
ms.openlocfilehash: 62a6c7913a088f9b986a09b205e4fb9bb350581a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602184"
---
# <a name="setting-compiler-options"></a>设置编译器选项

可在开发环境中或命令行上设置 C 和 C++ 编译器选项。

## <a name="in-the-development-environment"></a>在开发环境内

您可以设置的每个项目的编译器选项及其**属性页**对话框。 在左窗格中，选择**配置属性**， **C/c + +** ，然后选择编译器选项类别。 每个编译器选项的主题描述如何在开发环境中设置和查找它。 请参阅[编译器选项](../../build/reference/compiler-options.md)有关的完整列表。

## <a name="outside-the-development-environment"></a>在开发环境外

可在下列位置设置编译器 (CL.exe) 选项：

- [在命令行上](../../build/reference/compiler-command-line-syntax.md)

- [在命令文件](../../build/reference/cl-command-files.md)

- [在 CL 环境变量](../../build/reference/cl-environment-variables.md)

每次调用 CL 时都会使用在 CL 环境变量中指定的选项。 如果在 CL 环境变量中或在命令行上指定了命令文件，则使用在此命令文件中指定的选项。 与命令行或 CL 环境变量不同，命令文件允许使用多行选项和文件名。

按照“从左到右”的顺序处理编译器选项，如果检测到冲突，则先处理最后（最右边）的选项。 CL 环境变量在命令行之前处理，因此，如果 CL 和命令行之间发生任何冲突，则优先处理命令行。

## <a name="additional-compiler-topics"></a>其他编译器主题

- [快速编译](../../build/reference/fast-compilation.md)

- [CL 调用链接器](../../build/reference/cl-invokes-the-linker.md)

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)