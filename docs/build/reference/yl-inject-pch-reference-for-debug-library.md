---
title: -Yl （为调试库插入 PCH 引用） |Microsoft 文档
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yl
dev_langs:
- C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a73e79cd50343292ae63dfa831a7638d6444fc64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl（为调试库插入 PCH 引用）

**/Yl**选项在预编译标头文件中，生成唯一的符号，并使用预编译标头的所有对象文件中注入到此符号的引用。

## <a name="syntax"></a>语法

>**/Yl**  
>**/Yl**_名称_  
>**/Yl-**  

### <a name="arguments"></a>自变量

*name*  
使用唯一的符号的一部分的可选名称。

*\-*  
短划线 （-） 显式禁用 **/Yl**编译器选项。

## <a name="remarks"></a>备注

**/Yl**编译器选项通过使用创建的预编译的头文件中创建唯一的符号定义[/Yc](../../build/reference/yc-create-precompiled-header-file.md)选项。 通过使用包括预编译标头的所有文件中自动注入到此符号的引用[/Yu](../../build/reference/yu-use-precompiled-header-file.md)编译器选项。 **/Yl**默认情况下启用选项时 **/Yc**用于创建预编译的头文件。

**/Yl**_名称_选项用于创建预编译的头文件中的身份的符号。 编译器使用*名称*自变量作为修饰的符号名称的一部分创建，类似于\_ \_ @@ \_PchSym\_@00@..。 @*名称*，其中一个唯一的编译器生成省略号 （...） 表示字符字符串。 如果*名称*省略自变量，编译器会自动生成的符号名称。 通常情况下，不需要知道的符号的名称。 但是，当你的项目使用多个预编译的头文件， **/Yl**_名称_选项可能有助于确定哪些对象文件使用的预编译标头。 你可以使用*名称*作为搜索字符串在转储文件中查找符号引用。

**/Yl-** 禁用默认行为并不会将预编译标头文件中标识的符号。 包括此预编译标头的已编译的文件并不获取通用的符号引用。

当 **/Yc**未指定任何 **/Yl**选项不起作用，但如果指定它必须匹配任何 **/Yl**选项传递时 **/Yc**是指定。

如果你使用 **/Yl-**， **/Yc**和[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)选项生成预编译标头文件，调试信息存储在对象文件中用于创建源文件的文件名预编译标头，而不是单独的.pdb 文件。 如果此对象文件然后进行的库的一部分[LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md)错误或[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)如果源文件用于创建，可以使用此库和预编译标头文件的生成中出现警告预编译的头文件未定义任何符号本身。 在对象文件中为 nothing 引用在库客户端时，链接器可能从该链接，以及关联的调试信息，排除对象文件。 若要解决此问题，请指定 **/Yl** (或删除 **/Yl-** 选项) 时使用 **/Yc**创建预编译标头文件。 这可确保在生成中获取链接的包含调试信息的库中的对象文件。

预编译标头的详细信息，请参阅：

- [/Y（预编译标头）](../../build/reference/y-precompiled-headers.md)

- [创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 添加 **/Yl**_名称_中的编译器选项**其他选项**框。 选择**确定**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
