---
title: /Os、/Ot（代码大小优先、代码速度优先）
description: MSVC 编译器选项/Os 和/Ot 指定优化代码时是否优选大小或速度。
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
ms.openlocfilehash: 384019ddf7b80b8dd4e00197d73d1e4ac536634c
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180820"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>`/Os`， `/Ot` (优选小代码，代码速度优先) 

最小化或最大化 Exe 和 Dll 的大小。

## <a name="syntax"></a>语法

> **`/Os`**\
> **`/Ot`**

## <a name="remarks"></a>备注

**`/Os`** (优选小代码) 通过指示编译器优选大小以提高 Exe 和 Dll 的大小来最大程度地减小其大小。 编译器可以将许多 C 和 c + + 构造减少到功能类似的计算机代码序列中。 偶尔，这些差异会提供大小和速度的折衷。 **`/Os`** 和 **`/Ot`** 选项允许你为一个选项指定一个首选项：

**`/Ot`** (优选速度快的代码) 通过指示编译器优选速度来最大程度地提高 Exe 和 Dll 的速度。 **`/Ot`** 启用优化时，为默认值。 编译器可以将许多 C 和 c + + 构造减少到功能类似的计算机代码序列中。 有时，这些差异会提供大小和速度的折衷。 **`/Ot`** [`/O2`](o1-o2-minimize-size-maximize-speed.md) ("最大化速度") 选项隐含该选项。 **`/O2`** 选项组合了多个选项以生成更快的代码。

> [!NOTE]
> 如果指定、或，则从分析测试运行中收集的信息将覆盖在其他情况下有效的任何优化 **`/Ob`** **`/Os`** **`/Ot`** 。 有关详细信息，请参阅[按配置优化](../profile-guided-optimizations.md)。

### <a name="x86-specific-example"></a>x86 特定示例

下面的示例代码演示 **`/Os`** (优选小代码) 选项与 **`/Ot`** (优选快速代码) 选项之间的差异：

> [!NOTE]
> 此示例介绍使用或时的预期 **`/Os`** 行为 **`/Ot`** 。 但是，从发布到发布的编译器行为可能会导致以下代码的不同优化。

```c
/* differ.c
  This program implements a multiplication operator
  Compile with /Os to implement multiply explicitly as multiply.
  Compile with /Ot to implement as a series of shift and LEA instructions.
*/
int differ(int x)
{
    return x * 71;
}
```

如下面的计算机代码片段中所示，当 *`differ.c`* 编译为大小 (**`/Os`**) 时，编译器会将 return 语句中的乘法表达式显式实现为相乘，以生成较短但速度较慢的代码序列：

```asm
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

另外，当 *`differ.c`* 编译为速度 (**`/Ot`**) 时，编译器会将返回语句中的乘法表达式作为一系列移位和指令实现， `LEA` 以生成快速但更长的代码序列：

```asm
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **优化**" 属性页。

1. 修改**优选大小或速度**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>。

## <a name="see-also"></a>另请参阅

[/O 选项（优化代码）](o-options-optimize-code.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
