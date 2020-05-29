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
ms.openlocfilehash: 420b01263320cf86df3f99da4523cc2b8bb4d4b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168832"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>编译器和链接器中的 Unicode 支持

大多数视觉C++对象生成工具都支持 Unicode 输入和输出。

## <a name="filenames"></a>文件名

在命令行上或在编译器指令中指定的文件名（如 `#include`）可能包含 Unicode 字符。

## <a name="source-code-files"></a>源代码文件

标识符、宏、字符串和字符文本以及注释中支持 Unicode 字符。  还支持通用字符名称。

Unicode 可以在源代码文件中输入以下编码：

- 具有或不具有字节顺序标记（BOM）的 UTF-16 little endian

- 带有或不带 BOM 的 UTF-16 大 endian

- UTF-8 with BOM

## <a name="output"></a>输出

在编译期间，编译器会将诊断输出到 UTF-16 中的控制台。  可以在控制台中显示的字符取决于控制台窗口属性。  重定向到文件的编译器输出在当前 ANSI 控制台代码页中。

## <a name="linker-response-files-and-def-files"></a>链接器响应文件和。DEF 文件

响应文件和 DEF 文件可以是具有 BOM 的 UTF-16 或 ANSI。

## <a name="asm-and-cod-dumps"></a>.asm 和. 货转储

默认情况下，.asm 和. 货到的转储在 ANSI 中是为了与 MASM 兼容。 使用[/FAu](fa-fa-listing-file.md)输出 utf-8。 请注意，如果指定 **/FAs**，则只会直接打印混合源，并且可能会出现乱码，例如，如果源代码为 utf-8，而你未指定 **/FAsu**。

## <a name="see-also"></a>另请参阅

[通过命令行使用 MSVC 工具集](../building-on-the-command-line.md)
