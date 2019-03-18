---
title: 编译器和链接器中的 Unicode 支持
ms.date: 12/15/2017
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
helpviewer_keywords:
- Unicode, Visual C++
ms.openlocfilehash: 71458ab345670c0a5715576a7da80c4e6ff2955b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807495"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>编译器和链接器中的 Unicode 支持

大多数 Visual c + + 生成工具支持 Unicode 输入和输出。

## <a name="filenames"></a>文件名

在命令行上或编译器指令中指定的文件名 (如`#include`) 可能包含 Unicode 字符。

## <a name="source-code-files"></a>源代码文件

在标识符、 宏、 字符串和字符文本和注释支持 Unicode 字符。  也支持通用字符名称。

Unicode 可以输入到源代码文件中的以下编码：

- 具有或没有字节顺序标记 (BOM) utf-16 小 endian

- 带有或不带 BOM utf-16 大 endian

- 具有 BOM 的 utf-8

## <a name="output"></a>输出

在编译期间，编译器将诊断输出到控制台以 utf-16。  可以在控制台中显示的字符取决于控制台窗口属性。  编译器输出重定向到一个文件位于当前 ANSI 控制台代码页。

## <a name="linker-response-files-and-def-files"></a>链接器响应文件和。DEF 文件

响应文件和 DEF 文件可以是任一 utf-16 BOM，或 ANSI。

## <a name="asm-and-cod-dumps"></a>.asm 和.cod 转储

.asm 和.cod 转储为 ANSI 默认情况下，以便兼容 MASM。 使用[/fau 则](fa-fa-listing-file.md)输出 utf-8。 请注意，如果您指定 **/FAs**，混合的源只直接输出和可能看起来出现乱码，例如，如果源代码为 utf-8 并且未指定 **/fasu 时**。

## <a name="see-also"></a>请参阅

[使用命令行中的 MSVC 工具集](../building-on-the-command-line.md)