---
title: "-Oy （框架指针省略） |Microsoft 文档"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
dev_langs:
- C++
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15a760d1a9df383356ead2eb2d1e1b08e8b9ca57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="oy-frame-pointer-omission"></a>/Oy（框架指针省略）

禁止在调用堆栈上创建帧指针。

## <a name="syntax"></a>语法

> /Oy [-]

## <a name="remarks"></a>备注

此选项可以加快函数调用的速度，因为无需设置和移除任何框架指针。 它还可以使一个或多个寄存器（Intel 386 或更高版本上的 EBP）空闲出来，以便存储频繁使用的变量和子表达式。

**/Oy**启用框架指针省略和**/Oy-**禁止省略。 **/Oy**仅适用于 x86 编译器。

如果你的代码需要基于 EBP 的寻址，你可以指定**/Oy-**选项后**/Ox**选项或使用[优化](../../preprocessor/optimize.md)与"**y**"和**关闭**自变量以获取使用基于 EBP 的寻址的最大优化。 编译器可检测大部分需要基于 EBP 的寻址的情况（例如，使用 `_alloca` 和 `setjmp` 函数以及使用结构化异常处理的情况）。

[/Ox （启用最速度优化）](../../build/reference/ox-full-optimization.md)和[/O1、 /O2 （最小化大小、 最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)选项暗含**/Oy**。 指定**/Oy-**后**/Ox**， **/O1**，或**/O2**选项禁用**/Oy**，无论它是显式或隐式。

**/Oy**编译器选项使得调试器更加难以使用，因为编译器取消显示帧指针信息。 如果指定 debug 编译器选项 ([/Z7、 /Zi、 /ZI](../../build/reference/z7-zi-zi-debug-information-format.md))，我们建议您指定**/Oy-**在任何其他优化编译器选项后的选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**优化**属性页。

1. 修改**省略框架指针**属性。 此属性仅添加或移除**/Oy**选项。 如果你想要添加**/Oy-**选项，请单击**命令行**和修改**其他选项**。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>。

## <a name="see-also"></a>请参阅

[/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)

[编译器选项](../../build/reference/compiler-options.md)

[设置编译器选项](../../build/reference/setting-compiler-options.md)