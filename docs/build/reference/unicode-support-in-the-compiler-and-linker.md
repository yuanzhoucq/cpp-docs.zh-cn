---
title: "编译器和链接器中的 Unicode 支持 |Microsoft 文档"
ms.custom: 
ms.date: 12/15/2017
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
dev_langs: C++
helpviewer_keywords: Unicode, Visual C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe775a53914089648a868a94aa2c863ee87790c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>编译器和链接器中的 Unicode 支持

大多数 Visual c + + 生成工具支持 Unicode 输入和输出。

## <a name="filenames"></a>文件名

在命令行上或编译器指令中指定的文件名 (如`#include`) 可能包含 Unicode 字符。

## <a name="source-code-files"></a>源代码文件

在标识符、 宏、 字符串和字符文本和注释中支持 Unicode 字符。  此外支持通用字符名称。

可作为 Unicode 输入到源代码文件中的以下编码：

- Utf-16 小 endian 字节顺序标记 (BOM) 无论

- 带有或不带 BOM utf-16 big endian

- Utf-8 与物料清单

## <a name="output"></a>输出

在编译期间，编译器将诊断输出到 utf-16 中的控制台。  可以在控制台中显示的字符取决于控制台窗口属性。  编译器输出定向到一个文件，则在当前的 ANSI 控制台代码页。

## <a name="linker-response-files-and-def-files"></a>链接器响应文件和。DEF 文件

响应文件和 DEF 文件可以是任一 utf-16 BOM，或 ANSI。

## <a name="asm-and-cod-dumps"></a>.asm 和.cod 转储

.asm 和.cod 转储是在 ANSI 默认情况下，为了与 MASM 兼容。 使用[/FAu](../../build/reference/fa-fa-listing-file.md)输出 utf-8。 请注意，如果你指定**/FAs**，混合的源只需将直接打印，并且可能看起来出现乱码，例如，如果源代码为 utf-8，且未指定**/fasu 时**。

## <a name="see-also"></a>请参阅

[在命令行上生成 C/C++ 代码](../../build/building-on-the-command-line.md)