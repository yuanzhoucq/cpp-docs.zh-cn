---
title: MSVC 编译器选项
ms.date: 01/29/2018
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
ms.openlocfilehash: 831aade72cd728ec42aee5ef1f320deb7bdf173d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294260"
---
# <a name="compiler-options"></a>编译器选项

cl.exe 是一个控制 Microsoft Visual C ++（MSVC）C 和 C ++ 编译器和链接器的工具。 cl.exe 只能在支持 Microsoft Visual Studio for Windows 的操作系统上运行。

> [!NOTE]
> 只能从 Visual Studio 开发人员命令提示符启动此工具。 无法从系统命令提示符或文件资源管理器中启动它。 有关详细信息，请参阅[使用命令行中的 MSVC 工具集](../building-on-the-command-line.md)。

编译器生成通用对象文件格式（COFF）对象（.obj）文件。 链接器生成可执行（.exe）文件或动态链接库（DLL）。

请注意，所有编译器选项都区分大小写。 可以使用正斜杠（`/`）或短划线（`-`）来指定编译器选项。

要在不链接的情况下进行编译，请使用[/c](c-compile-without-linking.md)选项。

## <a name="find-a-compiler-option"></a>查找编译器选项

若要查找特定编译器选项，请参阅以下列表之一：

- [按字母顺序列出的编译器选项](compiler-options-listed-alphabetically.md)

- [按类别列出的编译器选项](compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>指定编译器选项

每个编译器选项的主题讨论如何在开发环境中设置。 指定在开发环境之外的选项的信息，请参阅：

- [MSVC 编译器命令行语法](compiler-command-line-syntax.md)

- [CL 命令文件](cl-command-files.md)

- [CL 环境变量](cl-environment-variables.md)

## <a name="related-build-tools"></a>相关的生成工具

[MSVC 链接器选项](linker-options.md)还影响如何生成你的程序。

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](c-cpp-building-reference.md)<br/>
[CL 调用链接器](cl-invokes-the-linker.md)
