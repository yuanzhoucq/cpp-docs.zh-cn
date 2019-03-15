---
title: C/c + + 生成参考-Visual Studio
description: C/c + + 项目系统和生成工具在 Visual Studio 中的参考内容。
ms.date: 12/10/2018
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
ms.openlocfilehash: 4c3f7aa598a9c43af04c148ed0d4b3f555566ec7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812481"
---
# <a name="cc-building-reference"></a>C/C++ 生成参考

Visual c + + 提供了两个方法来生成 C/c + + 程序。 最简单的 （也是最常见的） 方法是[Visual Studio IDE 中生成](../creating-and-managing-visual-cpp-projects.md)。 另一种方法是向[中的命令提示符下使用命令行工具生成](../building-on-the-command-line.md)。 在任一情况下，可以创建和编辑使用 Visual Studio 或所选的第三方编辑器的源文件。

## <a name="in-this-section"></a>本节内容

[C + + 项目的 MSBuild 参考](msbuild-visual-cpp-overview.md)

[MSVC 编译器的引用](compiling-a-c-cpp-program.md)<br/>
介绍 MSVC 编译器，创建一个包含计算机代码、 链接器指令、 部分、 外部引用和函数/数据名称的对象文件。

[MSVC 链接器引用](linking.md)<br/>
描述链接器，用于组合中的代码由编译器创建的对象文件以及从静态链接的库，解析的名称引用，并创建一个可执行文件。

[编译器和链接器中的 Unicode 支持](unicode-support-in-the-compiler-and-linker.md)

[其他 MSVC 生成工具](c-cpp-build-tools.md)<br/>
C + + 的其他命令行工具。

[C/C++ 生成错误](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)<br/>
引入了生成错误的部分表中的内容。

## <a name="related-sections"></a>相关章节

[C/C++ 预处理器参考](../../preprocessor/c-cpp-preprocessor-reference.md)<br/>
讨论预处理器，通过转换宏、 运算符和指令准备编译器的源文件。

[了解自定义生成步骤和生成事件](../understanding-custom-build-steps-and-build-events.md)<br/>
讨论自定义生成过程。

[生成 C/c + + 程序](../projects-and-build-systems-cpp.md)<br/>
提供一些链接，它们指向描述如何从命令行或 Visual Studio 的集成开发环境构建程序的主题。

[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
描述如何在开发环境中或命令行上设置编译器选项。

[MSVC 编译器选项](compiler-options.md)<br/>
提供指向讨论如何使用编译器选项。

[MSVC 链接器引用](linking.md)<br/>
描述如何设置链接器选项内部或外部的集成的开发环境。

[MSVC 链接器选项](linker-options.md)<br/>
提供指向讨论如何使用链接器选项。

[BSCMAKE 参考](bscmake-reference.md)<br/>
介绍 Microsoft 浏览信息维护实用工具 (BSCMAKE。Exe 文件），哪些.sbr 从生成浏览信息文件 (.bsc) 在编译期间创建的文件。

[LIB 引用](lib-reference.md)<br/>
介绍 Microsoft 库管理器 (LIB.exe)，将创建并管理通用对象文件格式 (COFF) 对象文件的库。

[EDITBIN 参考](editbin-reference.md)<br/>
介绍 Microsoft COFF 二进制文件编辑器 (EDITBIN。Exe 文件），它修改通用对象文件格式 (COFF) 的二进制文件。

[DUMPBIN 参考](dumpbin-reference.md)<br/>
介绍 Microsoft COFF 二进制文件转储器 (DUMPBIN。Exe 文件），其中显示有关通用对象文件格式 (COFF) 的二进制文件的信息。

[NMAKE 参考](nmake-reference.md)<br/>
介绍了 Microsoft 程序维护实用工具 (NMAKE。Exe 文件），这是一种工具生成的项目，根据说明文件中包含的命令。
