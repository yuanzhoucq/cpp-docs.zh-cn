---
title: /fp （指定浮点行为）
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
ms.openlocfilehash: 77e6d0c97f1d0381fe32ae23f8d7e8bd02ddf219
ms.sourcegitcommit: 22f7c4a9b4fc2158fb5283810f15275803cafe10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2019
ms.locfileid: "54417637"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp （指定浮点行为）

指定编译器如何处理浮点表达式、 优化和异常。 **/Fp**选项用于指定是否在生成的代码允许浮点环境更改为舍入模式、 异常掩码和次正常行为和浮点状态检查返回当前、 准确地结果。 它控制编译器是否生成代码的维护源代码操作和表达式排序并符合标准的 NaN 传播，或如果它将改为生成更高效的代码，可能会重新排序或合并操作并使用简化不允许使用的标准的代数转换。

## <a name="syntax"></a>语法

> **/fp:**[**precise** | **strict** | **fast** | **except**[**-**]]

### <a name="arguments"></a>自变量

#### <a name="precise"></a>精确

默认情况下，编译器将使用 **/fp： 精确**行为。

下 **/fp： 精确**编译器保留排序结果和舍入浮点代码的属性时它将生成并优化了目标计算机的对象代码的源表达式。 编译器在表达式计算期间舍入到四个特定点上的源代码精度： 在分配，在类型强制转换、 函数调用返回浮点型参数传递给函数调用，以及时的浮点值。 中间计算可能会在计算机精度执行。 类型强制转换可用于显式舍入中间计算。

编译器不会对浮点表达式，如重新关联或分发，不执行代数转换，除非该转换可保证生成的按位完全相同的结果。
根据 IEEE 754 规范处理所涉及特殊值 （NaN、 + infinity、-infinity、-0.0） 的表达式。 例如，`x != x`计算结果为**true**如果 x 为 NaN。 浮点*缩写*，，可在生成合并浮点运算的机器指令，即 **/fp： 精确**。

编译器将生成用于在运行的代码[默认的浮点环境](#the-default-floating-point-environment)，并假定未访问或修改在运行时浮点环境。 也就是说，它假定，该代码不取消屏蔽浮点异常、 读取或写入浮点状态注册或更改舍入模式。

如果你的浮点代码不依赖顺序运算和浮点语句中的表达式 (例如，如果您不关心是否`a * b + a * c`计算方式为`(b + c) * a`或`2 * a`作为`a + a`)，请考虑[/fp: fast](#fast)选项，可以生成更快、 更高效的代码。 如果你的代码同时取决于运算和表达式，并访问或更改 （例如，若要更改舍入模式，或若要捕获的浮点异常） 的浮点环境，使用[/fp: strict](#strict)。

#### <a name="strict"></a>strict

**/fp: strict**具有类似的行为 **/fp： 精确**，即编译器保留源顺序以及舍入的浮点代码时它将生成并优化了的属性对象为目标计算机的代码并在处理特殊值时遵循标准。 此外，该程序可以安全地访问或修改在运行时的浮点环境。

下 **/fp: strict**，编译器将生成使程序能够安全地取消屏蔽浮点异常、 读取或写入浮点状态注册或更改舍入模式的代码。 它将舍入到四个特定点上的源代码精度在表达式计算过程： 在分配，在类型强制转换、 函数调用返回浮点型参数传递给函数调用，以及时的浮点值。 中间计算可能会在计算机精度执行。 类型强制转换可用于显式舍入中间计算。 编译器不会对浮点表达式，如重新关联或分发，不执行代数转换，除非该转换可保证生成的按位完全相同的结果。 根据 IEEE 754 规范处理所涉及特殊值 （NaN、 + infinity、-infinity、-0.0） 的表达式。 例如，`x != x`计算结果为**true**如果 x 为 NaN。 在下，不会生成浮点缩写 **/fp: strict**。

**/fp: strict**比计算更昂贵 **/fp： 精确**因为编译器必须插入以捕获异常并允许访问或修改在浮点环境在程序的其他说明运行时。 如果你的代码不使用此功能，但需要源代码排序和舍入，或依赖于特殊值，使用 **/fp： 精确**。 否则，请考虑使用 **/fp: fast**，这可以生成更快、 更小的代码。

#### <a name="fast"></a>快速

**/Fp: fast**选项使编译器能够重新排序、 合并或简化浮点运算，以优化浮点代码的速度和空间。 编译器可能会忽略在赋值语句舍入、 类型强制转换或函数调用。 它可能会对操作重新排序或执行代数转换，例如，使用关联和分布式法律，即使此类转换导致显著不同的舍入行为。 由于此增强优化某些浮点计算的结果可能不同于由其他生成的那些 **/fp**选项。 特殊值 （NaN、 + infinity、-infinity、-0.0） 不会传播，或根据 IEEE 754 标准严格行为。 在下，可生成浮点缩写 **/fp: fast**。 编译器仍受下的基础体系结构 **/fp: fast**，以及额外的优化可通过使用[/arch](../../build/reference/arch-minimum-cpu-architecture.md)选项。

下 **/fp: fast**，编译器将生成用于在默认的浮点环境中运行的代码，并假定浮点环境不是访问或修改在运行时。 也就是说，它假定，该代码不取消屏蔽浮点异常、 读取或写入浮点状态注册或更改舍入模式。

**/fp: fast**适用于不需要严格源代码排序和浮点表达式的舍入，并且不要依赖于标准规则来处理特殊值，例如 NaN 的程序。 如果你的浮点代码要求保留源代码排序和舍入，或者依赖于特殊值，使用的标准行为[/fp： 精确](#precise)。 如果你的代码访问或修改要更改的舍入模式的浮点环境，取消屏蔽浮点异常，或检查浮点状态，请使用[/fp: strict](#strict)。

#### <a name="except"></a>except

**/Fp： 除**选项生成代码，以确保在开始他们进行，具体时间会发出任何取消屏蔽浮点异常，并引发任何其他的浮点异常。 默认情况下 **/fp: strict**选项使 **/fp： 除**，和 **/fp： 精确**却没有。 **/Fp： 除外**选项不兼容 **/fp: fast**。 可以通过我们的显式禁用选项 **/fp： 除-**。

请注意， **/fp： 除**不会启用任何浮点异常本身，但这是必需的程序以启用浮点异常。 请参阅[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)有关如何启用浮点异常的信息。

## <a name="remarks"></a>备注

多个 **/fp**在相同的编译器命令行中指定选项。 只有一个 **/fp: strict**， **/fp: fast**，并 **/fp： 精确**选项可以实际上是一次。 如果命令行上指定多个以下选项之一，则优先采用更高版本的选项和编译器生成警告。 **/Fp: strict**并 **/fp： 除**选项都不符合 **/clr**。

[/Za](../../build/reference/za-ze-disable-language-extensions.md) （ANSI 兼容性） 选项不兼容 **/fp**。

### <a name="using-pragmas-to-control-floating-point-behavior"></a>使用杂注控制浮点行为

编译器提供了三个杂注指令来重写命令行上指定的浮点行为： [float_control](../../preprocessor/float-control.md)， [fenv_access](../../preprocessor/fenv-access.md)，和[fp_contract](../../preprocessor/fp-contract.md). 这些杂注可用于控制在函数级别，不在函数的浮点行为。 请注意这些杂注不直接对应 **/fp**选项。 下表显示了如何 **/fp**选项和杂注将映射到对方。 有关详细信息，请参阅文档以了解各个选项和杂注。

||float_control(precise)|float_control(except)|fenv_access|fp_contract|
|-|-|-|-|-|
|**/fp:fast**|关闭|关闭|关闭|on|
|**/fp:precise**|on|关闭|关闭|on|
|**/fp:except**|on|on|on|关闭|

### <a name="the-default-floating-point-environment"></a>默认的浮动点环境

初始化一个过程时，*浮动点环境的默认*设置。 此环境会屏蔽所有浮点异常，设置的舍入模式舍入到最接近 (`FE_TONEAREST`)，将保留次正常 （非常规） 用于有效位数 （尾数） 的默认精度，值**float**， **双**，并**长双精度型**值，并在支持的情况，将无穷控制设置为默认仿射模式。

### <a name="floating-point-environment-access-and-modification"></a>浮点环境访问和修改

Microsoft Visual c + + 运行时提供多个函数来访问和修改的浮点环境。 其中包括[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)， [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)，并[_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)及其变量。 若要确保正确的程序行为时，你的代码访问或修改的浮点环境，`fenv_access`必须启用，或者通过 **/fp: strict**选项，或通过使用的`fenv_access`杂注，这些函数有任何效果。 当`fenv_access`是未启用，请访问或修改的浮点环境可能会导致意外的程序行为： 代码可能不接受请求对浮点环境进行更改; 可能不会报告浮点状态注册预期或当前结果;和意外的浮点异常可能会或可能不是预期的浮点异常。

时你的代码访问或修改的浮点环境，您必须小心结合使用代码时，`fenv_access`启用了代码并没有`fenv_access`启用。 在代码中其中`fenv_access`未启用，则编译器将假定平台默认浮点环境正在起作用，和浮点状态不是访问或修改。 我们建议您保存和之前控制转移到其中一个函数，但没有为其默认状态还原本地浮点环境`fenv_access`启用。 此示例演示如何将`float_control`杂注可进行设置，还原：

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>浮点舍入模式

下都 **/fp： 精确**并 **/fp: fast**编译器生成用于在默认的浮点环境中运行的代码，并假定该环境不是访问或修改在运行时。 也就是说，它假定，该代码不取消屏蔽浮点异常、 读取或写入浮点状态注册或更改舍入模式。  但是，某些程序需要更改的浮点环境。 例如，此示例计算误差范围的浮点乘法通过更改浮点舍入模式：

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

因为编译器会假定浮动点环境下的默认 **/fp: fast**并 **/fp： 精确**免费忽略对调用`_controlfp_s`。 例如，当编译的同时使用这二者 **/o2**和 **/fp： 精确**x86 体系结构，不计算边界，以及示例程序输出：

```Output
cLower = -inf
cUpper = -inf
```

编译时使用这两 **/o2**并 **/fp: strict** x86 体系结构中，示例程序输出：

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>特殊的浮点值

下 **/fp： 精确**并 **/fp: strict**，所涉及特殊值 （NaN、 + infinity、-infinity、-0.0） 的表达式的行为根据 IEEE 754 规范。 下 **/fp: fast**，这些特殊值的行为可能与 IEEE 754 不一致。

此示例演示在特殊值的不同行为 **/fp： 精确**， **/fp: strict**并 **/fp: fast**:

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

编译时使用 **/o2** **/fp： 精确**或 **/o2** **/fp: strict**针对 x86 体系结构，输出是符合 IEEE-754规范：

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

编译时使用 **/o2** **/fp: fast**针对 x86 体系结构，输出不是符合 IEEE-754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>浮点带来了代数转换

下 **/fp： 精确**并 **/fp: strict**，除非可以保证转换生成的按位相同结果，编译器不会执行数学转换。 编译器可能会执行此类转换下的 **/fp: fast**。 例如，表达式`a * b + a * c`中的示例函数`algebraic_transformation`可能会编译到`a * (b + c)`下 **/fp: fast**。 下不执行此类转换 **/fp： 精确**或 **/fp: strict**，并且编译器会生成`a * b + a * c`。

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>浮点的显式强制转换点

下 **/fp： 精确**并 **/fp: strict**，编译器在表达式计算期间舍入到四个特定点上的源代码精度： 在分配，在类型强制转换时浮点型参数被传递到函数调用和函数调用返回浮点值。 类型强制转换可用于显式舍入中间计算。 下 **/fp: fast**，编译器不会生成在这些位置以保证源代码精度的显式强制转换。 此示例演示如何在不同的行为 **/fp**选项：

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

通过使用在编译时 **/o2** **/fp： 精确**或 **/o2** **/fp: strict**，可以看到，在这两个插入显式类型强制转换类型转换，并在该函数返回点针对 x64 生成的代码中体系结构：

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

下 **/o2** **/fp: fast**简化生成的代码，因为所有类型强制转换都优化掉：

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **代码生成**属性页。

1. 修改**浮点模型**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](compiler-options.md)<br/>
[设置编译器选项](setting-compiler-options.md)<br/>
[Microsoft Visual c + + 浮点优化](floating-point-optimization.md)<br/>
