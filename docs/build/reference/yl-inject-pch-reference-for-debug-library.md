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
ms.openlocfilehash: 92e47836e0fdae077defa0fe35b515ab4ca20a66
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810284"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl（为调试库插入 PCH 引用）

**/Yl**选项在预编译标头文件中，生成唯一的符号，并使用预编译标头的所有对象文件中注入到此符号的引用。

## <a name="syntax"></a>语法

>**/Yl**
> **/Yl**_name_
> **/Yl-**

### <a name="arguments"></a>自变量

*name*<br/>
使用唯一的符号的一部分的可选名称。

*\-*<br/>
短划线 （-） 显式禁用 **/Yl**编译器选项。

## <a name="remarks"></a>备注

**/Yl**编译器选项会通过使用创建的预编译的头文件中创建唯一的符号定义[/Yc](yc-create-precompiled-header-file.md)选项。 通过使用包含预编译标头的所有文件中，对此符号的引用会自动注入[/Yu](yu-use-precompiled-header-file.md)编译器选项。 **/Yl**默认情况下启用选项时 **/Yc**用于创建预编译标头文件。

**/Yl**_名称_选项用于在预编译标头文件中创建一个易于识别的符号。 编译器将使用*名称*自变量作为符号修饰的名称的一部分创建，类似于`__@@_PchSym_@00@...@name`，其中一个唯一的编译器生成的省略号 （...） 表示字符字符串。 如果*名称*省略参数，编译器将自动生成的符号名称。 通常情况下，不需要知道的符号名称。 但是，当你的项目使用多个预编译的头文件， **/Yl**_名称_选项可能有助于确定哪个对象的文件使用的预编译标头。 可以使用*名称*作为搜索字符串的转储文件中查找符号引用。

**/Yl-** 禁用默认行为并不会将预编译标头文件中标识的符号。 包含此预编译标头的已编译的文件不会收到通用的符号引用。

当 **/Yc**未指定任何 **/Yl**选项没有任何影响，但如果指定它必须匹配任何 **/Yl**选项传递时 **/Yc**是指定。

如果您使用 **/Yl-**， **/Yc**并[/z7](z7-zi-zi-debug-information-format.md)用来创建的源代码文件的对象文件中存储用于生成预编译标头文件，调试信息选项预编译标头，而不是单独的.pdb 文件。 如果此对象文件然后将库的一部分[LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md)错误或[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)如果源文件使用创建可能出现在使用此库和预编译标头文件的生成警告预编译标头文件未定义任何符号本身。 库客户端中引用的对象文件中的任何内容时，链接器可能会从该链接，以及关联的调试信息，排除对象文件。 若要解决此问题，请指定 **/Yl** (或删除 **/Yl-** 选项) 时使用 **/Yc**创建预编译标头文件。 这可确保从包含调试信息的库对象文件获取链接在生成中。

预编译标头的详细信息，请参阅：

- [/Y（预编译标头）](y-precompiled-headers.md)

- [预编译的头文件](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 添加 **/Yl**_名称_中的编译器选项**其他选项**框。 选择“确定”以保存更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
