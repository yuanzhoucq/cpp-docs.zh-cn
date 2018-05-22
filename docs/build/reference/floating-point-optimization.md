---
title: Microsoft Visual c + + 浮点优化 |Microsoft 文档
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35c9263fa6252469124eefb0dfd575ef5bd2ac34
ms.sourcegitcommit: 5e932a0e110e80bc241e5f69e3a1a7504bfab1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2018
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Microsoft Visual c + + 浮点优化

获取有关优化浮点代码使用的管理的浮点语义的 Microsoft c + + 编译器的方法的句柄。 确保对浮点代码执行了唯一安全的优化时创建快速的程序。

## <a name="optimization-of-floating-point-code-in-c"></a>C + + 中的浮点代码优化

优化的 c + + 编译器不只将源代码转换为机器代码，它排列并提高效率和/或减小大小的方式计算机指令。 遗憾的是，许多常用优化方法是不一定安全时应用于浮点计算。 一个很好的示例可以检测到具有以下总和算法，取自 David 翰伟，"什么每个计算机科研人员应知道有关浮点算术"，*计算调查*、 年 3 月 1991，pg。 203:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

此函数添加 n **float**数组向量中的值`A`。 在循环主体中，算法将计算随后会应用于总和的下一步"更正"值。 此方法大大降低了简单的总和，同时保留 o （n） 时间复杂性相比累积舍入误差。

Naïve c + + 编译器可能会假定浮点运算，实数算术相同的代数规则如下所示。 此类编译器可能然后错误地认为

> C = T 和-Y = = > （sum + Y） 的总和-Y = = > 0;

即，C 感知的值始终是常数零。 如果此常数值然后传播到后续的表达式，循环体都会减少到简单的总和。 要精确，

> Y = [i]-C = = > Y = [i]<br/>T = 总和 + Y = = > T = 总和 + [i]<br/>sum = T = = > 总和 = 总和 + [i]

因此，对 naïve 编译器的逻辑转换`KahanSum`函数将是：

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

转换后的算法速度更快，尽管*很根本不准确地反映程序员的意图*。 精心设计的错误更正已完全，删除并我们左图简单、 直接总和算法，包含所有相关联的错误。

当然，复杂的 c + + 编译器将知道的代数规则的实际算术并通常不适用于浮点运算。 但是，即使复杂的 c + + 编译器可能仍不正确地解释程序员的意图。

请考虑优化常见尝试保存在寄存器中的任意多个值，尽可能 （称为"注册"值）。 在`KahanSum`示例中，此优化可能会尝试注册局部变量变量`C`，`Y`和`T`因为它们仅在循环体中使用。 如果注册精度 52bits (double) 而不是 23bits （单个），这种优化有效地类型提升`C`，`Y`和`T`类型**double**。 如果 sum 变量不是同样能，则它将保持以单精度编码。 此转换的语义`KahanSum`到以下

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

尽管`Y`，`T`和`C`此新的编码可能会产生不太准确的结果，具体情况中的值取决于在较高的精度，现在计算`A[]`。 因此即使看似无害的优化可能带来不利后果。

这些种类的优化问题不限于"棘手"浮点代码。 当错误地优化，即使简单浮点算法可能会失败。 请考虑简单、 直接总和算法：

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

由于一些浮点单元是能够同时执行多个操作，可以选择编译器面向标量降低优化。 此优化有效地将上面的简单的 Sum 函数转换成以下：

```cpp
float Sum( const float A[], int n )
{
   int n4 = n-n%4; // or n4=n4&(~3)
   int i;
   float sum=0, sum1=0, sum2=0, sum3=0;
   for (i=0; i<n4; i+=4)
   {
      sum = sum + A[i];
      sum1 = sum1 + A[i+1];
      sum2 = sum2 + A[i+2];
      sum3 = sum3 + A[i+3];
   }
   sum = sum + sum1 + sum2 + sum3;
   for (; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

该函数现在维护四个单独的求和，可以在每个步骤同时处理。 尽管优化的函数现在是要快得多，但可以从非优化结果却大不相同优化的结果。 在进行此更改，则编译器假定关联浮点加法;也就是说，这些两个表达式是等效： `(a + b) + c == a + (b + c)`。 但是，关联性并不总是适用浮点数。 而不是计算为的总和：

```cpp
sum = A[0]+A[1]+A[2]+...+A[n-1];
```

转换后的函数现在计算的结果

```cpp
sum = (A[0]+A[4]+A[8]+...)
    + (A[1]+A[5]+A[9]+...)
    + (A[2]+A[6]+A[10]+...)
    + (A[3]+A[7]+A[11]+...);
```

对于某些值的`A[]`，添加操作此不同排序可能产生意外的结果。 若要使问题进一步复杂化，某些程序员可能选择预计这种优化，并相应地补偿它们。 在这种情况下，程序可以构造数组`A`按不同的顺序，以便优化的总和产生预期的结果。 此外，在许多情况的优化结果的准确性可能会"近到足以"。 这在优化中提供了引人注目的速度好处时尤其如此。 视频游戏，例如，需要尽可能得多的速度，但通常不需要高度精确的浮点计算。 因此，编译器制定者必须提供程序员可以控制的速度和准确性通常完全不同的目标的机制。

某些编译器通过为每种类型的优化提供不同的交换机解决速度和准确性之间的权衡。 这允许开发人员禁用导致更改其特定的应用程序的浮点精度的优化。 尽管此解决方案可能会提供对编译器的控制度很高，它引入了几个其他问题：

- 它通常是不清楚该切换以启用或禁用。
- 禁用任何单个优化可能会非浮点代码的性能产生负面影响。
- 每个其他交换机会产生许多新交换机组合;快速的组合数变得非常笨拙。

因此尽管单独交换机提供的每个优化可能看似有吸引力，使用此类编译器可能很繁琐且不可靠。

许多 c + + 编译器提供*一致性*浮点模型 (通过 **/Op**或 **/fltconsistency**切换) 使开发人员可以创建程序符合使用严格的浮点语义。 时，此模型可阻止编译器使用浮点计算上的大多数优化，同时允许非浮点点代码这些优化。 一致性模型，但是，有深色端。 为了返回不同 FPU 体系结构的几乎所有实现可预测结果 **/Op**舍入到用户的中间表达式指定的精度; 例如，考虑下面的表达式：

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

以便生成一致且可重复结果下的 **/Op**，此表达式进行计算，就像它已实现，如下所示：

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

现在会受到从单精度舍入错误影响的最终结果*在每个步骤中对表达式求值*。 尽管此解释绝对不会中断任何 c + + 语义规则，但是很几乎从未计算浮点表达式的最佳方式。 它是需要通常更，来计算中间尽可能高精度是可行的如导致的。 例如，它将是更好的做法计算表达式`a = b * c + d * e`中作为 in 较高的精度

```cpp
double x = b * c;
double y = d * e;
double z = x + y;
a = (float)z;
```

或更佳

```cpp
long double x = b * c;
long double y = d * e
long double z = x + y;
a = (float)z;
```

在计算中较高的精度的中间结果，最终结果是显著更准确。 篇幅有限，采用一致性模型，用户尝试通过禁用不安全的优化来减少错误时精确地增加错误的可能性。 因此一致性模型可能会严重同时同时提供增加的精度不能保证降低效率。 对严重数字程序员来说，这看起来像一个很好的权衡，模型不通常很好地接收了的主要原因。

从版本 8.0 (Visual C++® 2005)，Microsoft c + + 编译器提供了多更好的选择。 它允许程序员可以选择三种常规浮点模式之一： fp： 精确： fast 和 fp： 严格。

- 下 fp： 精确，仅安全执行优化浮点代码上，而不同于 **/Op**，中间计算一致地执行在最高的实际精度。
- : fast 模式会减轻浮点规则允许的代价是牺牲准确性更频繁的优化。
- fp： 严格模式下提供所有 fp 的常规正确性： 精确时启用 fp 异常语义，并防止非法转换出现 FPU 环境更改 （例如对注册精度，舍入方向等的更改）。

可以通过命令行开关或编译器杂注; 独立控制浮点异常语义默认情况下，浮点异常语义处于禁用状态下 fp： 精确以及是否启用下 fp： 严格。 编译器还提供了控制 FPU 环境敏感度和某些浮点的特定优化，如缩写。 此非常简单的模型为开发人员提供了大量的控制而无需太多编译器开关的负担或不利的副作用的潜在的浮点代码的编译。

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Fp： 精确的浮点语义模式

默认的浮点语义模式是 fp： 精确。 当选中此模式下时，编译器严格遵循一组安全规则时优化浮点运算。 这些规则允许编译器在维护的浮点计算准确性时生成高效的机器代码。 为了便于快速的生产程序，fp： 精确的模型禁用浮点异常语义 （尽管它们可以显式启用）。 Microsoft 已选定 fp： 因为它会创建快速、 准确程序作为默认浮点模式精确。

若要显式请求 fp： 精确模式下使用命令行编译器，使用[/fp： 精确](fp-specify-floating-point-behavior.md)切换：

> cl /fp： 精确 source.cpp

这将指示编译器使用 fp： 为 source.cpp 文件生成代码时的精确语义。 Fp： 精确的模型也可以调用函数逐个函数地使用[float_control 编译器杂注](#the-float-control-pragma)。

下 fp： 精确模式下，编译器永远不会执行任何 perturb 的浮点计算精度的优化。 编译器将始终进行舍入正确在分配、 类型强制转换和函数调用，并中间舍入将一致地执行同样的准确度在如 FPU 注册。 默认情况下启用安全的优化，如的缩写。 异常语义和 FPU 环境敏感度在默认情况下处于禁用状态。

|fp： 精确的语义|说明|
|-|-|
|舍入语义|在分配，显式舍入类型强制转换和函数调用。 将在注册精度对中间表达式进行计算。|
|代数转换|严格遵守非关联、 非分布式浮点代数，除非可以转换保证到始终生成相同的结果。|
|缩写|默认情况下允许使用。 有关详细信息，请参阅部分[fp_contract 杂注](#the-fp-contract-pragma)。|
|浮点计算顺序|编译器可能重新排序浮点表达式求的值，前提是最终结果不会更改。|
|FPU 环境访问|默认情况下已禁用。 有关详细信息，请参阅部分[fenv_access 杂注](#the-fenv-access-pragma)。 假定的默认精度和舍入模式。|
|浮点异常语义|默认情况下已禁用。 有关详细信息，请参阅[/fp： 除](fp-specify-floating-point-behavior.md)。|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>舍入为下 fp 浮点表达式的语义： 精确

Fp： 精确的模型始终执行在最高的实际精度，仅在表达式计算中的某些点显式舍入的中间计算。 舍入为用户指定精度始终发生在四个位置: （a） 发出赋值后，（b） 执行类型转换时，（c） 当浮点值作为参数传递给函数，并将 （d） 时返回的浮点值函数。 因为在注册精度始终执行中间计算，中间结果的准确性是平台从属 (尽管精度始终会至少与指定的用户为准确精度)。

请考虑下面的代码中的赋值表达式。 将在注册精度，计算和则显式舍入为赋值的左侧的类型的赋值运算符 '=' 右侧表达式。

```cpp
float a, b, c, d;
double x;
...
x = a*b + c*d;
```

将计算为

```cpp
float a, b, c, d;
double x;
...
register tmp1 = a*b;
register tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

若要显式舍入中间结果，引入类型转换。 例如，如果前面的代码修改通过添加显式转换，中间表达式 (c * d) 将舍入到的类型转换的类型。

```cpp
float a, b, c, d;
double x;
// . . .
x = a*b + (float)(c*d);
```

将计算为

```cpp
float a, b, c, d;
double x;
// . . .
register tmp1 = a*b;
float tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

此舍入方法的一个含义是，某些看似等效转换实际上没有相同的语义。 例如，以下转换将拆分为两个分配表达式的单个赋值表达式。

```cpp
float a, b, c, d;
// . . .
a = b*(c+d);
```

不是等效于

```cpp
float a, b, c, d;
// . . .
a = c+d;
a = b*a;
```

同样：

```cpp
a = b*(c+d);
```

不是等效于

```cpp
a = b*(a=c+d);
```

由于第二个编码在每个引入其他赋值运算，并因此其他舍入点，这些编码而没有等效的语义。

当函数返回的浮点值时，值将舍入到函数的类型。 当浮点值作为参数传递给函数时，值将舍入到参数的类型。 例如：

```cpp
float sumsqr(float a, float b)
{
   return a*a + b*b;
}
```

将计算为

```cpp
float sumsqr(float a, float b)
{
    register tmp3 = a*a;
    register tmp4 = b*b;
    register tmp5 = tmp3+tmp4;
    return (float) tmp5;
}
```

同样：

```cpp
float w, x, y, z;
double c;
...
c = symsqr(w*x+y, z);
```

将计算为

```cpp
float x, y, z;
double c;
...
register tmp1 = w*x;
register tmp2 = tmp1+y;
float tmp3 = tmp2;
c = symsqr( tmp3, z);
```

### <a name="architecture-specific-rounding-under-fpprecise"></a>特定于体系结构的舍入下 fp： 精确

|处理器|舍入精度中间表达式|
|-|-|
|x86|使用 16 位指数由提供的扩展范围情况下，中间表达式计算在默认 53 位精度。 当这些 53:16 值"溢出"到内存 （也可以进行函数调用期间） 时，扩展的指数范围将缩小到 11 位。 也就是说，溢出的值都转换为使用仅一个 11 位指数按标准的双精度的格式。<br/>用户可以切换到扩展的 64 位精度，用于通过更改浮点控制字使用中间舍入`_controlfp`和通过启用 FPU 环境访问 (请参阅[fenv_access 杂注](#the-fenv-access-pragma))。 但是，当扩展的精度寄存器的值溢出到内存中，中间结果将仍舍入为双精度。<br/>此特定的语义进行更改。|
|amd64|在 amd64 FP 语义是从其他平台稍有不同。 出于性能原因，在提供给最大精度而不是在可用的提供给最大精度的其中一个操作数的计算中间的操作。  若要强制使用更宽的精度大于操作数要计算的计算，用户需要引入子表达式中的至少一个操作数转换运算。<br/>此特定的语义进行更改。|

### <a name="algebraic-transformations-under-fpprecise"></a>下 fp 代数转换： 精确

当 fp： 启用精确模式，编译器将永远不会执行代数转换*除非最终结果是证明为相同*。 许多实数算术的熟悉代数规则不始终保留的浮点运算。 例如，以下表达式是等效的实数，但不是一定对于浮点型值。

|窗体|描述|
|-|-|
|`(a+b)+c = a+(b+c)`|添加的的关联规则|
|`(a*b)*c = a*(b*c)`|用于乘法运算的关联规则|
|`a*(b+c) = a*b + b*c`|乘法通过加法的分布|
|`(a+b)(a-b) = a*a-b*b`|代数将分解|
|`a/b = a*(1/b)`|除数乘法逆元|
|`a*1.0 = a`|乘法恒等元|

如下图所示在简介的示例中使用的函数`KahanSum`，编译器可能会想要以生成速度更快的程序中执行各种代数转换。 尽管优化依赖于此类代数转换几乎始终是正确的有一些情况下它们是完全安全。 例如，它是有时需要将被除*常量*乘法运算的乘法逆的常数的值：

```cpp
const double four = 4.0;
double a, b;
...

a = b/four;
```

可能转换为

```cpp
const double four = 4.0;
const double tmp0 = 1/4.0;
double a, b;
...
a = b*tmp0;
```

这是安全的转换，因为优化器可以确定在编译时该 x / 4.0 = = x*(1/4.0) 对于所有的浮点值的 x，包括无穷大和 NaN。 通过将替换为乘法除法运算，编译器可以保存多个周期-尤其是在不直接实现的除法中，但需要编译器生成的倒数近似值组合并乘法加法 FPUs 上说明。 编译器可能会执行此类优化下 fp： 精确仅当替换乘法产生完全相同的结果为除法。 编译器还可能执行普通转换下 fp： 精确，提供结果是相同的。 这些方法包括：

|窗体|描述
|-|-|
|`(a+b) == (b+a)`|添加的的可交换性规则|
|`(a*b) == (b*a)`|用于乘法运算的可交换性规则|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|乘数 1.0 的乘法|
|`x/1.0*y == x*y/1.0 == x*y`|1.0 的除法|
|`2.0*x == x+x`|相乘 2.0|

### <a name="contractions-under-fpprecise"></a>下 fp 缩写： 精确

许多现代的浮点单位的一个主要体系结构功能是能够执行乘法跟作为单个操作随没有中间舍入误差的补充。 例如，Intel 的 Itanium 体系结构介绍了如何将合并每个这些三元操作 (*b + c)，(* b c) 和 (c a * b)，到单个浮点指令 (fma、 fms 和 fnma 分别)。 以下单个说明速度较快比执行单独相乘，添加说明，并且更加准确由于没有产品没有中间舍入。 此优化可以显著加快函数包含若干个交错 multiply 和添加操作。 例如，考虑以下算法计算两个 n 维向量的点积。

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

可以执行此计算的一系列乘法-加法说明的窗体 p = p + x [i] * y [i]。

缩写式优化可以独立使用进行控制`fp_contract`编译器杂注。 默认情况下，fp： 精确的模型可以缩写因为它们提高准确性和速度。 下 fp： 精确，编译器将永远不会协定具有显式舍入的表达式。
示例

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add
etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>下 fp 浮点表达式求值顺序： 精确

保留的浮点表达式计算顺序的优化始终是安全的因此在 fp 允许： 精确的模式。 请考虑下面的函数的计算个单精度中的两个 n 维向量的点积。 下面的第一个代码块是原始函数作为其可能有一位程序员编码跟相同的功能部分的循环展开优化后。

```cpp
//original function
float dotProduct( float x[], float y[], int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}

//after a partial loop-unrolling
float dotProduct( float x[], float y[], int n )
{
   int n4= n/4*4; // or n4=n&(~3);
   float p=0;
   int i;

   for (i=0; i<n4; i+=4)
   {
      p+=x[i]*y[i];
      p+=x[i+1]*y[i+1];
      p+=x[i+2]*y[i+2];
      p+=x[i+3]*y[i+3];
   }

   // last n%4 elements
   for (; i<n; i++)
      p+=x[i]*y[i];

   return p;
}
```

此优化的主要优点是它可以条件循环分支的数目减少 75%。 此外，通过增加循环体中的操作的数目，编译器可能具有更多机会来进一步优化。 例如，某些 FPUs 可能能够执行在 p + = 乘法-加法 x [i] * 同时提取 x [i + 1] 的值时的 y [i] 和 y [i + 1] 在下一步中使用。 这种类型是优化的完全安全来进行浮点计算的因为它将保留操作的顺序。

它通常是编译器对整个操作以便生成更快的代码重新排序非常有利的。 考虑下列代码：

```cpp
double a, b, c, d;
double x, y, z;
...
x = a*a*a + b*b*b + c*c*c;
...
y = a*a + b*b + c*c;
...
z = a + b + c;
```

C + + 语义规则指示该程序应产生的结果，就像它首先计算结果 x，y 然后最后 z。 假定编译器只需四个可用的浮点寄存器。 如果编译器强制来计算 x、 y 和 z 顺序情况下，它可能选择生成代码与下面的语义：

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute x
r0 = a;         // r1 = a*a*a
r1 = r0*r0;
r1 = r1*r0;
r0 = b;         // r2 = b*b*b
r2 = r0*r0;
r2 = r2*r0;
r0 = c;         // r3 = c*c*c
r3 = r0*r0;
r3 = r3*r0;
r0 = r1 + r2;
r0 = r0 + r3;
x = r0;         // x = r1+r2+r3
// . . .
// Compute y
r0 = a;         // r1 = a*a
r1 = r0*r0;
r0 = b;         // r2 = b*b
r2 = r0*r0;
r0 = c;         // r3 = c*c
r3 = r0*r0;
r0 = r1 + r2;
r0 = r0 + r3;
y = r0;         // y = r1+r2+r3
// . . .
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1 + r2;
r0 = r0 + r3;
z = r0;         // z = r1+r2+r3
```

有几个清楚地冗余运算是这种编码。 如果编译器严格遵循 c + + 语义规则，此排序操作，因为程序可能在每个分配访问 FPU 环境之间。 但是，fp 的默认设置： 精确的使编译器能够优化，就好像该程序不访问该环境，使其能够重新排列这些表达式。 然后它就可以通过按相反的顺序，如下所示，计算三个值中删除重复内容：

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1+r2;
r0 = r0+r3;
z = r0;
...
// Compute y
r1 = r1*r1;
r2 = r2*r2;
r3 = r3*r3;
r0 = r1+r2;
r0 = r0+r3;
y = r0;
...
// Compute x
r0 = a;
r1 = r1*r0;
r0 = b;
r2 = r2*r0;
r0 = c;
r3 = r3*r0;
r0 = r1+r2;
r0 = r0+r3;
x = r0;
```

此编码是明显更好，具有降低的 fp 指令数几乎 40%。 结果为 x，y 和 z 为相同和前面一样，但计算有较少的开销。

下 fp： 精确，编译器也可能会*隔行扫描*以便生成更快的代码的公用子表达式。 例如，可能会按以下方式编写的代码以计算 quadratic 公式的根：

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

尽管这些表达式只是单个操作不同，程序员可能已编写它这种方式，若要确保每个根值，将计算中的最高的实际精度。 下 fp： 精确，编译器可以自由地隔行扫描 root0 和 root1 删除而不会丢失精度的公用子表达式的计算。 例如，以下已删除多个冗余步骤生成完全相同的答案时。

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

其他优化可能会尝试移动的某些独立的表达式求值。 请考虑以下算法，其中包含在循环主体条件分支。

```cpp
vector<double> a(n);
double d, s;
// . . .
for (int i=0; i<n; i++)
{
   if (abs(d)>1.0)
      s = s+a[i]/d;
   else
      s = s+a[i]*d;
}
```

编译器可能会检测到的表达式的值 (abs(d) > 1) 是固定在循环体中。 这使编译器能够"提升"if 外部循环正文中，将上面的代码转换为以下语句：

```cpp
vector<double> a(n);
double d, s;
// . . .
if (abs(d)>1.0)
   for (int i=0; i<n; i++)
      s = s+a[i]/d;
else
   for (int i=0; i<n; i++)
      s = s+a[i]*d;
```

在转换后，没有不再条件分支中的循环主体，从而极大地提高循环的整体性能。 这种类型的优化是完全安全因为表达式的计算 (abs(d) > 1.0) 独立于其他表达式。

出现 FPU 环境访问或浮点异常，因为它们会更改语义流程被 contraindicated 这些类型的优化。 这种优化仅下有 fp： 精确模式因为默认情况下禁用 FPU 环境访问和浮点异常语义。 访问 FPU 环境的函数可以通过使用显式禁用这种优化`fenv_access`编译器杂注。 同样，使用浮点异常的函数应使用`float_control(except ... )`编译器杂注 (或使用 **/fp： 除**命令行开关)。

总之，fp： 精确模式允许编译器重新排序的浮点表达式求值，前提是最终结果不会被更改，并且结果不依赖 FPU 环境或浮点异常。

### <a name="fpu-environment-access-under-fpprecise"></a>下 fp FPU 环境访问： 精确

当 fp： 启用精确模式，编译器将假定程序不会访问或更改的 FPU 环境。 如上文所述，此假设使编译器能够重新排序或移动浮点运算，以提高效率下 fp： 精确。

有些程序可能会更改使用的浮点舍入方向`_controlfp`函数。 例如，某些程序计算上限和错误下限算术运算上通过执行相同的计算两次，第一次时向负无穷舍入，然后，而向正无穷舍入。 由于 FPU 提供一种简便方式控制舍入，程序员也可以选择通过更改 FPU 环境更改舍入模式。 下面的代码计算一个具体错误绑定的浮点乘法通过更改 FPU 环境。

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

下 fp： 精确，编译器始终将假定默认 FPU 环境，以便优化器可以自由地忽略对的调用`_controlfp`并减少到 cUpper 的上述分配 = cLower = * b; 这清楚地将产生不正确的结果。 若要防止这种优化，通过使用启用 FPU 环境访问`fenv_access`编译器杂注。

其他程序可能会尝试通过检查 FPU 的状态字检测某些浮点错误。 例如，下面的代码检查的条件被零除和准确条件

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = r;
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

下 fp： 精确，重新排序表达式计算的优化可能更改的某些错误发生的点。 程序可访问状态字应使用启用 FPU 环境访问`fenv_access`编译器杂注。

有关详细信息，请参阅部分[fenv_access 杂注](#the-fenv-access-pragma)。

### <a name="floating-point-exception-semantics-under-fpprecise"></a>浮点异常语义下 fp： 精确

默认情况下，浮点异常语义处于禁用状态下 fp： 精确。 大多数 c + + 程序员更喜欢进行处理而不必使用系统或 c + + 异常的异常的浮点条件。 此外，如上文所述，禁用浮点异常语义允许编译器更大的灵活性时优化浮点运算。 可以使用两种 **/fp： 除**切换或`float_control`杂注时使用 fp 启用浮点异常语义： 精确的模型。

有关详细信息，请参阅部分[启用浮点异常语义](#enabling-floating-point-exception-semantics)。

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>浮点语义: fast 模式

启用： fast 模式后，编译器会该 fp 减轻规则： 精确使用时优化浮点运算。 此模式下是使编译器能够进一步优化浮点代码的速度，代价是浮点准确性和正确性。 不要依赖于高度精确的浮点计算的程序可能会遇到重大速度提高通过启用： fast 模式。

使用启用： fast 浮点模式[/fp:fast](fp-specify-floating-point-behavior.md) ，如下所示的命令行编译器开关：

> cl /fp:fast source.cpp

下面的示例指示编译器为 source.cpp 文件生成代码时使用： fast 语义。 : Fast 模型也可以调用函数逐个函数地使用`float_control`编译器杂注。

有关详细信息，请参阅部分[float_control 杂注](#the-float-control-pragma)。

在： fast 模式下，编译器可能执行 alter 的浮点计算精度的优化。 编译器不在分配正确 round、 类型强制转换或函数调用，并中间舍入将不始终会执行。 浮点的特定优化，如的缩写，始终启用状态。 浮点异常语义和 FPU 环境敏感度是禁用并且不可用。

|: fast 语义|说明
|-|-|
|舍入语义|在分配，显式舍入类型强制转换，并且函数调用可能会被忽略。<br/>中间表达式可能在小于注册根据性能要求的精度舍入。|
|代数转换|编译器可能转换表达式根据实际数目关联、 分布式代数;不保证这些转换都是准确或正确。|
|缩写|始终处于启用状态;不能通过杂注来禁用 `fp_contract`|
|浮点计算顺序|即使此类更改可能会更改的最终结果，编译器可能重新排序的浮点表达式的计算。|
|FPU 环境访问|禁用。 不可用|
|浮点异常语义|禁用。 不可用|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>舍入为下： fast 浮点表达式的语义

与 fp 不同： 精确模型，： fast 模型执行中间计算在最方便的精度。 在分配，舍入类型强制转换，不可能始终会执行函数调用。 例如，下面的第一个函数引入了三个单精度变量 (`C`，`Y`和`T`)。 编译器可能选择注册局部变量这些变量，有效的类型提升`C`，`Y`和`T`到双精度。

原始功能：

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

变量能：

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

在此示例中，： fast 具有 subverted 原始函数的意图。 最后一个优化结果，保存在变量中`sum`，可能会非常 perturbed 从正确的结果。

下： fast，编译器将通常尝试维护至少指定源代码的精度。 但是，在某些情况下编译器可以选择执行中间表达式*降低精度*比指定的源代码中。 例如，下面的第一个代码块调用平方根函数的双精度版本。 下： fast，在某些情况下，例如当的结果和该函数的操作数显式强制转换为单精度，编译器可以选择为双精度的调用替换`sqrt`通过单精度调用`sqrtf`函数。 因为强制转换，请确保进入值`sqrt`和推出的值舍入为单精度，这只会更改的舍入的位置。 如果进入 sqrt 的值是一个双精度值，而编译器执行此转换，多达一半的精度位数可能是错误。

原始函数

```cpp
double sqrt(double);
// . . .
double a, b, c;
float f1, f2;
// . . .
float length = (float)sqrt((float)(a*a + b*b + c*c));
float sum = (float) ((double)f1 + (double)f2);
```

优化的函数

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
double tmp0 = a*a + b*b + c*c;
float tmp1 = tmp0;    // round of parameter value
float length = sqrtf(tmp1); // rounded sqrt result
float sum = f1 + f2;
```

虽然不太准确，这种优化时，可能尤其有益以提供单精度，内部函数的函数的版本，如处理器为目标`sqrt`。 只需精确时，编译器会使用这种优化是平台和上下文相关。

此外，还有可能在任何可用于编译器的精度级别执行的中间计算的精度不确定的一致性。 尽管编译器将尝试至少维护的代码由指定的精度级别，则： fast 允许向下转换的中间计算优化以便生成更快或更小的机器代码。 例如，编译器可能来进一步优化从上面的代码要舍入为单精度中间乘法运算的一些。

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
float tmp0 = a*a;     // round intermediate a*a to single-precision
float tmp1 = b*b;     // round intermediate b*b to single-precision
double tmp2 = c*c;    // do NOT round intermediate c*c to single-precision
float tmp3 = tmp0 + tmp1 + tmp2;
float length = sqrtf(tmp3);
float sum = f1 + f2;
```

使用较低精度浮点单元，如 SSE2，若要执行的中间计算，则可能会导致这种类型的其他舍入。 : Fast 舍入的准确性因此是平台从属;适用于一个处理器编译的代码可能不一定适用于另一个处理器。 它是从左到使用者确定速度好处是否超过任何准确性问题。

如果对于特定函数特别成问题： fast 优化，浮点模式可以本地切换为 fp： 精确使用`float_control`编译器杂注。


### <a name="algebraic-transformations-under-fpfast"></a>下： fast 代数转换

: Fast 模式选项使编译器能够执行某些操作，不安全的代数转换为浮点点表达式。 例如，以下不安全优化可能用于下： fast。

||||
|-|-|-|
|原始代码|步骤 1|第 2 步
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

在步骤 1 中，编译器遵循`z = y – a – b`也始终等于零。 虽然这是从技术上讲无效观察值，它是在： fast 允许。 然后，编译器将传播到变量 z 的每个后续使用的常量值零。 在步骤 2 中，编译器进一步优化通过观察， `x - 0 == x`， `x * 0 == 0`，等等。同样，即使这些观察结果不是严格有效的它们是在： fast 允许。 优化的代码现已快得多，但也可能会有相当大不太准确或甚至不正确。

任何以下 （不安全） 的代数规则可能启用： fast 模式时采用优化器中：

|||
|-|-|
|窗体|描述|
|`(a + b) + c = a + (b + c)`|添加的的关联规则|
|`(a * b) * c = a * (b * c)`|用于乘法运算的关联规则|
|`a * (b + c) = a * b + b * c`|乘法通过加法的分布|
|`(a + b)(a - b) = a * a - b * b`|代数将分解|
|`a / b = a * (1 / b)`|除数乘法逆元|
|`a * 1.0 = a, a / 1.0 = a`|乘法恒等元|
|`a ± 0.0 = a, 0.0 - a = -a`|加法恒等元|
|`a / a = 1.0, a - a = 0.0`|取消|

如果对某个特殊功能特别成问题： fast 优化，浮点模式可以本地切换为 fp： 精确使用`float_control`编译器杂注。

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>下： fast 浮点表达式计算顺序

与 fp 不同： 精确： fast 使编译器能够重新排列以便生成更快的代码的浮点操作。 因此，在: fast 下的某些优化可能不保留表达式的预期的顺序。 例如，考虑以下函数计算两个 n 维向量的点积。

```cpp
float dotProduct( float x[], float y[],
                  int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

优化器可能在： fast 下, 执行的标量降低`dotProduct`函数有效地转换函数，如下所示：

```cpp
float dotProduct( float x[], float y[],int n )
{
    int n4= n/4*4; // or n4=n&(~3);
    float p=0, p2=0, p3=0, p4=0;
    int i;

    for (i=0; i<n4; i+=4)
    {
        p+=x[i]*y[i];
        p2+=x[i+1]*y[i+1];
        p3+=x[i+2]*y[i+2];
        p4+=x[i+3]*y[i+3];
    }
    p+=p2+p3+p4;

    // last n%4 elements
    for (; i<n; i++)
    p+=x[i]*y[i];

    return p;
}
```

在优化版本的函数四个单独的产品求和是同时执行，然后加在一起。 此优化可以加快计算`dotProduct`通过得那么多，具体取决于目标处理器，但最终结果的以下四个因素可能因此不准确并使其无法工作。 如果这种优化单个函数或翻译单元特别成问题，浮点模式可以本地切换为 fp： 精确使用`float_control`编译器杂注。

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>Fp： 浮点语义的严格模式

当 fp： 启用严格模式下，编译器遵循以统一的规则该 fp： 精确使用时优化浮点运算。 此模式还启用浮点异常语义和到 FPU 环境的大小写并禁用某些优化，如缩写。 它是操作的严格模式。

Fp： 使用启用严格的浮点模式[/fp: strict](fp-specify-floating-point-behavior.md) ，如下所示的命令行编译器开关：

> cl /fp: strict source.cpp

下面的示例指示编译器使用 fp： 严格语义为 source.cpp 文件生成代码时。 Fp： 严格模式也可以调用函数逐个函数地使用`float_control`编译器杂注。

有关详细信息，请参阅部分[float_control 杂注](#the-float-control-pragma)。

下 fp： 严格模式下，编译器永远不会执行任何 perturb 的浮点计算精度的优化。 编译器将始终进行舍入正确在分配、 类型强制转换和函数调用，并中间舍入将一致地执行同样的准确度在如 FPU 注册。 默认情况下启用浮点异常语义和 FPU 环境敏感度。 某些优化，如的缩写，已禁用，因为编译器无法保证在每个用例的正确性。

|fp： 严格的语义|说明|
|-|-|
|舍入语义|在分配，显式舍入类型强制转换和函数调用<br/>将在注册精度对中间表达式进行计算。<br/>与 fp 相同： 精确|
|代数转换|严格遵守非关联、 非分布式浮点代数，除非可以转换保证到始终生成相同的结果。<br/>与 fp 相同： 精确|
|缩写|始终处于禁用状态|
|浮点计算顺序|编译器不重新排序浮点表达式求的值|
|FPU 环境访问|始终处于启用状态。|
|浮点异常语义|默认情况下启用。|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>浮点异常语义下 fp： 严格

默认情况下，浮点异常语义启用下 fp： 严格模式。 若要禁用这些语义，使用 **/fp： 除-** 切换或引入`float_control(except, off)`杂注。

有关详细信息，请参阅部分[启用浮点异常语义](#enabling-floating-point-exception-semantics)和[float_control 杂注](#the-float-control-pragma)。

## <a name="the-fenvaccess-pragma"></a>Fenv_access 杂注

用法：

```cpp
#pragma fenv_access( [ on  | off ] )
```

[Fenv_access](../../preprocessor/fenv-access.md)杂注使编译器能够进行的某些优化，可能会破坏 FPU 标记测试和 FPU 模式更改。 时的状态`fenv_access`处于禁用状态，则编译器可以假定默认 FPU 模式才有效且未测试 FPU 标志。 默认情况下，环境访问禁用的 fp： 精确模式，尽管它可能显式启用使用此杂注。 下 fp： 严格，`fenv_access`始终处于启用状态，并且无法禁用。 下： fast，`fenv_access`始终处于禁用状态，并且不能启用。

Fp 中所述： 精确部分中，某些程序员可能会更改浮点舍入方向使用`_controlfp`函数。 例如，若要计算的算术运算的上限和下限误差界限，某些程序执行相同的计算两次，第一次时向负无穷舍入然后时向正无穷舍入。 由于 FPU 提供一种简便方式控制舍入，程序员也可以选择通过更改 FPU 环境更改舍入模式。 下面的代码计算一个具体错误绑定的浮点乘法通过更改 FPU 环境。

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

禁用时，`fenv_access`杂注允许编译器假定默认 FPU 环境; 因此优化器是自由地忽略对的调用`_controlfp`并减少到的上述分配`cUpper = cLower = a*b`。 如果启用，但是，`fenv_access`可防止这种优化。

程序可能还将检查 FPU 状态字，来检测某些浮点错误。 例如，下面的代码检查的条件被零除和准确条件

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

当`fenv_access`是禁用，编译器可能会重新排列浮点表达式，因此可能从而影响 FPU 状态检查的执行顺序。 启用`fenv_access`可防止这种优化。

## <a name="the-fpcontract-pragma"></a>Fp_contract 杂注

用法：

```cpp
#pragma fp_contract( [ on | off ] )
```

Fp 中所述： 精确部分中，缩写式是许多现代的浮点单位的基本体系结构功能。 缩写提供执行乘法跟添加作为单个操作随没有中间舍入误差的能力。 以下单个说明速度较快比执行单独相乘，添加说明，并且更加准确由于没有产品没有中间舍入。 签约的操作可以计算的值`(a*b+c)`这两种操作像一样计算结果为无限精度，则舍入为最接近的浮点数。 此优化可以显著加快函数包含若干个交错 multiply 和添加操作。 例如，考虑以下算法计算两个 n 维向量的点积。

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

可以执行此计算的一系列乘法-加法的窗体的说明`p = p + x[i]*y[i]`。

[Fp_contract](../../preprocessor/fp-contract.md)杂注指定是否可以收缩浮点表达式。 默认情况下，fp： 精确模式允许缩写由于它们提高准确性和速度。 缩写始终启用： fast 模式。 但是，这是因为缩写可以破坏的错误情况，显式检测`fp_contract`杂注 fp 下将始终被禁用： 严格模式。 可能的表达式的示例收缩时`fp_contract`启用杂注：

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

## <a name="the-floatcontrol-pragma"></a>Float_control 杂注

**/Fp： 精确**， **/fp:fast**， **/fp: strict**和 **/fp： 除**交换机来控制对文件的文件的浮点语义基数。 [Float_control](../../preprocessor/float-control.md)杂注提供了函数的函数分别对此类控制。

用法：

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

杂注`float_control(push)`和`float_control(pop)`分别推送和弹出浮点模式和到堆栈上的异常选项的当前状态。 请注意，状态`fenv_access`和`fp_contract`杂注不受`pragma float_control(push/pop)`。

调用杂注`float_control(precise, on)`将启用和`float_control(precise, off)`将禁用精确模式语义。 同样，杂注`float_control(except, on)`将启用和`float_control(except, off)`将禁用异常语义。 时还将启用精确的语义，才可启用异常语义。 时可选`push`自变量是否存在、 的状态`float_control`选项推送之前更改语义。

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>设置基于函数的函数的浮点语义模式

命令行开关实际上是用于设置四个其他浮点杂注的速记。 若要显式选择的函数的函数基于特定的浮点语义模式，选择每个四个浮点选项杂注下表中所述：

||||||
|-|-|-|-|-|
||float_control(precise)|float_control(except)|fp_contract|fenv_access|
|/fp: strict|on|on|关闭|on|
|/fp: strict /fp： 除-|on|关闭|关闭|on|
|/fp： 精确|on|关闭|on|关闭|
|/fp： 精确 /fp： 除外|on|on|on|关闭|
|/fp:fast|关闭|关闭|on|关闭|

例如，以下显式启用： fast 语义。

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> 必须关闭"精确"的语义之前关闭异常语义。

## <a name="enabling-floating-point-exception-semantics"></a>启用浮点异常语义

某些异常的浮点条件，例如除以零，可能会导致 FPU 发出信号硬件异常。 默认情况下，浮点异常处于禁用状态。 通过修改 FPU 控制字与启用了浮点异常`_controlfp`函数。 例如，下面的代码能够通过零除浮点异常：

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

启用通过零除异常后，任何与分母等于零的除法运算将导致 FPU 异常终止。

若要还原为默认模式 FPU 控制字，调用`_controlfp(_CW_DEFAULT, ~0)`。

启用与浮点异常语义 **/fp： 除**标志不是与启用浮点异常。 当启用浮点异常语义时，编译器必须考虑可能会出现任何浮点运算可能引发异常。 由于 FPU 是一个单独的处理器单元，可以与其他单元上的说明并发执行在 FPU 上执行的说明。

启用浮点异常后，将暂停执行有问题的指令 FPU 并将其然后通过设置 FPU 状态字指示一个异常情况。 当 CPU 到达下一个浮点指令时，它将首先检查任何挂起的 FPU 异常。 如果没有挂起的异常，处理器就会捕获它通过调用由操作系统提供的异常处理程序。 这意味着时浮点运算遇到一个异常情况，, 将不会检测相应的异常，直到执行下一步的浮点运算。 例如，下面的代码将捕获通过零除异常：

```cpp
double a, b, c;
// . . .
// ...unmasking of FPU exceptions omitted...
__try
{
   b/c; // assume c==0.0
   printf("This line shouldn't be reached when c==0.0\n");
   c = 2.0*b;
}
__except( EXCEPTION_EXECUTE_HANDLER )
{
   printf("SEH Exception Detected\n");
}
// . . .
```

如果在表达式中发生被零除条件 = b/c，FPU 不会陷阱/引发表达式 2.0 中的下一步浮点操作直到异常 * b。 这将导致下面的输出：

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

Printf 对应的输出的第一行应尚未达到;它已达到因为直到执行到达 2.0 未引发浮点异常引起表达式 b/c * b。 若要引发的异常之后执行 b/c，则编译器必须引入"等待"指令：

```cpp
// . . .
   __try
   {
      b/c; // assume this expression will cause a "divide-by-zero" exception
      __asm fwait;
      printf("This line shouldn't be reached when c==0.0\n");
      c = 2.0*b;
   }
// . . .
```

此"等待"指令强制处理器同步与 FPU 的状态并处理任何挂起的异常。 编译器将仅生成这些"等待"的说明启用浮点语义时。 当这些语义都被禁用，因为默认情况下时，程序使用浮点异常时可能遇到同步错误，类似于上面。

当启用时的浮点语义时，编译器将不会仅引入"等待"说明，它还会阻止编译器从非法优化浮点代码出现情况下，可能出现的异常。 这包括 alter 引发异常的点的任何转换。 由于这些因素，启用浮点语义可能会显著减少生成的机器代码，从而降低应用程序的性能的效率。

默认情况下 fp 启用浮点异常语义： 严格模式。 若要启用这些语义中 fp： 精确模式下，添加 **/fp： 除**切换到命令行编译器。 浮点异常语义还可以启用和禁用函数逐个函数地使用`float_control`杂注。

### <a name="floating-point-exceptions-as-c-exceptions"></a>浮点异常作为 c + + 异常

所有硬件例外情况之外，浮点异常本质上不会导致 c + + 异常，但改为触发结构化的异常。 为映射到 c + + 异常时浮点的结构化的异常，用户可以引入自定义的 SEH 异常转换器。 首先，引入了与每个浮点异常相对应的 c + + 异常：

```cpp
class float_exception : public std::exception {};

class fe_denormal_operand : public float_exception {};
class fe_divide_by_zero : public float_exception {};
class fe_inexact_result : public float_exception {};
class fe_invalid_operation : public float_exception {};
class fe_overflow : public float_exception {};
class fe_stack_check : public float_exception {};
class fe_underflow : public float_exception {};
```

然后，引入了转换函数，它将检测浮点 SEH 异常并引发相应的 c + + 异常。 若要使用此函数，设置与当前的进程线程的结构化异常处理程序转换器[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)从运行时库函数。

```cpp
void se_fe_trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )
{
    switch (u)
    {
    case STATUS_FLOAT_DENORMAL_OPERAND:   throw fe_denormal_operand();
    case STATUS_FLOAT_DIVIDE_BY_ZERO:     throw fe_divide_by_zero();
   etc...
    };
}
// . . .
_set_se_translator(se_fe_trans_func);
```

一旦初始化此映射时，浮点异常的行为如同它们是 c + + 异常。 例如：

```cpp
try
{
   // floating-point code that might throw divide-by-zero
   // or other floating-point exception
}
catch(fe_divide_by_zero)
{
    cout << "fe_divide_by_zero exception detected" << endl;
}
catch(float_exception)
{
    cout << "float_exception exception detected" << endl;
}
```

## <a name="references"></a>参考资料

[关于浮点运算，每个计算机科学家应知道什么](http://pages.cs.wisc.edu/~david/courses/cs552/S12/handouts/goldberg-floating-point.pdf)由 David 翰伟。

## <a name="see-also"></a>请参阅

[优化代码](optimizing-your-code.md)<br/>
