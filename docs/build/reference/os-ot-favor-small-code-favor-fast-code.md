---
title: /Os、/Ot（代码大小优先、代码速度优先）
ms.date: 11/04/2016
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
ms.openlocfilehash: c2abf23c15e6550a6d115f2e2b41a9c59de5fa3a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424634"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os、/Ot（代码大小优先、代码速度优先）

最小化或最大化 Exe 和 Dll 的大小。

## <a name="syntax"></a>语法

```
/Os
/Ot
```

## <a name="remarks"></a>备注

**/Os** （倾向于代码） 通过指示编译器大小优先于速度降至最低 Exe 和 Dll 的大小。 为机器代码的功能上类似序列，编译器可以减少许多 C 和 c + + 构造。 这些差异有时提供大小和速度的折衷。 **/Os**并 **/Ot**选项，可以指定一个首选项：

**/Ot** （优选代码速度） 指示编译器优选速度而非大小，从而最大化 Exe 和 Dll 的速度。 （这是默认值）。为机器代码的功能上类似序列，编译器可以减少许多 C 和 c + + 构造。 有时，这些差异提供大小和速度的折衷。 /Ot 选项隐含的最大化速度 ([/o2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)) 选项。 **/O2**选项组合多个选项以生成速度非常快的代码。

如果您使用 **/Os**或 **/Ot**，则还必须指定[/Og](../../build/reference/og-global-optimizations.md)以优化的代码。

> [!NOTE]
>  通过分析测试运行收集的信息将覆盖本应有效如果指定的优化 **/Ob**， **/Os**，或 **/Ot**。 有关详细信息[按配置文件优化](../../build/reference/profile-guided-optimizations.md)。

**x86 Specific**

下面的代码示例演示了代码大小优先之间的差异 (**/Os**) 选项和代码速度优先 (**/Ot**) 选项：

> [!NOTE]
>  以下介绍时使用的预期的行为 **/Os**或 **/Ot**。 但是，编译器行为发行版本可能会导致下面的代码的不同优化。

```
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

计算机下面的代码片段中所示，当编译 DIFFER.c 大小 (**/Os**)，该编译器实现乘法表达式将返回语句中的显式为乘法，以生成代码的短但速度较慢的序列：

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

或者，DIFFER.c 编译速度 (**/Ot**)，编译器实现乘作为一系列 shift 在 return 语句中的表达式和`LEA`生成代码的速度，但较长序列的说明：

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**结束 x86 特定**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**优化**属性页。

1. 修改**优选大小或速度**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>。

## <a name="see-also"></a>请参阅

[/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
