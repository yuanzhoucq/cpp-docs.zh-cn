---
title: /O1、/O2（最小化大小、最大化速度）
description: MSVC 编译器 options/O1 和/O2 指定最小大小或最大速度的所有优化。
ms.date: 07/08/2020
f1_keywords:
- /O2
- /O1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: c1eda8395e604468cbb23572ec930d6171984fe4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180898"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>`/O1`， `/O2` (最小化大小、最大化速度) 

选择一组会影响生成的代码的大小和速度的预定义选项。

## <a name="syntax"></a>语法

> **`/O1`**\
> **`/O2`**

## <a name="remarks"></a>备注

**`/O1`** 和 **`/O2`** 编译器选项是一次设置多个特定优化选项的快速方法。 **`/O1`** 选项设置在大多数情况下创建最小代码的各个优化选项。 **`/O2`** 选项设置在大多数情况下创建最快代码的选项。 **`/O2`** 选项是发布版本的默认选项。 下表显示了由和设置的特定选项 **`/O1`** **`/O2`** ：

| 选项 | 等效于 |
|--|--|
| **`/O1`** (最小化大小)  | [`/Og`](og-global-optimizations.md) [`/Os`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |
| **`/O2`** (最大化速度)  | [`/Og`](og-global-optimizations.md) [`/Oi`](oi-generate-intrinsic-functions.md) [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |

**`/O1`** 和 **`/O2`** 是互斥的。

> [!NOTE]
> **x86 特定**\
> 这些选项意味着使用框架指针省略 ([`/Oy`](oy-frame-pointer-omission.md)) 选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **优化**" 属性页。

1. 修改 "**优化**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。

## <a name="see-also"></a>另请参阅

[`/O` (优化代码的选项) ](o-options-optimize-code.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[`/EH` (异常处理模型) ](eh-exception-handling-model.md)
