---
title: "-Ox （启用大多数速度优化） |Microsoft 文档"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /ox
dev_langs:
- C++
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85efa8a2beab34d0dcf1bdb74e3cf89008b10d6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox （启用大多数速度优化）

**/Ox**编译器选项启用的优选速度的优化的组合。 在某些版本的 Visual Studio IDE 和编译器帮助消息，这被称为*完全优化*，但**/Ox**编译器选项，可以仅由启用的速度优化选项的子集**/O2**。

## <a name="syntax"></a>语法

> /Ox

## <a name="remarks"></a>备注

**/Ox**编译器选项启用**/O**编译器选项，该优选速度。 **/Ox**编译器选项不包括的附加[/GF （消除重复字符串）](../../build/reference/gf-eliminate-duplicate-strings.md)和[/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md) 由启用的选项[/O1 或 /O2 （最小化大小、 最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。 应用的其他选项**/O1**和**/O2**可能会导致指向字符串或共享的目标地址，这可能会影响调试和严格语言一致性的函数。 **/Ox**选项是不包括的情况下启用大多数优化的简单办法**/GF**和**/Gy**。 有关详细信息，请参阅说明[/GF](../../build/reference/gf-eliminate-duplicate-strings.md)和[/Gy](../../build/reference/gy-enable-function-level-linking.md)选项。

**/Ox**编译器选项等同于结合使用以下选项：

- [/Ob （内联函数扩展）](../../build/reference/ob-inline-function-expansion.md)，其中选项参数是 2 (**/Ob2**)

- [/Og （全局优化）](../../build/reference/og-global-optimizations.md)

- [/Oi （生成内部函数）](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot （代码快速代码）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy （框架指针省略）](../../build/reference/oy-frame-pointer-omission.md)

**/Ox**互斥从：

- [/O1 （最小化大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/O2 （最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od （禁用 （调试））](../../build/reference/od-disable-debug.md)

你可以取消的速度趋向偏差**/Ox**编译器选项，如果你指定**/Oxs**，它结合**/Ox**编译器选项与[/Os （优先小代码）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。 结合使用的选项倾向于代码大小更小。

若要应用的发布版本中所有可用的文件级优化，我们建议你指定[/O2 （最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)而不是**/Ox**，和[/O1 （最小化大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)改为**/Oxs**。 为版本中的更多优化版本，还应考虑[/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)编译器选项和[/LTCG （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)链接器选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 下**配置属性**，打开**C/c + +** ，然后选择**优化**属性页。

1. 修改**优化**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。

## <a name="see-also"></a>请参阅

[/O 选项 （优化代码）](../../build/reference/o-options-optimize-code.md)  
[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)