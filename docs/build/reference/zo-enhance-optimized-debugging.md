---
title: -Zo （增强优化调试） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- -Zo
- /Zo
dev_langs:
- C++
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b40f7b4fff1d6df6f5fb818e090ce687f12a7b4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412782"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo（增强优化调试）

在非调试生成中为优化代码生成增强调试信息。

## <a name="syntax"></a>语法

```cpp
/Zo[-]
```

## <a name="remarks"></a>备注

**/Zo**编译器开关生成增强为优化代码的调试信息。 优化可能为本地变量、代码重新排序、向量化循环和内联函数调用使用寄存器。 这些优化可能会掩盖的源代码和编译的对象代码之间的关系。 **/Zo**开关告诉编译器生成本地变量和内联的函数的更多调试信息。 使用它来查看中的变量**自动**，**局部变量**，并**观看**windows 时单步执行时优化 Visual Studio 调试器中的代码。 它还启用堆栈跟踪以在 WinDBG 调试器中显示内联的函数。 调试已禁用优化的版本 ([/Od](../../build/reference/od-disable-debug.md)) 不需要时生成的其他调试信息 **/Zo**指定。 使用 **/Zo**开关来调试发布配置在启用优化。 有关优化开关的详细信息，请参阅[/O 选项 （优化代码）](../../build/reference/o-options-optimize-code.md)。 **/Zo**指定与调试信息时，Visual Studio 中默认情况下启用的选项 **/Zi**或 **/z7**。 指定 **/Zo-** 若要显式禁用此编译器选项。

**/Zo**切换在 Visual Studio 2013 Update 3，从开始提供，它将替换先前未记录 **/d2Zi+** 切换。

### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /Zo 编译器选项

1. 打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性**， **C/c + +** 文件夹。

1. 选择**命令行**属性页。

1. 修改**其他选项**属性以包含`/Zo`，然后选择**确定**。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)<br/>
[/Z7、/Zi、/ZI（调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)<br/>
[编辑并继续](/visualstudio/debugger/edit-and-continue)