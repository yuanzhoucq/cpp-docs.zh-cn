---
title: /fp（指定浮点行为）
ms.date: 11/09/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: c90a35bbaf967ecf50977987865d6a768b019fe3
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150769"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp（指定浮点行为）

指定编译器如何处理浮点表达式、优化和异常。 **/Fp**选项指定生成的代码是否允许浮点环境更改为舍入模式、异常掩码和次正常行为，以及浮点状态检查是否返回当前的准确结果。 它控制编译器是否生成用于维护源操作和表达式排序并符合 NaN 传播标准的代码，或者是否生成更有效的代码，以便对操作进行重新排序或组合操作并进行简化标准不允许的代数转换。

## <a name="syntax"></a>语法

> **/fp：** [**精确** | **严格** | **快速** | **除外**[ **-** ]]

### <a name="arguments"></a>参数

#### <a name="precise"></a>说

默认情况下，编译器使用 `/fp:precise` 行为。

在 `/fp:precise` 下，编译器会在生成并优化目标计算机的对象代码时保留浮点代码的源表达式排序和舍入属性。 在表达式计算过程中，编译器会在四个特定点处舍入到源代码精度：在赋值时，在 typecasts 时，将浮点参数传递到函数调用，以及从函数调用返回浮点值。 中间计算可在计算机精度执行。 Typecasts 可用于显式舍入中间计算。

编译器不会对浮点表达式（如重新关联或分布）执行代数转换，除非保证转换生成按位相同的结果。
涉及特殊值（NaN、+ 无穷、-无限大、-0.0）的表达式根据 IEEE-754 规范进行处理。 例如，如果 x 为 NaN，则 `x != x` 的计算结果为**true** 。 浮点*缩写*（即组合浮点操作的计算机指令）可在 `/fp:precise`下生成。

编译器生成旨在在[默认浮点环境](#the-default-floating-point-environment)中运行的代码，并假定在运行时不访问或修改浮点环境。 也就是说，它假定代码不取消屏蔽浮点异常、读取或写入浮点状态寄存器或更改舍入模式。

如果你的浮点代码不依赖于你的浮点语句中的运算和表达式的顺序（例如，如果你不关心 `a * b + a * c` 是作为 `(b + c) * a` 计算还是 `a + a`中的 `2 * a` 计算），请考虑[/fp： fast](#fast)选项，该选项可以生成更快、更高效的代码。 如果你的代码都依赖于操作和表达式的顺序，并访问或更改了浮点环境（例如，更改舍入模式或捕获浮点异常），请使用[/fp： strict](#strict)。

#### <a name="strict"></a>strict

`/fp:strict` 具有类似于 `/fp:precise`的行为，也就是说，当编译器生成并优化目标计算机的对象代码时，它会保留浮点代码的源顺序和舍入属性，并遵循处理特殊值时的标准。 此外，程序可以在运行时安全访问或修改浮点环境。

在 `/fp:strict`下，编译器将生成代码，使程序可以安全取消屏蔽浮点异常、读取或写入浮点状态寄存器或更改舍入模式。 在表达式计算过程中，它在四个特定点处舍入到源代码精度：在赋值时，在 typecasts 时，将浮点自变量传递给函数调用，以及从函数调用返回浮点值。 中间计算可在计算机精度执行。 Typecasts 可用于显式舍入中间计算。 编译器不会对浮点表达式（如重新关联或分布）执行代数转换，除非保证转换生成按位相同的结果。 涉及特殊值（NaN、+ 无穷、-无限大、-0.0）的表达式根据 IEEE-754 规范进行处理。 例如，如果 x 为 NaN，则 `x != x` 的计算结果为**true** 。 不 `/fp:strict`下生成浮点缩写。

与 `/fp:precise` 相比，`/fp:strict` 的计算成本更高，因为编译器必须插入额外的指令来捕获异常，并允许程序在运行时访问或修改浮点环境。 如果你的代码不使用此功能，但需要源代码排序和舍入，或者依赖于特殊值，请使用 `/fp:precise`。 否则，请考虑使用 `/fp:fast`，这会产生更快且更小的代码。

#### <a name="fast"></a>快速

`/fp:fast` 选项允许编译器重新排序、合并或简化浮点运算，以优化浮点代码的速度和空间。 编译器可能会忽略赋值语句、typecasts 或函数调用的舍入。 即使此类转换导致显著不同的舍入行为，它也可能对操作进行重新排序或执行代数转换（例如，通过使用关联法和分配法）。 由于此增强的优化，某些浮点计算的结果可能不同于其他 `/fp` 选项所产生的结果。 特殊值（NaN、+ 无限大、-无限大、-0.0）可能不会根据 IEEE-754 标准传播或严格地表现。 可以在 `/fp:fast`下生成浮点缩写。 编译器仍受 `/fp:fast`下的基础体系结构的约束，可以通过使用[/arch](arch-minimum-cpu-architecture.md)选项提供其他优化。

在 `/fp:fast`下，编译器将生成用于在默认浮点环境中运行的代码，并假定在运行时不访问或修改浮点环境。 也就是说，它假定代码不取消屏蔽浮点异常、读取或写入浮点状态寄存器或更改舍入模式。

`/fp:fast` 适用于不需要对浮点表达式进行严格的源代码排序和舍入的程序，并且不依赖于用于处理特殊值（如 NaN）的标准规则。 如果你的浮点代码需要保留源代码排序和舍入，或者依赖于特殊值的标准行为，请使用[/fp：精确](#precise)。 如果你的代码访问或修改了浮点环境以更改舍入模式、取消屏蔽浮点异常或检查浮点状态，请使用[/fp： strict](#strict)。

#### <a name="except"></a>except

`/fp:except` 选项将生成代码，以确保在其出现时的确切位置引发任何未屏蔽的浮点异常，并且不会引发额外的浮点异常。 默认情况下，`/fp:strict` 选项启用 `/fp:except`，而 `/fp:precise` 不启用。 `/fp:except` 选项与 `/fp:fast`不兼容。 可以通过 `/fp:except-`显式禁用该选项。

请注意，`/fp:except` 不会自行启用任何浮点异常，但程序必须启用浮点异常。 有关如何启用浮点异常的信息，请参阅[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 。

## <a name="remarks"></a>备注

可以在同一个编译器命令行中指定多个 `/fp` 选项。 一次只能有 `/fp:strict`、`/fp:fast`和 `/fp:precise` 选项之一生效。 如果在命令行上指定了多个选项，则后面的选项优先，编译器将生成警告。 `/fp:strict` 和 `/fp:except` 选项与 `/clr`不兼容。

[/Za](za-ze-disable-language-extensions.md) （ANSI 兼容性）选项与 `/fp`不兼容。

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>使用编译器指令控制浮点行为

编译器提供了三个杂注指令用于重写命令行上指定的浮点行为： [float_control](../../preprocessor/float-control.md)、 [fenv_access](../../preprocessor/fenv-access.md)和[fp_contract](../../preprocessor/fp-contract.md)。 您可以使用这些指令在函数级别控制浮点行为，而不是在函数中。 请注意，这些指令不与 `/fp` 选项直接对应。 下表显示 `/fp` 选项和杂注指令如何相互映射。 有关详细信息，请参阅各个选项和杂注指令的文档。

||float_control(precise)|float_control(except)|fenv_access|fp_contract|
|-|-|-|-|-|
|`/fp:fast`|关闭|关闭|关闭|on|
|`/fp:precise`|on|关闭|关闭|on|
|`/fp:strict`|on|on|on|关闭|

### <a name="the-default-floating-point-environment"></a>默认浮点环境

初始化进程时，将设置*默认的浮点环境*。 此环境将屏蔽所有浮点异常，将舍入模式设置为舍入到最接近的值（`FE_TONEAREST`），保留次正常（denormal）值，对**float**、 **double**和**long 双**精度值使用默认精度有效位数（尾数），并在支持时将无穷大控件设置为默认仿射模式。

### <a name="floating-point-environment-access-and-modification"></a>浮点环境访问和修改

Microsoft Visual C++运行时提供了几个用于访问和修改浮点环境的函数。 其中包括[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)、 [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)和[_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)及其变体。 若要确保代码访问或修改浮点环境时正确的程序行为，必须通过 `/fp:strict` 选项或通过使用 `fenv_access` 杂注来启用 `fenv_access`，才能使这些函数生效。 在未启用 `fenv_access` 的情况下，访问或修改浮点环境可能会导致意外的程序行为：代码可能不服从对浮点环境所请求的更改;浮点状态寄存器可能不会报告预期结果或当前结果;可能会发生意外的浮点异常，或者可能不会发生预期的浮点异常。

当你的代码访问或修改浮点环境时，你必须在将使用未启用 `fenv_access` 的代码的情况下启用 `fenv_access` 的代码组合起来时小心。 在未启用 `fenv_access` 的代码中，编译器假设平台默认浮点环境有效，且不会访问或修改浮点状态。 建议将本地浮点环境保存并还原到默认状态，然后再将控制转移到未启用 `fenv_access` 的函数。 此示例演示如何设置和还原 `float_control` 杂注：

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>浮点舍入模式

在 `/fp:precise` 和 `/fp:fast`，编译器将生成用于在默认浮点环境中运行的代码，并假定在运行时不会访问或修改环境。 也就是说，它假定代码不取消屏蔽浮点异常、读取或写入浮点状态寄存器或更改舍入模式。  但是，某些程序需要改变浮点环境。 例如，此示例通过更改浮点舍入模式，计算浮点乘法的误差边界：

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

由于编译器在 `/fp:fast` 下采用默认浮点环境，因此 `/fp:precise` 可随意忽略对 `_controlfp_s`的调用。 例如，当使用 x86 体系结构的 `/O2` 和 `/fp:precise` 进行编译时，不计算边界，示例程序输出：

```Output
cLower = -inf
cUpper = -inf
```

当用 x86 体系结构的 `/O2` 和 `/fp:strict` 进行编译时，示例程序会输出：

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>浮点特殊值

在 `/fp:precise` 和 `/fp:strict`下，涉及特殊值（NaN，+ 无限大，-无限大，-0.0）的表达式的行为取决于 IEEE-754 规范。 在 `/fp:fast`下，这些特殊值的行为可能与 IEEE-754 不一致。

此示例演示 `/fp:precise`、`/fp:strict` 和 `/fp:fast`下的特殊值的不同行为：

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

当用 `/O2` `/fp:precise` 或 `/O2` `/fp:strict` 对于 x86 体系结构进行编译时，输出与 IEEE-754 规范一致：

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

用 x86 体系结构 `/O2` `/fp:fast` 进行编译时，输出与 IEEE-754 不一致：

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>浮点代数转换

在 `/fp:precise` 和 `/fp:strict`下，编译器不会执行数学转换，除非保证转换生成按位相同的结果。 编译器可以在 `/fp:fast`下执行此类转换。 例如，示例函数中 `a * b + a * c` 的表达式 `algebraic_transformation` 可以编译到 `/fp:fast`下的 `a * (b + c)` 中。 不会在 `/fp:precise` 或 `/fp:strict`下执行此类转换，编译器会生成 `a * b + a * c`。

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>浮点显式强制转换点

在 `/fp:precise` 和 `/fp:strict`下，编译器将在表达式计算过程中的四个特定点处舍入到源代码精度：在赋值时，在 typecasts 时，将浮点参数传递到函数调用，以及从函数调用返回浮点值。 Typecasts 可用于显式舍入中间计算。 在 `/fp:fast`下，编译器不会在这些点生成显式强制转换以保证源代码的精度。 此示例演示了不同 `/fp` 选项下的行为：

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

使用 `/O2` `/fp:precise` 或 `/O2` `/fp:strict`编译时，可以看到在 x64 体系结构的生成代码中，转换和函数返回点上都插入了显式类型转换：

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

在 `/O2` 中 `/fp:fast` 会简化生成的代码，因为所有类型强制转换已被优化掉：

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" > " **C/C++**  > **代码生成**" 属性页。

1. 修改**浮点模型**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
