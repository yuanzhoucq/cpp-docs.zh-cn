---
title: /arch (x64)
ms.date: 10/01/2019
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: 0ade6d9f744339ebaf38981d81334340b56080cb
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816228"
---
# <a name="arch-x64"></a>/arch (x64)

在 x64 上为代码生成指定体系结构。 另请参阅[/arch （x86）](arch-x86.md)和[/arch （ARM）](arch-arm.md)。

## <a name="syntax"></a>语法

```
/arch:[AVX|AVX2|AVX512]
```

## <a name="arguments"></a>参数

**/arch:AVX**<br/>
启用对 Intel 高级矢量扩展指令的使用。

**/arch:AVX2**<br/>
启用对 Intel 高级矢量扩展 2 指令的使用。

**/arch： AVX512**<br/>
启用 Intel 高级矢量扩展512说明的使用。

## <a name="remarks"></a>备注

**/Arch**选项允许使用某些指令集扩展，特别是对于矢量计算，适用于 INTEL 和 AMD 的处理器。 通常，在使用指令集扩展执行代码之前，更高版本的处理器可能支持更高版本的处理器，更高版本的处理器可能支持更高版本的处理器[__cpuid](../../intrinsics/cpuid-cpuidex.md) 。

**/arch**仅影响本机函数的代码生成。 使用[/clr](clr-common-language-runtime-compilation.md)进行编译时， **/arch**不会影响托管函数的代码生成。

处理器扩展具有以下特征：

- 默认模式使用 SSE2 指令进行标量浮点和向量计算。 这些说明允许用128位向量（单精度、双精度、1、2、4或8字节整数值）以及单精度和双精度标量浮点值进行计算。

- **AVX**引入了一个适用于矢量和浮点标量指令的替代说明编码，这些指令允许使用128位或256位的矢量，并使所有矢量结果都为完全矢量大小。 （为实现旧兼容性，SSE 样式矢量指令保留比特127更高的所有位。）大多数浮点运算扩展到256位。

- **AVX2**将大多数整数运算扩展到256位向量，并允许使用已扩充的乘法-加法（FMA）指令。

- **AVX-512**引入了另一个允许512位矢量和某些其他可选功能的指令编码形式。 还添加了其他操作的说明。

每个 **/arch**选项还可以启用与该选项关联的其他非矢量指令的使用。 例如，在指定 **/arch： AVX2**时使用某些 BMI 指令。

当指定 **/arch： AVX**， **/arch： AVX2**或 **/arch： AVX512**编译器选项时，将定义 `__AVX__` 预处理器符号。 指定 **/arch： AVX2**或 **/arch： AVX512**编译器选项时，将定义 `__AVX2__` 预处理器符号。 指定 **/arch： AVX512**编译器选项时，将定义 `__AVX512F__`、`__AVX512CD__`、`__AVX512BW__`、`__AVX512DQ__` 和 `__AVX512VL__` 预处理器符号。 有关详细信息，请参阅 [Predefined Macros](../../preprocessor/predefined-macros.md)。 版本 12.0.34567.1) Visual Studio 2013 中引入了 **/arch： AVX2**选项。 对/arch 的有限支持 **： AVX512**已添加到 visual studio 2017，并在 visual studio 2019 中扩展。

### <a name="to-set-the-archavx-archavx2-or-archavx512-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置/arch： AVX，/arch： AVX2 或/arch： AVX512 编译器选项

1. 打开项目的 "**属性页**" 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**"、" **C/C++** 文件夹"。

1. 选择 "**代码生成**" 属性页。

1. 在 "**启用增强指令集**" 下拉框中，选择 "**高级矢量扩展" （/arch： AVX）** 、**高级矢量扩展2（/Arch： AVX2）** 或**高级矢量扩展512（/arch： AVX512）** 。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。

## <a name="see-also"></a>另请参阅

[/arch（最小 CPU 体系结构）](arch-minimum-cpu-architecture.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
