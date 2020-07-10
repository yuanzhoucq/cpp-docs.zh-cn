---
title: '/Ox (实现最快的优化) '
description: MSVC/Ox 选项将一些速度的编译器优化选项组合到一个选项中。
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: 10893fe1cf032f2ab56f27aa4af95b050c2ec37e
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180833"
---
# <a name="ox-enable-most-speed-optimizations"></a>`/Ox` (启用最大速度优化) 

**`/Ox`** 编译器选项启用优选速度的优化组合。 在某些版本的 Visual Studio IDE 和编译器帮助消息中，这称为 "*完全优化*"，但 **`/Ox`** 编译器选项仅启用了启用的速度优化选项的子集 **`/O2`** 。

## <a name="syntax"></a>语法

> **`/Ox`**

## <a name="remarks"></a>备注

**`/Ox`** 编译器选项启用 **`/O`** 优选速度的编译器选项。 **`/Ox`** 编译器选项不包括其他[ `/GF` (消除重复的字符串) ](gf-eliminate-duplicate-strings.md)并[ `/Gy` (启用函数级链接) ](gy-enable-function-level-linking.md)选项启用[ `/O1` 或 `/O2` (最小化大小，) 速度最大化](o1-o2-minimize-size-maximize-speed.md)。 和应用的其他选项 **`/O1`** **`/O2`** 可能会导致指向字符串的指针或用于共享目标地址的函数，这可能会影响调试和严格的语言一致性。 **`/Ox`** 选项是在不包括和的情况下启用大多数优化的简单方法 **`/GF`** **`/Gy`** 。 有关详细信息，请参阅 [`/GF`](gf-eliminate-duplicate-strings.md) 和选项的说明 [`/Gy`](gy-enable-function-level-linking.md) 。

**`/Ox`** 编译器选项与结合使用以下选项相同：

- [ `/Ob` (内联函数展开) ](ob-inline-function-expansion.md)，其中 option 参数为 2 (**`/Ob2`**) 

- [`/Oi` (生成内部函数) ](oi-generate-intrinsic-functions.md)

- [`/Ot` (代码速度优先) ](os-ot-favor-small-code-favor-fast-code.md)

- [`/Oy` (框架指针省略) ](oy-frame-pointer-omission.md)

**`/Ox`** 与以下内容互斥：

- [`/O1` (最小化大小) ](o1-o2-minimize-size-maximize-speed.md)

- [`/O2` (最大化速度) ](o1-o2-minimize-size-maximize-speed.md)

- [`/Od` (禁用 (调试) # B3](od-disable-debug.md)

如果指定，则可取消偏向 **`/Ox`** 编译器选项的速度 **`/Oxs`** ，这会将 **`/Ox`** 编译器选项与[ `/Os` (优选小代码) ](os-ot-favor-small-code-favor-fast-code.md)组合。 组合选项的代码大小更小。  **`/Oxs`** 选项与指定按 **`/Ox`** **`/Os`** 顺序显示选项的方式完全相同。

若要为发布版本应用所有可用的文件级优化，建议指定[ `/O2` (最大化速度) ](o1-o2-minimize-size-maximize-speed.md)而不是 **`/Ox`** ，并[ `/O1` (最大限度地减少大小) ](o1-o2-minimize-size-maximize-speed.md) ，而不是 **`/Oxs`** 。 为了更好地在发布版本中进行优化，还应考虑[ `/GL` (完全程序优化) ](gl-whole-program-optimization.md)编译器选项，并[ `/LTCG` (链接时代码生成) ](ltcg-link-time-code-generation.md)链接器选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **优化**" 属性页。

1. 修改 "**优化**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。

## <a name="see-also"></a>另请参阅

[`/O` (优化代码的选项) ](o-options-optimize-code.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
