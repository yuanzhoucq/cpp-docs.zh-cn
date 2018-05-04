---
title: /Tc、 /Tp、 /TC、 /TP （指定源文件类型） |Microsoft 文档
ms.date: 1/11/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
dev_langs:
- C++
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cb612d5c26fd4db51222c480539867d5e506b70
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc、/Tp、/TC、/TP（指定源文件类型）

**/Tc**选项指定其文件名参数是 C 源文件，即使它不具有扩展名为.c。 **/Tp**选项指定其文件名参数是 c + + 源文件，即使它不具有扩展名为.cpp 或.cxx 文件。 选项和文件名之间留一个空格是可选的。 每个选项指定一个文件;若要指定其他文件，重复使用此选项。

**/TC**和 **/TP**了的全局变体 **/Tc**和 **/Tp**。 它们向编译器将所有文件视为 C 源文件名为命令行上指定 (**/TC**) 或 c + + 源文件 (**/TP**)，而不考虑相对于选项在命令行上的位置。 可以在单个文件的方式上覆盖这些全局选项 **/Tc**或 **/Tp**。

## <a name="syntax"></a>语法

> **/Tc** _filename_  
> **/Tp** _filename_  
> **/TC**  
> **/TP**  

## <a name="arguments"></a>自变量

*filename*  
C 或 c + + 源文件。

## <a name="remarks"></a>备注

默认情况下， **CL**假定扩展名为.c 文件是 C 源文件，并且具有.cpp 或.cxx 扩展的文件是 c + + 源文件。

当任一**TC**或**Tc**指定选项的任何规范[/zc: wchar_t （wchar_t 是本机类型）](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)忽略选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **高级**属性页。

1. 修改**编译为**属性。 选择**确定**或**应用**要应用所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>。

## <a name="examples"></a>示例

此 CL 命令行指定 MAIN.c、 TEST.prg 和 COLLATE.prg 是所有 C 源文件。 CL 将无法识别 PRINT.prg。

> CL MAIN。C /TcTEST.PRG /TcCOLLATE.PRG 打印。PRG

此 CL 命令行指定 TEST1.c、 TEST2.cxx、 TEST3.huh 和 TEST4.o 编译为 c + + 文件，并且 TEST5.z 编译为 C 文件。

> CL TEST1。C TEST2。CXX TEST3。吧 TEST4。O /Tc TEST5。Z /TP

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
