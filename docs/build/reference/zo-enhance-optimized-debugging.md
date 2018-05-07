---
title: -Zo （增强优化调试） |Microsoft 文档
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
ms.openlocfilehash: 013738ab05bf67d3db066d94d32d398a0555c55e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo（增强优化调试）
在非调试生成中为优化代码生成增强调试信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
/Zo[-]  
```  
  
## <a name="remarks"></a>备注  
 **/Zo**编译器开关生成为优化代码的增强调试信息。 优化可能为本地变量、代码重新排序、向量化循环和内联函数调用使用寄存器。 这些优化可能会掩盖的源代码和编译的对象代码之间的关系。 **/Zo**开关通知编译器生成其他本地变量和内联的函数的调试信息。 使用它查看中的变量**自动**，**局部变量**，和**监视**windows 当逐句通过优化在 Visual Studio 调试器中的代码。 它还启用堆栈跟踪以在 WinDBG 调试器中显示内联的函数。 调试版本，已禁用优化 ([/Od](../../build/reference/od-disable-debug.md)) 不需要时生成的其他调试信息 **/Zo**指定。 使用 **/Zo**开关来调试启用优化的发布配置。 有关优化开关的详细信息，请参阅[/O 选项 （优化代码）](../../build/reference/o-options-optimize-code.md)。 **/Zo**指定调试信息时，默认情况下，Visual Studio 中启用的选项 **/Zi**或 **/Z7**。 指定 **/Zo-** 若要显式禁用此编译器选项。  
  
 **/Zo**开关也可从 Visual Studio 2013 Update 3 开始，并且会替换先前未记录 **/d2Zi+** 切换。  
  
### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /Zo 编译器选项  
  
1.  打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**配置属性**， **C/c + +** 文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  修改**其他选项**属性以包含`/Zo`，然后选择**确定**。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [/O 选项 （优化代码）](../../build/reference/o-options-optimize-code.md)   
 [/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)   
 [编辑并继续](/visualstudio/debugger/edit-and-continue)