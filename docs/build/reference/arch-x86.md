---
title: -arch (x86) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87e1826e324f8e544a791520a3ac035f5ab07100
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374695"
---
# <a name="arch-x86"></a>/arch (x86)
在 x86 上为代码生成指定体系结构。 另请参阅[/arch (x64)](../../build/reference/arch-x64.md)和[/arch (ARM)](../../build/reference/arch-arm.md)。  
  
## <a name="syntax"></a>语法  
  
```  
/arch:[IA32|SSE|SSE2|AVX|AVX2]  
```  
  
## <a name="arguments"></a>自变量  
 **/arch:IA32**  
 指定未增强指令，同时为浮点计算指定 x87。  
  
 **/arch:SSE**  
 启用对 SSE 指令的使用。  
  
 **/arch:SSE2**  
 启用对 SSE2 指令的使用。 这是在 x86 上的默认指令平台如果没有 **/arch**指定选项。  
  
 **/arch: avx**  
 启用对 Intel 高级矢量扩展指令的使用。  
  
 **/arch: avx2**  
 启用对 Intel 高级矢量扩展 2 指令的使用。  
  
## <a name="remarks"></a>备注  
 SSE 和 SSE2 指令在各种 Intel 和 AMD 处理器中均存在。 Intel 浅桥处理器和 AMD Bulldozer 处理器上存在 AVX 说明。 AVX2 指令受 Intel Haswell 和 Broadwell 处理器以及 AMD 基于挖掘机处理器支持。  
  
 `_M_IX86_FP`，`__AVX__`和`__AVX2__`宏指示 (如果有） **/arch**编译器选项已使用。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。 **/Arch: avx2**选项和`__AVX2__`宏在 Visual Studio 2013 Update 2，版本 12.0.34567.1 中引入。  
  
 优化器选择何时以及如何使用 SSE 和 SSE2 指令时 **/arch**指定。 当确定使用 SSE/SSE2 指令和寄存器肯定要比使用 x87 浮点寄存器堆栈更快时，将 SSE 和 SSE2 指令用于某些标量浮点计算。 因此，你的代码实际上将混合使用 x87 和 SSE/SSE2 来进行浮点计算。 此外，通过 **/arch:SSE2**，SSE2 指令用于某些 64 位整数运算。  
  
 除了使用 SSE 和 SSE2 指令之外，编译器还使用在支持 SSE 和 SSE2 的处理器修订版上提供的其他指令。 例如，在 Intel 处理器的 Pentium Pro 修订版中首次出现的 CMOV 指令。  
  
 由于的 x86 编译器生成使用 SSE2 指令的代码默认情况下，您必须指定 **/arch:IA32**禁用 SSE 和 SSE2 指令生成面向 x86 处理器。  
  
 **/arch**仅影响本机函数生成的代码。 当你使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)进行编译时， **/arch**对托管的函数的代码生成没有影响。  
  
 **/arch**和[/QIfist](../../build/reference/qifist-suppress-ftol.md)不能用于同一编译。 具体而言，如果不使用 `_controlfp` 修改 FP 控制字，则运行时启动代码会将 x87 FPU 控制字精度控制字段设置为 53 位。 因此，表达式中的每个浮点型和双运算都使用 53 位有效数和 15 位指数。 但是，每个 SSE 单精度运算都使用 24 位有效数和 8 位指数，而 SSE2 双精度运算使用 53 位有效数和 11 位指数。 有关详细信息，请参阅 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)。 在单个表达式树中可能会出现这些差异，而在每一子表达式后存在用户赋值的情况下则不会。 考虑以下情况：  
  
```cpp  
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.  
```  
  
 进行比较：  
  
```cpp  
t = f1 * f2;   // Do f1 * f2, round to the type of t.  
r = t + d;     // This should produce the same overall result   
               // whether x87 stack is used or SSE/SSE2 is used.  
```  
  
### <a name="to-set-this-compiler-option-for-avx-avx2-ia32-sse-or-sse2-in-visual-studio"></a>在 Visual Studio 中设置 AVX、AVX2、IA32、SSE 或 SSE2 的此编译器选项  
  
1.  打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**配置属性**， **C/c + +** 文件夹。  
  
3.  选择**代码生成**属性页。  
  
4.  修改**启用增强指令集**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。  
  
## <a name="see-also"></a>请参阅  
 [/arch （最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)