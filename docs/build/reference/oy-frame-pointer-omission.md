---
title: /Oy（框架指针省略）
ms.date: 11/19/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
ms.openlocfilehash: 343b0e026c2932e97d4a8d4472ba2035d6302661
ms.sourcegitcommit: 3da2cb3ec85e77ddfd4d2a55edb133d580ce4f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2018
ms.locfileid: "52330385"
---
# <a name="oy-frame-pointer-omission"></a>/Oy（框架指针省略）

禁止在调用堆栈上创建帧指针。

## <a name="syntax"></a>语法

> /Oy [-]

## <a name="remarks"></a>备注

此选项可以加快函数调用的速度，因为无需设置和移除任何框架指针。 它还可以使一个或多个寄存器用于常规用途。

**/Oy**启用帧指针省略和 **/Oy-** 禁止省略。 在 x64 编译器中， **/Oy**并 **/Oy-** 不可用。

如果你的代码需要基于帧的寻址，您可以指定 **/Oy-** 选项后 **/Ox**选项，或使用[优化](../../preprocessor/optimize.md)与"**y**"和**关闭**参数以获取基于帧的寻址的最大优化。 编译器检测到大多数情况下，基于帧的寻址在需要时 (例如，使用`_alloca`和`setjmp`函数和结构化的异常处理)。

[/Ox （启用最速度优化）](../../build/reference/ox-full-optimization.md)并[/o1，/o2 （最小化大小、 最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)选项暗含 **/Oy**。 指定 **/Oy-** 后 **/Ox**， **/o1**，或者 **/o2**选项禁用 **/Oy**，无论它是显式或隐式。

**/Oy**编译器选项使得调试器更加难以使用，因为编译器取消显示帧指针信息。 如果指定 debug 编译器选项 ([/Z7、 /Zi、 /ZI](../../build/reference/z7-zi-zi-debug-information-format.md))，我们建议您指定 **/Oy-** 后任何其他优化编译器选项的选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **优化**属性页。

1. 修改**省略框架指针**属性。 此属性仅添加或移除 **/Oy**选项。 如果你想要添加 **/Oy-** 选项，选中**命令行**属性页，并修改**其他选项**。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>。

## <a name="see-also"></a>请参阅

[/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
