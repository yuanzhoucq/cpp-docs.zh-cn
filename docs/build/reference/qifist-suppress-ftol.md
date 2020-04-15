---
title: /QIfist（取消 _ftol）
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 5d6e12a1003ea125b0da4bfef580d8096e97553a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336104"
---
# <a name="qifist-suppress-_ftol"></a>/QIfist（取消 _ftol）

已弃用。 当需要从浮点型转换为整型时，取消调用 Helper 函数 `_ftol` 。

## <a name="syntax"></a>语法

```
/QIfist
```

## <a name="remarks"></a>备注

> [!NOTE]
> **/QIfist**仅在针对 x86 的编译器中可用;针对 x64 或 ARM 的编译器中不提供此编译器选项。

除了从浮点类型转换为积分类型外，`_ftol`该函数还通过设置控制字位 10 和 11 来确保浮点单元 （FPU） 的舍入模式朝零（截断） 方向发展。 这保证了从浮点类型转换为积分类型发生，如 ANSI C 标准所述（放弃数字的小数部分）。 使用 **/QIfist 时**，此保证不再适用。 舍入模式将是英特尔参考手册中记录的四种模式之一：

- 向最近旋转（偶数，如果等距）

- 向负无穷大圆

- 向正无穷大圆

- 向零旋转

您可以使用[_control87、_controlfp、_control87_2 \_](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C 运行时函数来修改 FPU 的舍入行为。 FPU 的默认舍入模式为"向最近旋转"。 使用 **/QIfist**可以提高应用程序的性能，但不能没有风险。 在依赖生产环境中使用 **/QIfist**构建的代码之前，应彻底测试代码对舍入模式敏感的部分。

[/arch （x86）](arch-x86.md)和 **/QIfist**不能用于同一编译和。

> [!NOTE]
> **/QIfist**在默认情况下无效，因为舍入位也会影响浮点到浮点舍入（每次计算后发生），因此，当您为 C 样式（向零）舍入设置标志时，浮动点计算可能会有所不同。 如果代码依赖于截断浮点数的分几部分的预期行为，则不应使用 **/QIfist。** 如果您不确定，请勿使用 **/QIfist**。

**/QIfist**选项从 Visual Studio 2005 开始被弃用。 编译器在浮点到 int 转换速度方面进行了显著改进。 有关弃用编译器选项的列表，请参阅[按类别列出的编译器选项](compiler-options-listed-by-category.md)中的**弃用和删除编译器选项**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行” **** 属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[/Q 选项（低级别操作）](q-options-low-level-operations.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
