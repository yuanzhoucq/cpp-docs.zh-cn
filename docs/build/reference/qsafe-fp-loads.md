---
title: /Qsafe_fp_loads
ms.date: 01/24/2018
ms.openlocfilehash: 57aece79dfab617121371e0489aa80f18e143372
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319325"
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

要求对浮点值使用整数移动指令，并禁用特定浮点加载优化。

## <a name="syntax"></a>语法

> **/Qsafe_fp_loads**

## <a name="remarks"></a>备注

**/Qsafe_fp_loads**才可在面向 x86 的; 它不是在面向 x64 或 ARM 的编译器中可用。

**/Qsafe_fp_loads**强制编译器使用整数移动指令而不是浮点移动指令内存和 MMX 之间移动数据寄存器。 多个控制路径中可加载的浮点值可能导致加载异常（例如 NaN 值）时，此选项还禁用这些值的寄存器加载优化。

此选项重写[/fp： 除](fp-specify-floating-point-behavior.md)。 **/Qsafe_fp_loads**指定由指定的编译器行为的子集 **/fp： 除**。

**/Qsafe_fp_loads**与不兼容[/clr](clr-common-language-runtime-compilation.md)并[/fp: fast](fp-specify-floating-point-behavior.md)。 有关浮点编译器选项的详细信息，请参阅[/fp （指定浮点行为）](fp-specify-floating-point-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++** > **命令行**属性页。

1. 输入中的编译器选项**其他选项**框。 选择**确定**以应用更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](q-options-low-level-operations.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
