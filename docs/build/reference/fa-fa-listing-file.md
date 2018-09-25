---
title: /FA、 /Fa （列出文件） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs:
- C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9f1d205eff155b628081c5bc615570c44a88f08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412803"
---
# <a name="fa-fa-listing-file"></a>/FA、/Fa（列出文件）

创建包含组装器代码的列表文件。

## <a name="syntax"></a>语法

> **/FA**[**c**\][**s**\][**u**] **/Fa**_路径名_

## <a name="remarks"></a>备注

**/FA**编译器选项为每个翻译单元中在编译中，通常对应于 C 或 c + + 源文件生成组装器列表文件。 默认情况下，仅组装器会包含在列表文件中，编码为 ANSI。 可选**c**， **s**，并**u**参数 **/FA**控件是否机器代码或源代码以及汇编程序输出列出，并且是否在列表编码为 utf-8。

默认情况下，每个列表文件获取与源文件相同的基名称和扩展名为.asm。 当机器代码包含使用**c**选项，列表文件的扩展名为.cod。 您可以更改的名称和扩展名的列表文件并创建使用的目录 **/Fa**选项。

### <a name="fa-arguments"></a>/FA 参数

无<br/>
只是组装器语言包含在列表中。

**c**<br/>
可选。 在列表中包括计算机代码。

**秒**<br/>
可选。 在列表中包含源代码。

**u**<br/>
可选。 编码 utf-8 格式的列表文件，并包含字节顺序标记。 默认情况下，该文件编码为 ANSI。 使用`u`创建列表文件的任何系统上正确显示，或者如果使用 Unicode 作为编译器的输入源代码文件。

如果这两个**s**并**u**指定，且如果源代码文件使用 Unicode 编码，而不是 utf-8，则.asm 文件中的代码行可能无法正确显示。

### <a name="fa-argument"></a>/Fa 参数

无<br/>
一个*源*为每个源代码文件编译中创建.asm 文件。

*filename*<br/>
名为的列表文件*文件名*.asm 放在当前目录中。 编译单个源代码文件时，此值才有效。

*将文件名.扩展名*<br/>
名为的列表文件*文件名.扩展名*位于当前目录中。 编译单个源代码文件时，此值才有效。

*目录*__\\__<br/>
一个*source_file*创建.asm 文件并将其放在指定*directory*为编译中每个源代码文件。 请注意所需的尾随反斜杠。 允许仅在当前磁盘上的路径。

*目录*__\\__*文件名*<br/>
名为的列表文件*文件名*.asm 放在指定*directory*。 编译单个源代码文件时，此值才有效。

*目录*__\\__*文件名.扩展名*<br/>
名为的列表文件*文件名.扩展名*放置在指定*directory*。 编译单个源代码文件时，此值才有效。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

2. 选择**配置属性** > **C/c + +** > **输出文件**属性页。

3. 修改**汇编程序输出**属性来设置 **/FAc**并 **/FAs**组装器、 计算机和源代码的选项。 修改**使用 Unicode 对于组装器列出**属性来设置 **/fau 则**ANSI 或 utf-8 输出的选项。 修改**ASM 列表位置**若要设置 **/Fa**用于列出文件的名称和位置选项。

请注意，将设置两者**汇编程序输出**并**使用 Unicode 对于组装器列出**属性可能会导致[命令行警告 D9025](../../error-messages/tool-errors/command-line-warning-d9025.md)。 若要组合在 IDE 中的这些选项，使用**其他选项**字段中**命令行**属性页相反。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>。 若要指定 **/fau 则**，请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="example"></a>示例

下面的命令行生成合并的源和机器代码列表调用 HELLO.cod:

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](../../build/reference/output-file-f-options.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[指定路径名](../../build/reference/specifying-the-pathname.md)