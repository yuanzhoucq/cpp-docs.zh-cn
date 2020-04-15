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
ms.openlocfilehash: 0eda9461b3ef730e0e0a832aa94a688e03c7e1bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336177"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os、/Ot（代码大小优先、代码速度优先）

最小化或最大化 EXEs 和 DLL 的大小。

## <a name="syntax"></a>语法

```
/Os
/Ot
```

## <a name="remarks"></a>备注

**/O（** 有利于小代码）通过指示编译器选择大小而不是速度来最小化 EXEs 和 DLL 的大小。 编译器可以减少许多 C 和 C++构造，以在功能上相似的计算机代码序列。 有时，这些差异会提供大小与速度的权衡。 **/O**和 **/Ot**选项允许您指定一个首选项而不是另一个首选项：

**/Ot（** 希望快速代码）通过指示编译器选择速度而不是大小来最大化 EXEs 和 DLL 的速度。 （这是默认值。编译器可以减少许多 C 和 C++构造，以在功能上相似的计算机代码序列。 有时，这些差异会提供大小与速度的权衡。 **/Ot**选项由"最大化速度 （[/O2](o1-o2-minimize-size-maximize-speed.md)） " 选项隐含。 **/O2**选项结合了多个选项，可生成非常快的代码。

如果使用 **/O**或 **/Ot**，则还必须指定[/Og](og-global-optimizations.md)以优化代码。

> [!NOTE]
> 从分析测试运行中收集的信息将覆盖如果指定 **/Ob、/O**或 **/Ot**时 **/Os**生效的优化。 有关详细信息，[配置文件引导优化](../profile-guided-optimizations.md)。

**x86 专用**

以下示例代码演示了"首选小代码 （**/O**） 选项和"首选快速代码 （**/Ot**） "选项之间的区别：

> [!NOTE]
> 下面描述了使用 **/O**或 **/Ot**时的预期行为。 但是，从发布到发布的编译器行为可能会导致对以下代码进行不同的优化。

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

如下图所示，当为大小 **（/O）** 编译为*S.c 时，编译器在 return 语句中显式实现乘法表达式，以生成短但较慢的代码序列：

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

或者，当为速度 **（/Ot）** 编译 DIFFER.c 时，编译器将返回语句中的乘法表达式实现为一系列移`LEA`位和指令，以生成快速但较长的代码序列：

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**结束 x86 特定**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击 **"优化**属性"页。

1. 修改 **"优惠大小"或"速度"** 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>。

## <a name="see-also"></a>另请参阅

[/O 选项（优化代码）](o-options-optimize-code.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
