---
title: "-Yl （为调试库插入 PCH 引用） |Microsoft 文档"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /yl
dev_langs: C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e777977f6d869d2bbc28d980f6445851e54396b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl（为调试库插入 PCH 引用）

**/Yl**选项创建预编译的头文件的公共符号，并插入到此符号在使用预编译标头的所有文件的引用。 这使得预编译标头符号的完整类型信息中使用预编译标头的所有文件的调试器。 默认情况下会启用此选项。 使用此选项可以防止由于缺少链接使用预编译标头的库中的调试信息的链接器错误。

## <a name="syntax"></a>语法

>**/Yl**  
>**/Yl**_名称_  
>**/Yl-**  

### <a name="arguments"></a>自变量

*name*  
用于定义的符号的定义或使用预编译标头的存储且在被引用的对象文件是一个可选名称。

*\-*  
短划线 （-） 显式禁用**/Yl**编译器选项。

## <a name="remarks"></a>备注

**/Yl**选项支持调试器预编译标头中包含预编译标头的每个文件中获取有关类型的完整信息。 此选项将创建一个内部的符号名称，插入用于创建预编译标头，方法的对象文件中的符号定义[/Yc](../../build/reference/yc-create-precompiled-header-file.md)选项，然后插入到包括预编译的所有文件中的符号引用通过使用的标头[/Yu](../../build/reference/yu-use-precompiled-header-file.md)编译器选项。 由于使用预编译标头的所有源文件都引用命名符号，因此链接器将始终链接定义符号和关联的预编译的头调试信息的对象文件。 默认情况下会启用此选项。

**/Yl**_名称_选项用于显式创建预编译的头文件的标识符号。 编译器使用*名称*参数，以创建符号类似于\_ \_ @@ \_PchSym\_@00@..。 @*名称*，其中的省略号 （…） 链接器生成的表示字符字符串。 如果省略该参数，编译器会自动生成的符号名称。

**/Yl-**禁用默认行为并不会将包含预编译标头的对象文件中标识的符号引用。 此选项可能需要的文件不存在的预编译标头文件编译。

如果你使用**/Yl-**， **/Yc**和[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)选项以构建的库，编译器创建一个包含存储中的调试信息的预编译标头文件对象文件而不是.pdb 文件。 [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md)错误或[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)警告可以发生在使用此库的版本中，如果源文件用于创建预编译标头的预编译标头不定义任何符号。 链接器可能排除此库对象文件的链接，以及关联的预编译标头的调试信息，在对象文件中为 nothing 由引用库客户端。 若要解决此问题，请指定**/Yl**当你使用**/Yc**创建预编译标头文件和**/Yu**若要使用它。 这可确保，在生成中包括包含调试信息的对象文件。

预编译标头的详细信息，请参阅：

- [/Y（预编译标头）](../../build/reference/y-precompiled-headers.md)

- [创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**命令行**中的属性页**C/c + +**文件夹。

1. 添加**/Yl**_名称_中的编译器选项**其他选项**框。 选择**确定**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
