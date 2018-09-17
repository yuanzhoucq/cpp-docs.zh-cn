---
title: C/c + + 生成参考 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 116ddca6ed9f5e0b3ea02652958931f88cc8fc13
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703217"
---
# <a name="cc-building-reference"></a>C/C++ 生成参考

Visual c + + 提供了两个方法来生成 C/c + + 程序。 最简单的 （也是最常见的） 方法是[Visual c + + 开发环境中生成](../../ide/building-cpp-projects-in-visual-studio.md)。 另一种方法是向[中的命令提示符下使用命令行工具生成](../../build/building-on-the-command-line.md)。 在任一情况下，可以创建使用 Visual c + + 源代码编辑器或所选的第三方编辑器的源文件。

如果程序使用生成文件而不是.vcxproj 文件，则仍可以生成它在开发环境中作为[外部项目](../../ide/building-external-projects.md)。

## <a name="in-this-section"></a>本节内容

[编译 C/c + + 程序](../../build/reference/compiling-a-c-cpp-program.md)介绍，编译器可创建包含计算机代码、 链接器指令、 部分、 外部引用和函数/数据名称的对象文件。

[链接](../../build/reference/linking.md)描述链接器，用于组合中的代码由编译器创建的对象文件以及从静态链接的库，解析的名称引用，并创建一个可执行文件。

[发行版本](../../build/reference/release-builds.md)显示原因和时间你想要从调试版本更改为发布版本的信息，并探讨一些从调试版本更改为发布版本时可能遇到的问题。

[优化代码](../../build/reference/optimizing-your-code.md)提供指向讨论如何优化代码的机制：

[C/c + + 生成工具](../../build/reference/c-cpp-build-tools.md)用于查看或操作生成输出中提供了以下的命令行工具：

[C/c + + 生成错误](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)引入了生成错误的部分表中的内容。

## <a name="related-sections"></a>相关章节

[C/c + + 预处理器参考 》](../../preprocessor/c-cpp-preprocessor-reference.md)讨论预处理器，通过转换宏、 运算符和指令准备编译器的源文件。

[了解自定义生成步骤和生成事件](../../ide/understanding-custom-build-steps-and-build-events.md)讨论自定义生成过程。

[生成 C/c + + 程序](../../build/building-c-cpp-programs.md)提供一些链接，这些主题描述了构建应用程序从命令行或从 Visual Studio 集成的开发环境。

[设置编译器选项](../../build/reference/setting-compiler-options.md)描述如何在开发环境中或在命令行上设置编译器选项。

[编译器选项](../../build/reference/compiler-options.md)提供指向讨论如何使用编译器选项。

[设置链接器选项](../../build/reference/setting-linker-options.md)描述如何设置链接器选项内部或外部的集成的开发环境。

[链接器选项](../../build/reference/linker-options.md)提供指向讨论如何使用链接器选项。

[BSCMAKE 参考](../../build/reference/bscmake-reference.md)介绍 Microsoft 浏览信息维护实用工具 (BSCMAKE。Exe 文件），哪些.sbr 从生成浏览信息文件 (.bsc) 在编译期间创建的文件。

[LIB 引用](../../build/reference/lib-reference.md)介绍的 Microsoft 库管理器 (LIB.exe)，将创建并管理通用对象文件格式 (COFF) 对象文件的库。

[EDITBIN 参考](../../build/reference/editbin-reference.md)介绍 Microsoft COFF 二进制文件编辑器 (EDITBIN。Exe 文件），它修改通用对象文件格式 (COFF) 的二进制文件。

[DUMPBIN 参考](../../build/reference/dumpbin-reference.md)介绍 Microsoft COFF 二进制文件转储器 (DUMPBIN。Exe 文件），其中显示有关通用对象文件格式 (COFF) 的二进制文件的信息。

[NMAKE 参考](../../build/nmake-reference.md)介绍了 Microsoft 程序维护实用工具 (NMAKE。Exe 文件），这是一种工具生成的项目，根据说明文件中包含的命令。