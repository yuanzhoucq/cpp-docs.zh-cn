---
title: 编译器选项 |Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler
- x86 Visual C++ compiler
- ARM Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 76ab322dc4573863a30092b296e87e90c41619ab
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716204"
---
# <a name="compiler-options"></a>编译器选项

cl.exe 是控制 Microsoft Visual c + + （msvc） 编写 C 和 c + + 编译器和链接器工具。 cl.exe 可以仅在支持 Microsoft Visual Studio 的 Windows 操作系统上运行。

> [!NOTE]
> 可以仅从 Visual Studio 开发人员命令提示符启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。 有关详细信息，请参阅[命令行上的生成 C/c + + 代码](../building-on-the-command-line.md)。

编译器产生通用对象文件格式 (COFF) 对象 (.obj) 文件。 链接器生成，可执行文件 (.exe) 文件或动态链接库 (Dll)。

请注意，所有编译器选项区分大小写。 可以使用正斜杠 (`/`) 或短划线 (`-`) 来指定编译器选项。

若要编译但不链接，请使用[/c](../../build/reference/c-compile-without-linking.md)选项。

## <a name="find-a-compiler-option"></a>找到编译器选项

若要查找特定编译器选项，请参阅以下列表之一：

- [按字母顺序列出的编译器选项](../../build/reference/compiler-options-listed-alphabetically.md)

- [按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>指定编译器选项

每个编译器选项的主题讨论如何在开发环境中设置。 指定在开发环境之外的选项的信息，请参阅：

- [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)

- [CL 命令文件](../../build/reference/cl-command-files.md)

- [CL 环境变量](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>相关的生成工具

[链接器选项](../../build/reference/linker-options.md)还影响如何生成你的程序。

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[快速编译](../../build/reference/fast-compilation.md)<br/>
[CL 调用链接器](../../build/reference/cl-invokes-the-linker.md)
