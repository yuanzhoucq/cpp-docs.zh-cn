---
title: /arch (x86)
ms.date: 10/01/2019
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: b1e5501f6edd3eb016395380ff476250c0c388b9
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816314"
---
# <a name="arch-x86"></a>/arch (x86)

在 x86 上为代码生成指定体系结构。 另请参阅[/arch （x64）](arch-x64.md)和[/arch （ARM）](arch-arm.md)。

## <a name="syntax"></a>语法

```
/arch:[IA32|SSE|SSE2|AVX|AVX2|AVX512]
```

## <a name="arguments"></a>参数

**/arch:IA32**<br/>
指定未增强指令，同时为浮点计算指定 x87。

**/arch:SSE**<br/>
启用对 SSE 指令的使用。

**/arch:SSE2**<br/>
启用对 SSE2 指令的使用。 如果未指定 **/arch**选项，则这是 x86 平台上的默认说明。

**/arch:AVX**<br/>
启用对 Intel 高级矢量扩展指令的使用。

**/arch:AVX2**<br/>
启用对 Intel 高级矢量扩展 2 指令的使用。

**/arch： AVX512**<br/>
启用 Intel 高级矢量扩展512说明的使用。

## <a name="remarks"></a>备注

**/Arch**选项启用或禁用特定指令集扩展的使用，特别是对于矢量计算，适用于 INTEL 和 AMD 的处理器。 通常，在使用指令集扩展执行代码之前，更高版本的处理器可能支持更高版本的处理器，更高版本的处理器可能支持更高版本的处理器[__cpuid](../../intrinsics/cpuid-cpuidex.md) 。

**/arch**仅影响本机函数的代码生成。 使用[/clr](clr-common-language-runtime-compilation.md)进行编译时， **/arch**不会影响托管函数的代码生成。

**/Arch**选项引用具有以下特征的指令集扩展：

- **IA32**是旧式32位 x86 指令集，无需任何矢量操作，并使用 x87 进行浮点计算。

- **SSE**允许用多达四个单精度浮点值的矢量进行计算。 还添加了相应的标量浮点指令。

- **SSE2**允许对单精度、双精度、1、2、4或8字节整数值的128位向量进行计算。 还添加了双精度标量指令。

- **AVX**引入了一个适用于矢量和浮点标量指令的替代说明编码，这些指令允许使用128位或256位的矢量，并使所有矢量结果都为完全矢量大小。 （为实现旧兼容性，SSE 样式矢量指令保留比特127更高的所有位。）大多数浮点运算扩展到256位。

- **AVX2**将大多数整数运算扩展到256位向量，并支持使用已扩充的乘法-加法（FMA）指令。

- **AVX512**引入了另一个允许512位向量以及某些其他可选功能的指令编码形式。 还添加了其他操作的说明。

优化器根据指定的 **/arch** ，选择何时以及如何使用向量指令。 标量浮点计算是使用 SSE 或 AVX 指令执行的（如果可用）。 某些调用约定指定在 x87 堆栈上传递浮点参数，因此，您的代码可能混合使用 x87 和 SSE/AVX 指令作为浮点计算。 整数向量指令还可用于某些64位整数操作（如果有）。

除了矢量和浮点标量指令以外，每个 **/arch**选项还可以允许使用与该选项关联的其他非矢量指令。 例如，CMOVcc 指令系列首次出现在 Intel 奔腾 Pro 处理器上。 由于后面的 Intel Pentium III 处理器引入了 SSE 说明，因此，在指定 **/arch： IA32**时，可能会生成 CMOVcc 指令。

浮点运算通常在 x87 代码中舍入为双精度（64位），但你可以使用 `_controlfp` 修改 FP 控制字，包括将精度控件设置为扩展精度（80位）或单精度（32位）。 有关详细信息，请参阅 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)。 SSE 和 AVX 对于每个操作都有单独的单精度和双精度指令，因此对于 SSE/AVX 代码没有等效项。 在进一步计算中直接使用浮点运算的结果，而不是将其分配给用户变量时，这会改变结果的舍入方式。 请考虑以下事项：

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

具有显式赋值：

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

**/arch**和[/QIfist](qifist-suppress-ftol.md)不能用于同一编译单位。 **/QIfist**选项更改浮点到整数转换的舍入行为。 默认行为是截断（向零舍入），而 **/QIfist**选项指定使用浮点环境舍入模式。 因为这将更改所有浮点到整数转换的行为，所以此标志已弃用。 为 SSE 或 AVX 进行编译时，可以使用浮点环境舍入模式通过内部函数序列将浮点值舍入到整数：

```cpp
int convert_float_to_int(float x) {
    return _mm_cvtss_si32(_mm_set_ss(x));
}

int convert_double_to_int(double x) {
    return _mm_cvtsd_si32(_mm_set_sd(x));
}
```

`_M_IX86_FP`、`__AVX__`、`__AVX2__`、`__AVX512F__`、`__AVX512CD__`、`__AVX512BW__`、`__AVX512DQ__` 和 `__AVX512VL__` 宏指示使用了哪个 **/arch**编译器选项。 有关详细信息，请参阅 [Predefined Macros](../../preprocessor/predefined-macros.md)。 在版本 12.0.34567.1) Visual Studio 2013 Update 2 中引入了 **/arch： AVX2**选项和 `__AVX2__` 宏。 对/arch 的有限支持 **： AVX512**已添加到 visual studio 2017，并在 visual studio 2019 中扩展。

### <a name="to-set-this-compiler-option-for-avx-avx2-avx512-ia32-sse-or-sse2-in-visual-studio"></a>在 Visual Studio 中为 AVX、AVX2、AVX512、IA32、SSE 或 SSE2 设置此编译器选项

1. 打开项目的 "**属性页**" 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**"、" **C/C++** 文件夹"。

1. 选择 "**代码生成**" 属性页。

1. 修改 "**启用增强指令集**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。

## <a name="see-also"></a>另请参阅

[/arch（最小 CPU 体系结构）](arch-minimum-cpu-architecture.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
