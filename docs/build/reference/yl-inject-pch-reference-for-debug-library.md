---
title: /Yl（为调试库插入 PCH 引用）
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: 816ba66c94e616407a8891cd149a41e44e29358d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825712"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl（为调试库插入 PCH 引用）

**/Yl**选项会在预编译头文件中生成唯一符号，并在使用预编译标头的所有对象文件中插入对此符号的引用。

## <a name="syntax"></a>语法

>**/Yl**\
>**/Yl**_名称_\
>**/Yl-**

### <a name="arguments"></a>参数

*name*<br/>
用作唯一符号的一部分的可选名称。

*\-*<br/>
破折号（-）显式禁用 **/Yl**编译器选项。

## <a name="remarks"></a>备注

**/Yl**编译器选项在使用[/yc](yc-create-precompiled-header-file.md)选项创建的预编译头文件中创建唯一的符号定义。 使用[/yu](yu-use-precompiled-header-file.md)编译器选项可在包含预编译标头的所有文件中自动注入对此符号的引用。 当使用 **/yc**创建预编译头文件时，默认情况下启用 **/Yl**选项。

**/Yl**_name_选项用于在预编译头文件中创建可识别的符号。 编译器使用*name*参数作为其创建的修饰符号名称的一部分，类似于`__@@_PchSym_@00@...@name`，其中省略号（...）表示编译器生成的唯一字符串。 如果省略*name*参数，编译器将自动生成符号名称。 通常情况下，不需要知道符号的名称。 但是，当你的项目使用多个预编译头文件时， **/Yl**_name_选项可能会很有用，可以确定哪些对象文件使用哪个预编译标头。 您可以使用*name*作为搜索字符串来查找转储文件中的符号引用。

**/Yl-** 禁用默认行为，且不会在预编译头文件中放置标识符号。 包含此预编译头的已编译文件不会获取公共符号引用。

如果未指定 **/yc** ，则任何 **/Yl**选项都不起作用，但如果指定，则它必须与指定 **/Yc**时传递的任何 **/Yl**选项匹配。

如果使用 **/Yl-**、 **/yc**和[/Z7](z7-zi-zi-debug-information-format.md)选项生成预编译头文件，调试信息将存储在用于创建预编译标头的源文件的对象文件中，而不是存储在单独的 .pdb 文件中。 如果将此对象文件作为库的一部分，则在使用此库和预编译标头文件的生成中可能会发生[LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md)错误或[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)警告（如果用于创建预编译标头文件的源文件未定义任何符号本身）。 如果未在库客户端中引用对象文件中的任何内容，则链接器可能会从链接中排除对象文件，以及关联的调试信息。 若要解决此问题，请在使用 **/yc**创建预编译头文件时指定 **/Yl** （或删除 **/Yl-** 选项）。 这确保了包含调试信息的库中的对象文件会在您的生成中链接在一起。

有关预编译标头的详细信息，请参阅：

- [/Y（预编译标头）](y-precompiled-headers.md)

- [预编译标头文件](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > " "**c/c + +** > **命令行**" 属性页。

1. 在 "**附加选项**" 框中添加 **/Yl**_name_编译器选项。 选择“确定”以保存更改****。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
