---
title: /Ob（内联函数展开）
ms.date: 08/08/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: 7eb3db1e359349eaf5125a6c8a46a3ac7d847f2f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915484"
---
# <a name="ob-inline-function-expansion"></a>/Ob（内联函数展开）

控制函数的内联扩展。 默认情况下, 在进行优化时, 将在编译器对所有函数 (通常称为*自动内联*) 上自行决定扩展。

## <a name="syntax"></a>语法

::: moniker range=">=vs-2019"

> **/Ob**{**0**|12|**3**}|

::: moniker-end

::: moniker range="<=vs-2017"

> **/Ob**{**0**|12|}

::: moniker-end

## <a name="arguments"></a>自变量

**0**\
[/Od](od-disable-debug.md)下的默认值。 禁用内联扩展。

**1**\
仅允许对标记为[inline](../../cpp/inline-functions-cpp.md)、 [__inline](../../cpp/inline-functions-cpp.md)或[__forceinline](../../cpp/inline-functions-cpp.md)的函数或在类声明C++中定义的成员函数进行扩展。

**pps-2**\
[/O1](o1-o2-minimize-size-maximize-speed.md)和[/O2](o1-o2-minimize-size-maximize-speed.md)下的默认值。 允许编译器展开未显式标记为 "无内联" 的任何函数。

::: moniker range=">=vs-2019"

**3**\
此选项指定比 **/Ob2**更严格的内联, 但具有相同的限制。 从 Visual Studio 2019 开始, 可以使用 **/Ob3**选项。

::: moniker-end

## <a name="remarks"></a>备注

编译器将内联扩展选项和关键字视为建议。 不能保证所有函数都将以内联方式展开。 您可以禁用内联扩展, 但是不能强制编译器内联特定函数, 即使使用`__forceinline`关键字时也是如此。

若要将函数作为内联展开的候选项排除, 可以使用[__declspec (noinline)](../../cpp/noinline.md)或标记为[#pragma auto_inline (off)](../../preprocessor/auto-inline.md)和[#pragma auto_inline (on)](../../preprocessor/auto-inline.md)指令的区域。 有关为编译器提供内联提示的另一种方式的信息, 请参阅[#pragma 内部](../../preprocessor/intrinsic.md)指令。

> [!NOTE]
> 通过分析测试运行收集的信息会替代由于你指定了 **/Ob**、 **/os**或 **/ot**而生效的优化。 有关详细信息，请参阅[按配置优化](../profile-guided-optimizations.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > " " > **C/C++** **优化**" 属性页。

1. 修改**内联函数展开**属性。

::: moniker range=">=vs-2019"

**/Ob3**选项在**内联函数展开**属性中不可用。 设置 **/Ob3**:

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > " " > **C/C++**  **命令行**" 属性页。

1. 在**其他选项**中, 输入 **/Ob3** 。

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>。

## <a name="see-also"></a>请参阅

[/O 选项 (优化代码)](o-options-optimize-code.md)\
[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
