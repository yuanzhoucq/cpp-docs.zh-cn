---
title: "编译器选项 |Microsoft 文档"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler
- x86 Visual C++ compiler
- ARM Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4addd9f5dce819f554e6ab04707929a32f7b7d9d
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2018
---
# <a name="compiler-options"></a>编译器选项

cl.exe 是控制对 Microsoft Visual c + + (MSVC) C 和 c + + 编译器和链接器工具。 cl.exe 可以仅在支持 Microsoft Visual Studio for Windows 的操作系统上运行。

> [!NOTE]  
> 只能从 Visual Studio 开发人员命令提示，可以启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。 有关详细信息，请参阅[命令行上的生成 C/c + + 代码](../building-on-the-command-line.md)。

编译器生成通用对象文件格式 (COFF) 对象 (.obj) 文件。 链接器生成可执行文件 (.exe) 文件或动态链接库 (Dll)。

请注意，所有编译器选项都都区分大小写。 你可以使用正斜杠 (`/`) 或短划线 (`-`) 来指定编译器选项。

若要编译链接的情况下，使用[/c](../../build/reference/c-compile-without-linking.md)选项。

## <a name="find-a-compiler-option"></a>查找编译器选项

若要查找特定的编译器选项，请参阅以下列表之一：

- [按字母顺序列出的编译器选项](../../build/reference/compiler-options-listed-alphabetically.md)

- [按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>指定编译器选项

每个编译器选项的主题讨论如何可以在开发环境中设置它。 指定在开发环境外的选项的信息，请参阅：

- [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)

- [CL 命令文件](../../build/reference/cl-command-files.md)

- [CL 环境变量](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>相关的生成工具

[链接器选项](../../build/reference/linker-options.md)也会影响程序的生成方式。

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
[快速编译](../../build/reference/fast-compilation.md)  
[CL 调用链接器](../../build/reference/cl-invokes-the-linker.md)  
