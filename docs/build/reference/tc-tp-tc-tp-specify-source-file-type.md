---
title: /Tc、/Tp、/TC、/TP（指定源文件类型）
ms.date: 1/11/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.openlocfilehash: f7ee51c858c9f90440cf0c2b21799ef7473cf6da
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813859"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc、/Tp、/TC、/TP（指定源文件类型）

**/Tc**选项指定其文件名参数是 C 源文件，即使它不具有扩展名为.c。 **/Tp**选项指定其文件名参数是 c + + 源文件，即使它没有.cpp 或.cxx 扩展名。 选项和文件名之间留一个空格是可选的。 每个选项指定一个文件;若要指定其他文件，重复使用此选项。

**/TC**并 **/TP**是全局的变体 **/Tc**并 **/Tp**。 指定编译器将为 C 源文件名为命令行上的所有文件 (**/TC**) 或 c + + 源文件 (**/TP**)，而不考虑相对于选项在命令行上的位置。 这些全局选项可以通过单个文件重写 **/Tc**或 **/Tp**。

## <a name="syntax"></a>语法

> **/Tc** _filename_
>  **/Tp** _filename_
>  **/TC**
>  **/TP**

## <a name="arguments"></a>自变量

*filename*<br/>
C 或 c + + 源文件。

## <a name="remarks"></a>备注

默认情况下**CL**假设文件扩展名为.c 已 C 源文件，并将带有.cpp 或.cxx 扩展名的文件的 c + + 源文件。

当任一**TC**或**Tc**指定选项的任何规范[/zc: wchar_t （wchar_t 是本机类型）](zc-wchar-t-wchar-t-is-native-type.md)选项将被忽略。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **高级**属性页。

1. 修改**编译为**属性。 选择**确定**或**应用**应用所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>。

## <a name="examples"></a>示例

此 CL 命令行指定 MAIN.c、 TEST.prg 和 COLLATE.prg 是所有的 C 源文件。 CL 将无法识别 PRINT.prg。

> CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG

此 CL 命令行指定 TEST1.c、 TEST2.cxx、 TEST3.huh 和 TEST4.o 编译为 c + + 文件，并作为 C 文件编译 TEST5.z。

> CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
