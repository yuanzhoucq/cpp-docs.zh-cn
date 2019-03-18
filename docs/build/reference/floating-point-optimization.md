---
title: MSVC 浮点优化
ms.date: 03/09/2018
ms.topic: conceptual
ms.openlocfilehash: 78c5c310f2f348b5cfa5a92feb65e265d28560d9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814366"
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Microsoft Visual c + + 浮点优化

获取有关优化浮点代码使用管理浮点语义的 Microsoft c + + 编译器的方法的句柄。 创建快速程序，同时确保对浮点代码执行了唯一安全的优化。

## <a name="optimization-of-floating-point-code-in-c"></a>C + + 中的浮点代码优化

优化的 c + + 编译器不只将源代码转换为机器代码，则会安排的方式提高效率和/或减小大小中的计算机说明。 遗憾的是，很多常见的优化是不一定是安全时应用于浮点计算。 很好的例子可以看到与以下总和算法，David 翰伟，"什么每个计算机科学家应知道有关浮点算术"，从*计算调查*、 年 3 月 1991 年 pg。 203:

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

此函数会添加 n **float**数组向量中的值`A`。 在循环主体中，算法将计算"更正"值，然后将其应用到下一步的总和。 此方法可以大幅减少累积舍入误差相比简单求和，同时保留的时间复杂度 o （n）。

一个简单的 c + + 编译器可能认为浮点算术，遵循相同的代数实数算术规则。 此类编译器可能然后会错误地认为

> C = T - sum - Y ==> (sum+Y)-sum-Y ==> 0;

即，C 感知的值始终是常数零。 如果此常数值然后传播到后续的表达式，则循环主体减少到简单求和。 准确地说，是

> Y = A[i] - C ==> Y = A[i]<br/>T = sum + Y ==> T = sum + A[i]<br/>sum = T ==> sum = sum + A[i]

因此，对简单编译器的逻辑转换`KahanSum`函数将是：

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

转换的算法速度更快，尽管*根本不是程序员的意图的准确表示*。 已完全删除精心设计的错误更正和我们所留下使用简单、 直接求和算法使用所有相关联的错误。

当然，复杂的 c + + 编译器会知道这带来了代数规则的实际算术不适通常用于浮点运算。 但是，复杂 c + + 编译器可能仍错误地解释了程序员的意图。

请考虑优化常见的尝试尽可能 （名为"注册"的值） 在寄存器中保存尽可能多的值。 在中`KahanSum`示例中，这种优化可能会尝试注册局部变量变量`C`，`Y`和`T`由于它们只在循环主体中使用。 如果注册精度为 52bits (double) 而不是 23bits （单个），这种优化有效类型将提升`C`，`Y`并`T`键入**double**。 如果 sum 变量不是同样以内，它将保持编码中单精度。 这将转换的语义`KahanSum`所示

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

尽管`Y`，`T`并`C`此新的编码可能产生不太准确的结果取决于中的值以更高的精度，现在计算`A[]`。 因此即使看似无害的优化可能会带来负面影响。

这些类型的优化问题并不限于"复杂"的浮点代码。 当错误地优化，甚至简单的浮点算法可能会失败。 请考虑一个简单、 直接求和算法：

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

因为某些浮点单位是能够同时执行多个操作，可以选择一个编译器吸引标量降低优化。 这种优化有效地将上述简单的 Sum 函数转换为以下：

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

该函数现在维护四个单独的求和，可以同时处理每个步骤。 尽管已优化的函数现在要快得多，但优化的结果会从非优化结果大不相同。 在进行此更改，编译器假定关联浮点加法;也就是说，这些两个表达式是等效： `(a + b) + c == a + (b + c)`。 但是，关联性并不总是为浮点数，则返回 true。 而不是计算为总和：

```cpp
sum = A[0]+A[1]+A[2]+...+A[n-1];
```

转换后的函数现在计算形式的结果

```cpp
sum = (A[0]+A[4]+A[8]+...)
    + (A[1]+A[5]+A[9]+...)
    + (A[2]+A[6]+A[10]+...)
    + (A[3]+A[7]+A[11]+...);
```

对于某些值的`A[]`，加法运算的此不同的排序可能产生意外的结果。 若要更加复杂的情况，某些编程人员可能选择预计这种优化并相应地对它们进行补偿。 在这种情况下，程序可以构造数组`A`中以不同的顺序，以便优化的总和产生预期的结果。 此外，在许多情况下优化结果的准确性可能会"足够接近"。 当优化提供极具吸引力的速度优势时，也是如此。 视频游戏，例如，需要尽可能多的速度，但通常不需要高度精确的浮点计算。 编译器创建者因此必须提供对编程人员控制的速度和准确性通常完全不同的目标的机制。

某些编译器通过优化每个类型提供不同的交换机解决速度和准确性之间的权衡。 这允许开发人员禁用导致其特定的应用程序的浮点准确性对更改的优化。 尽管此解决方案可能会提供很大程度控制编译器，它引入了几个其他问题：

- 它通常是不清楚该开关启用或禁用。
- 禁用任何单个优化可能会非浮点代码的性能产生负面影响。
- 每个其他开关会产生许多新的开关组合;快速的组合数变得难以处理。

因此尽管单独交换机提供的每个优化可能看起来有吸引力，使用此类编译器可能繁琐且不可靠。

提供了许多 c + + 编译器*一致性*浮点模型 (通过 **/Op**或 **/fltconsistency**切换) 使开发人员创建程序兼容使用严格浮点语义。 时，此模型可防止同时允许非浮动点代码这些优化措施上浮点计算中使用大多数优化编译器。 一致性模型，但是，有一个深端。 为了在不同 FPU 体系结构，几乎所有的实现上返回可预测的结果 **/Op**倒圆角中间表达式为用户指定的精度; 例如，考虑下面的表达式：

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

若要生成一致且可重复结果下的 **/Op**，像它已实现的如下所示获取计算此表达式：

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

最终结果现在受到单精度舍入误差*在每个步骤中对表达式求值*。 尽管此解释严格不会中断任何 c + + 语义规则，但几乎从不是浮点表达式进行计算的最佳方式。 它是通常更需要计算中间结果尽可能高精度切实可行的前提。 例如，它会好一些计算表达式`a = b * c + d * e`中作为在较高的精度

```cpp
double x = b * c;
double y = d * e;
double z = x + y;
a = (float)z;
```

或者更确切地说

```cpp
long double x = b * c;
long double y = d * e
long double z = x + y;
a = (float)z;
```

在计算中较高的精度的中间结果，最终结果是明显更准确。 讽刺的是，通过采用的一致性模型，用户尝试通过禁用不安全优化减少错误时，精确地增加错误的可能性。 因此一致性模型可能会严重同时同时提供不能保证提高精度的降低效率。 到严重数字程序员提供的这看起来非常好过不，是，该模型不通常畅行无阻的主要原因。

从版本 8.0 (Visual C++® 2005)，Microsoft c + + 编译器提供了多更好的选择。 它使程序员可以选择三种常规的浮点模式之一： fp: precise，/fp: fast 和 fp： 严格。

- 下 fp： 非常精确的仅安全执行优化浮点代码上，在与不同 **/Op**，以最高的实际精度一致地执行中间计算。
- /fp: fast 模式放松了浮点规则，以允许为代价是牺牲准确性更高性能优化。
- fp： 严格模式下提供的 fp 所有常规的正确性： 同时启用 fp 异常语义并防止非法转换出现 FPU 环境更改 （例如更改到寄存器的精度、 舍入方向等） 的情况下精确。

可通过命令行开关或编译器杂注; 独立控制的浮点异常语义默认情况下，浮点异常语义处于禁用状态下 fp： 精确和 fp 下已启用： 严格。 编译器还提供了对 FPU 环境敏感度和某些浮点特定优化，如缩略形式的控制。 此简单直接的模型为开发人员提供了大量的控制而无需过多的编译器开关的负担或不良的副作用的前景的浮点代码的编译。

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Fp： 精确模式下的浮点语义

默认的浮点语义模式是 fp： 精确。 选择此模式，编译器严格符合一组安全规则时优化浮点运算。 这些规则允许编译器的浮点计算准确性的同时生成高效的机器代码。 若要促进快速的生产程序，fp： 精确模型禁用浮点异常语义 （尽管它们可以显式启用）。 Microsoft 已选择 fp： 因为这会创建快速、 准确程序作为默认浮点模式精确。

若要显式请求 fp： 精确模式下使用命令行编译器，使用[/fp： 精确](fp-specify-floating-point-behavior.md)切换：

> cl /fp： 精确 source.cpp

这会指示编译器使用 fp： 为 source.cpp 文件生成代码时的精确语义。 Fp： 精确的模型还可以调用函数的函数使用[float_control 编译器杂注](#the-float-control-pragma)。

下 fp： 精确模式下，编译器永远不会执行任何干扰的浮点计算准确性的优化。 编译器将始终向上舍入正确分配在、 类型强制转换和函数调用，并中间舍入不一致地执行同样的准确度在 FPU 注册。 默认情况下启用的缩写，如安全优化。 默认情况下禁用异常语义和 FPU 环境敏感度。

|fp： 精确的语义|说明|
|-|-|
|舍入语义|在分配，显式舍入类型强制转换和函数调用。 中间表达式将在注册精度上进行评估。|
|代数转换|严格遵守非关联、 非分布式浮点代数，除非可以转换始终保证对生成相同的结果。|
|缩写|默认情况下允许。 有关详细信息，请参阅部分[fp_contract 杂注](#the-fp-contract-pragma)。|
|浮点计算顺序|前提是最终结果，不会改变编译器可能对浮点表达式的计算重新排序。|
|FPU 环境访问权限|默认情况下禁用。 有关详细信息，请参阅部分[fenv_access 杂注](#the-fenv-access-pragma)。 假定为默认的精度和舍入模式。|
|浮点异常语义|默认情况下禁用。 有关详细信息，请参阅[/fp： 除](fp-specify-floating-point-behavior.md)。|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>舍入为下 fp 浮点表达式的语义： 精确

Fp： 精确模型始终执行以最高的实际精度，仅在特定时间点在表达式计算中显式舍入的中间计算。 舍入到用户指定的精度始终发生在四个位置: （a） 时进行分配，（b） 执行类型强制转换时，（c） 时的浮点值作为参数传递到函数和 （d） 时返回的浮点值函数。 在注册精度始终执行中间的计算，因为中间结果的准确性与平台相关 (但精度始终是至少与指定的用户为准确精度)。

请考虑下面的代码中的赋值表达式。 在右侧的表达式的赋值运算符 = 将计算以注册精度和则显式舍入到的类型赋值的左侧。

```cpp
float a, b, c, d;
double x;
...
x = a*b + c*d;
```

计算方式为

```cpp
float a, b, c, d;
double x;
...
register tmp1 = a*b;
register tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

若要显式将一个中间结果舍入，引入类型强制转换。 例如，如果前面的代码修改通过添加显式类型转换，中间表达式 (c * d) 将舍入到的类型强制转换的类型。

```cpp
float a, b, c, d;
double x;
// . . .
x = a*b + (float)(c*d);
```

计算方式为

```cpp
float a, b, c, d;
double x;
// . . .
register tmp1 = a*b;
float tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

此舍入方法的隐含意义是，一些看似等效转换实际上并没有完全相同的语义。 例如，以下转换将拆分为两个赋值表达式的单个赋值表达式。

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

这些编码不具有等效语义，因为第二个编码每个引入了其他赋值运算，并因此其他舍入点。

当函数返回浮点值时，该值将舍入到函数的类型。 当浮点值作为参数传递给函数时，值将舍入到参数的类型。 例如：

```cpp
float sumsqr(float a, float b)
{
   return a*a + b*b;
}
```

计算方式为

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

计算方式为

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
|x86|中间表达式上的默认 53 位精度计算出使用 16 位指数由提供的扩展范围。 当这些 53:16 值"溢出"到内存 （如函数调用期间可能发生） 时，扩展指数范围将被提取到 11 位。 也就是说，溢出的值转换为仅一个 11 位指数与标准的双精度格式。<br/>用户可能会切换到扩展的 64 位精度，用于通过更改浮点控制字使用中间舍入`_controlfp`并启用 FPU 环境访问 (请参阅[fenv_access 杂注](#the-fenv-access-pragma))。 但是，当扩展的精度寄存器的值将溢出到内存中，中间结果将仍舍入为双精度。<br/>此特定的语义可能会发生更改。|
|amd64|在 amd64 FP 语义是其他平台的稍有不同。 出于性能原因，中间操作以提供给最大精度而不是在可用的提供给最大精度的其中一个操作数的计算。  若要强制将使用的更广泛的精度比操作数进行计算的计算，用户需要引入上至少一个子表达式中操作数的强制转换操作。<br/>此特定的语义可能会发生更改。|

### <a name="algebraic-transformations-under-fpprecise"></a>代数转换下 fp： 精确

当 fp： 启用精确模式下，编译器将永远不会执行代数转换*除非最终结果是已证实相同*。 众多实数算术的熟悉带来了代数规则始终不包含有关浮点运算。 例如，以下表达式是等效的实数，但不必对浮点数。

|窗体|描述|
|-|-|
|`(a+b)+c = a+(b+c)`|添加关联规则|
|`(a*b)*c = a*(b*c)`|表示乘法的关联规则|
|`a*(b+c) = a*b + b*c`|乘法通过加法的分布|
|`(a+b)(a-b) = a*a-b*b`|代数分解|
|`a/b = a*(1/b)`|除数乘法逆元|
|`a*1.0 = a`|乘法恒等元|

如下图所示在简介的示例中使用函数`KahanSum`，编译器可能很想要执行各种带来了代数转换以便生成要快很多程序。 优化依赖于此类带来了代数转换几乎始终是不正确的尽管存在一些情况下它们是完全安全。 例如，最好有时替换除数*常量*常量的乘法逆通过执行乘法运算的值：

```cpp
const double four = 4.0;
double a, b;
...

a = b/four;
```

可能会转换为

```cpp
const double four = 4.0;
const double tmp0 = 1/4.0;
double a, b;
...
a = b*tmp0;
```

这是安全的转换，因为优化器可以在编译时确定 x / 4.0 = = x*(1/4.0) 所有的 x，其中包括无穷大和 NaN 的浮点值。 通过使用乘法取代除法运算，编译器可以节省一些循环 — 尤其是在 FPUs 不直接实现部门，但需要编译器生成的倒数近似值组合并乘加上有关说明。 编译器可能会执行下 fp 这样的优化： 精确仅当替换乘法产生完全相同的结果，作为该除法运算。 编译器还可以执行简单转换下 fp： 精确，提供的结果是相同的。 这些问题包括：

|窗体|描述
|-|-|
|`(a+b) == (b+a)`|添加可交换性规则|
|`(a*b) == (b*a)`|表示乘法的可交换性规则|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|1.0 的乘法|
|`x/1.0*y == x*y/1.0 == x*y`|1.0 的除法|
|`2.0*x == x+x`|乘法运算 2.0|

### <a name="contractions-under-fpprecise"></a>缩写下 fp： 精确

许多现代浮点单元的一项主要体系结构功能是能够执行乘法跟作为单个操作随任何中间舍入误差的补充。 例如，Intel 的 Itanium 体系结构提供有关将合并这些三元操作的说明 (*b + c)，(* b 到 c) 和 (c a * b)，为单个浮点指令 (fma、 fms 和 fnma 分别)。 这些单指令速度较快比单独执行相乘，添加说明，并且更加准确由于产品没有中间舍入。 这种优化可以显著加快包含几个交错 multiply 函数并添加操作。 例如，考虑以下算法计算两个 n 维向量的点积。

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

可以执行此计算一系列的乘加说明的窗体 p = p + x [i] * y [i]。

缩写优化可以独立地控制使用`fp_contract`编译器杂注。 默认情况下，fp： 精确的模型可以为缩写，因为它们提高准确性和速度。 下 fp： 非常精确的编译器将永远不会合同具有显式舍入的表达式。
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

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>Fp 下的浮点表达式求值顺序： 精确

保留的浮点表达式计算顺序的优化始终是安全的因此在 fp 允许： 精确模式。 请考虑以下函数计算两个单精度中的 n 维向量的点积。 下面的第一个代码块是原始函数为其可能会有一位程序员，编码后跟相同的功能部分的循环展开优化后。

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

这种优化的主要优点是它最多 75%的减少的条件的循环分支数量。 此外，通过增加的循环主体中的操作数量，编译器可能会有更多的机会来进一步优化。 例如，某些 FPUs 可能能够执行乘加在 p + = x [i] * y [i] 时同时提取 x [i + 1] 的值和 y [i + 1] 在下一步中使用。 这种优化是完全安全的浮点计算的因为它保留操作的顺序。

通常很有好处的编译器对整个操作重新排序以生成更快的代码。 考虑下列代码：

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

C + + 的语义规则指示该程序应生成的结果，如同它首先计算 x，则 y 和 z 最后。 假设编译器具有只需四个可用的浮点寄存器。 如果强制编译器来计算 x、 y 和 z 顺序情况下，它可以选择生成具有以下语义的代码：

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

有多个清楚地冗余操作是此编码。 如果编译器严格遵循 c + + 语义规则，此排序必须，因为该程序可能会访问中间 FPU 环境每次分配。 但是，fp 的默认设置： 精确允许编译器以优化，就好像该程序不会访问该环境，使其能够重新排列这些表达式。 这样，它将删除了剩余的计算的三个值按相反的顺序，按如下所示：

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

此编码是明显更好，具有降低的 fp 指令数几乎 40%。 结果为 x，y 和 z 是相同的与之前一样，但计算开销更少。

下 fp： 非常精确的编译器可能还*隔行扫描*以便生成使代码更快的公用子表达式。 例如，可能会按如下所示编写代码来计算的二次方程的根：

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

尽管两个表达式仅通过单个操作不同，程序员可能编写这种方式，以保证，将在实际的最高精度计算每个根值。 下 fp： 非常精确的编译器可以自由地隔行扫描 root0 和 root1 删除而不会丢失精度的公用子表达式的计算。 例如，以下已移除冗余的几个步骤时生成完全相同的答案。

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

其他优化可能会尝试移动某些独立表达式的计算。 请考虑下面的算法，其中包含循环主体中的条件分支。

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

编译器可能检测到的表达式的值 (abs(d) > 1) 是在循环主体中固定不变。 这使编译器能够"提升"if 外部循环主体，将上面的代码转换成以下语句：

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

在转换后，不再条件分支中的循环主体，从而极大地提高了循环的整体性能。 这种优化是完全安全的因为是表达式的计算 (abs(d) > 1.0) 是独立于其他表达式。

出现的情况下 FPU 环境访问或浮点异常，因为它们会更改语义的流程被 contraindicated 这些类型的优化。 此类优化都仅位于 fp： 精确模式下因为默认情况下禁用 FPU 环境访问权限和浮点异常语义。 访问 FPU 环境的函数可以通过使用显式禁用此类优化`fenv_access`编译器杂注。 同样，使用浮点异常的函数应使用`float_control(except ... )`编译器杂注 (或使用 **/fp： 除**命令行开关)。

总之，fp： 精确模式下允许编译器对浮点表达式的计算进行重新排序，前提是最终结果，不会更改和结果不依赖 FPU 环境或浮点异常。

### <a name="fpu-environment-access-under-fpprecise"></a>FPU 环境访问下 fp： 精确

当 fp： 启用精确模式下，编译器将假定程序不访问或更改 FPU 环境。 如前面所述，此假设使编译器能够重新排序或移动浮点运算，以提高效率下 fp： 精确。

某些程序可能会更改使用的浮点舍入方向`_controlfp`函数。 例如，某些程序计算上限和通过执行相同计算两次，较低错误边界上的算术运算先时向负无穷舍入，然后，而向正无穷舍入。 由于 FPU 提供方便地控制舍入，也可以选择一名程序员通过更改 FPU 环境更改舍入模式。 以下代码计算确切错误通过更改 FPU 环境浮点乘法运算的绑定。

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

下 fp： 非常精确的编译器始终假定默认 FPU 环境，因此，优化器可以自由地忽略对调用`_controlfp`并减少到 cUpper 的上述分配 = cLower = * b; 这显然会产生不正确的结果。 若要防止这种优化，通过使用启用 FPU 环境访问`fenv_access`编译器杂注。

其他程序可能会尝试通过检查 FPU 的状态字检测某些浮点错误。 例如，下面的代码检查被零除和不精确条件

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

下 fp： 精确，重新排列表达式计算优化可能会更改出现某些错误的点。 程序可访问的状态字应使用启用 FPU 环境访问`fenv_access`编译器杂注。

有关详细信息，请参阅部分[fenv_access 杂注](#the-fenv-access-pragma)。

### <a name="floating-point-exception-semantics-under-fpprecise"></a>浮点异常语义下 fp： 精确

默认情况下，浮点异常语义处于禁用状态下 fp： 精确。 大多数 c + + 程序员更喜欢而无需使用系统或 c + + 异常处理浮点异常情况。 此外，如前面所述，禁用浮点异常语义允许编译器更大的灵活性时优化浮点运算。 可以使用两种 **/fp： 除外**切换或`float_control`杂注来使用 fp 时启用浮点异常语义： 精确的模型。

有关详细信息，请参阅部分[启用浮点异常语义](#enabling-floating-point-exception-semantics)。

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>浮点语义 /fp: fast 模式

启用 /fp: fast 模式后，编译器会该 fp 放松规则： 时优化浮点运算的精确使用。 此模式下是允许编译器以进一步优化浮点代码的速度，代价是浮点准确性和正确性。 不要依赖于高度精确的浮点计算的程序可能会遇到大量的速度提高通过启用 /fp: fast 模式。

使用启用 /fp: fast 浮点模式[/fp: fast](fp-specify-floating-point-behavior.md)命令行编译器开关，如下所示：

> cl /fp: fast source.cpp

下面的示例指示编译器为 source.cpp 文件生成代码时使用 /fp: fast 语义。 /Fp: fast 模型还可以调用函数的函数使用`float_control`编译器杂注。

有关详细信息，请参阅部分[float_control 杂注](#the-float-control-pragma)。

在 /fp: fast 模式下，编译器可能执行更改的浮点计算准确性的优化。 编译器不在分配正确 round、 类型强制转换或函数调用，以及中间舍入不始终会执行。 始终启用浮点特定优化，如的缩写。 浮点异常语义和 FPU 环境敏感度是禁用并且不可用。

|/fp: fast 语义|说明
|-|-|
|舍入语义|在分配，显式舍入类型强制转换和函数调用可能会被忽略。<br/>在早于注册根据性能要求的精度，中间表达式可能会舍入。|
|代数转换|编译器可能会转换表达式根据其实数关联、 分布式代数;这些转换不保证准确性或正确。|
|缩写|始终处于启用状态;杂注不能禁用 `fp_contract`|
|浮点计算顺序|即使在此类更改可能会更改的最终结果时，编译器可能对浮点表达式的计算重新排序。|
|FPU 环境访问权限|禁用。 不可用|
|浮点异常语义|禁用。 不可用|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>舍入为下 /fp: fast 的浮点表达式的语义

与不同的 fp： 精确的模型，/fp: fast 模型执行中间计算在最方便的精度。 在分配，舍入类型强制转换和函数调用并不总是会。 例如，下面的第一个函数引入了三个单精度变量 (`C`，`Y`和`T`)。 编译器可以选择注册局部变量这些变量，有效的类型提升`C`，`Y`和`T`为双精度。

原始函数：

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

变量以内：

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

在此示例中，/fp: fast 具有 subverted 原始函数的意图。 最后一个优化结果，保存在变量中`sum`，可能会相当 perturbed 从正确的结果。

在 /fp: fast，编译器将通常尝试至少维护的源代码所指定的精度。 但是，在某些情况下，编译器可能会选择执行中间表达式*降低精度*比指定的源代码中。 例如，下面的第一个代码块调用平方根的函数的双精度版本。 在下 /fp: fast，在某些情况下，例如当结果和函数的操作数显式强制转换为单精度编译器可能会选择要为双精度的调用替换为`sqrt`通过单精度调用`sqrtf`函数。 因为强制转换，请确保传入值`sqrt`和即将推出的值将舍入为单精度，这只会更改的舍入的位置。 如果传入 sqrt 的值为双精度值，并且编译器执行此转换，多达下半部分的精度位数可能错误。

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

已优化的函数

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

尽管不太准确，这种优化可能尤其有用，以提供单精度，函数的内部版本，例如处理器为目标时`sqrt`。 只需精确时编译器将使用这种优化与平台和上下文相关。

此外，还有可能在任何可用于编译器的精度级别上执行的中间计算的精度不保证的一致性。 尽管编译器将尝试至少维护的代码指定的精度级别，/fp: fast 允许向下转换将中间计算优化器以生成更快或更小的计算机代码。 例如，编译器进一步可能优化从上面的代码要舍入为单精度中间的乘法运算的一些。

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

使用较低精度浮点单元，例如 SSE2，若要执行的中间计算的则可能会导致这种额外的舍入。 /Fp: fast 舍入的准确性因此与平台相关;适合一个处理器编译的代码可能不一定适合另一个处理器。 它由用户来确定速度利准确性的任何问题。

如果 /fp: fast 优化是指特定功能的特别容易出现问题，浮点模式可以本地切换到 fp： 精确使用`float_control`编译器杂注。

### <a name="algebraic-transformations-under-fpfast"></a>/Fp: fast 下带来了代数转换

/Fp: fast 模式使编译器能够执行某些操作，不安全带来了代数转换为浮动点表达式。 例如，以下不安全的优化措施 /fp: fast 下。

||||
|-|-|-|
|原始代码|步骤 1|步骤 2
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

在步骤 1 中，编译器将观察的`z = y – a – b`也始终等于零。 尽管从技术上讲无效观察值，它是在 /fp: fast 允许。 然后，编译器将传播到每个后续使用的变量 z 的常量值零。 在步骤 2 中，编译器进一步通过观察，来优化`x - 0 == x`， `x * 0 == 0`，等等。同样，即使这些观测值不是完全有效，它们所允许的 /fp: fast。 优化的代码现在速度更快，但也可能是相当不太准确或甚至不正确。

任何以下 （不安全） 带来了代数规则可能启用 /fp: fast 模式时采用优化器中：

|||
|-|-|
|窗体|描述|
|`(a + b) + c = a + (b + c)`|添加关联规则|
|`(a * b) * c = a * (b * c)`|表示乘法的关联规则|
|`a * (b + c) = a * b + b * c`|乘法通过加法的分布|
|`(a + b)(a - b) = a * a - b * b`|代数分解|
|`a / b = a * (1 / b)`|除数乘法逆元|
|`a * 1.0 = a, a / 1.0 = a`|乘法恒等元|
|`a ± 0.0 = a, 0.0 - a = -a`|累加性标识|
|`a / a = 1.0, a - a = 0.0`|取消|

如果 /fp: fast 优化特定函数特别容易出现问题，浮点模式可以本地切换到 fp： 精确使用`float_control`编译器杂注。

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>/Fp: fast 下的浮点表达式求值顺序

与不同的 fp: precise，/fp: fast 使编译器能够重新排序以生成更快的代码的浮点运算。 因此，/fp: fast 下的一些优化可能不保留顺序的表达式。 例如，考虑以下函数计算两个 n 维向量的点积。

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

在 /fp: fast，则优化器可能会执行的标量降低`dotProduct`函数有效地转换函数，如下所示：

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

在函数的优化版本四个单独的产品就是同时执行，然后加在一起。 这种优化可以提高计算速度`dotProduct`通过得那么多的四个具体取决于目标处理器，但最终结果的因素可能会因此并使其不准确。 如果此类优化都为单个函数或翻译单元特别容易出现问题，浮点模式可以本地切换到 fp： 精确使用`float_control`编译器杂注。

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>Fp： 严格模式下的浮点语义

当 fp： 启用严格模式下，编译器遵循以统一的规则该 fp： 时优化浮点运算的精确使用。 此模式还启用浮点异常语义和 FPU 环境的敏感度，并禁用某些优化，如的缩写。 是操作的最严格模式。

Fp： 使用启用严格的浮点模式[/fp: strict](fp-specify-floating-point-behavior.md)命令行编译器开关，如下所示：

> cl /fp: strict source.cpp

下面的示例指示编译器使用 fp： 严格的语义为 source.cpp 文件生成代码时。 Fp： 严格模式也可调用函数的函数使用`float_control`编译器杂注。

有关详细信息，请参阅部分[float_control 杂注](#the-float-control-pragma)。

下 fp： 严格模式下，编译器永远不会执行任何干扰的浮点计算准确性的优化。 编译器将始终向上舍入正确分配在、 类型强制转换和函数调用，并中间舍入不一致地执行同样的准确度在 FPU 注册。 默认情况下启用浮点异常语义和 FPU 环境敏感度。 某些优化，如的缩写，已禁用，因为编译器无法保证在每个用例的正确性。

|fp： 严格的语义|说明|
|-|-|
|舍入语义|在分配，显式舍入类型强制转换和函数调用<br/>中间表达式将在注册精度上进行评估。<br/>Fp 与相同： 精确|
|代数转换|严格遵守非关联、 非分布式浮点代数，除非可以转换始终保证对生成相同的结果。<br/>Fp 与相同： 精确|
|缩写|始终处于禁用状态|
|浮点计算顺序|编译器将不重新排序浮点表达式的计算|
|FPU 环境访问权限|始终处于启用状态。|
|浮点异常语义|默认情况下启用。|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>浮点异常语义下 fp： 严格

默认情况下，启用浮点异常语义下 fp： 严格模式。 若要禁用这些语义，请使用 **/fp： 除-** 切换或引入`float_control(except, off)`杂注。

有关详细信息，请参阅部分[启用浮点异常语义](#enabling-floating-point-exception-semantics)并[float_control 杂注](#the-float-control-pragma)。

## <a name="the-fenvaccess-pragma"></a>Fenv_access 杂注

用法：

```cpp
#pragma fenv_access( [ on  | off ] )
```

[Fenv_access](../../preprocessor/fenv-access.md)杂注允许编译器以使 FPU 标记测试和 FPU 模式更改可能会破坏某些优化。 时的状态`fenv_access`处于禁用状态，则编译器可以假定默认 FPU 模式才有效和 FPU 标志进行测试。 默认情况下，禁用 fp 环境访问权限： 精确模式下，尽管它可能会显式启用使用此杂注。 下 fp： 严格，`fenv_access`始终处于启用状态，并且无法禁用。 在 /fp: fast，`fenv_access`始终处于禁用状态，且无法启用。

Fp 中所述： 精确部分中，某些编程人员可能会更改浮点舍入方向使用`_controlfp`函数。 例如，若要计算的算术运算的上限和下限误差界限，某些程序执行相同计算两次，第一次时向负无穷舍入然后时向正无穷舍入。 由于 FPU 提供方便地控制舍入，也可以选择一名程序员通过更改 FPU 环境更改舍入模式。 以下代码计算确切错误通过更改 FPU 环境浮点乘法运算的绑定。

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

禁用时，`fenv_access`杂注，编译器将假定默认 FPU 环境; 因此，优化器是可以忽略对调用`_controlfp`，并减少到的上述分配`cUpper = cLower = a*b`。 如果启用，但是，`fenv_access`可防止这种优化。

程序还可以查看 FPU 状态字来检测某些浮点错误。 例如，下面的代码检查被零除和不精确条件

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

当`fenv_access`是禁用，编译器可能会重新排列的浮点表达式，因此可能会破坏 FPU 状态检查的执行顺序。 启用`fenv_access`可防止这种优化。

## <a name="the-fpcontract-pragma"></a>Fp_contract 杂注

用法：

```cpp
#pragma fp_contract( [ on | off ] )
```

Fp 中所述： 精确部分中，缩写式是很多现代浮点单元的基本体系结构功能。 缩写提供执行乘法跟添加作为单个操作随任何中间舍入误差的能力。 这些单指令速度较快比单独执行相乘，添加说明，并且更加准确由于产品没有中间舍入。 收缩的操作可以计算的值`(a*b+c)`好像这两项操作已计算到无限精度，则舍入到最近的浮点数。 这种优化可以显著加快包含几个交错 multiply 函数并添加操作。 例如，考虑以下算法计算两个 n 维向量的点积。

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

可以执行此计算一系列的乘加窗体的说明`p = p + x[i]*y[i]`。

[Fp_contract](../../preprocessor/fp-contract.md)杂注指定是否可以收缩浮点表达式。 默认情况下，fp： 精确模式下可以为缩写，因为它们提高准确性和速度。 /Fp: fast 模式始终启用的缩写。 但是，这是因为缩写可以破坏显式检测错误条件，`fp_contract`杂注始终处于禁用状态下 fp： 严格模式。 可能的表达式的示例收缩时`fp_contract`启用杂注：

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

**/Fp： 精确**， **/fp: fast**， **/fp: strict**并 **/fp： 除**开关控制文件的文件中的浮点语义基数。 [Float_control](../../preprocessor/float-control.md)杂注提供了此类控制在函数的函数的基础上。

用法：

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

杂注`float_control(push)`和`float_control(pop)`分别推送和弹出浮点模式以及到堆栈上的异常选项的当前状态。 请注意，状态`fenv_access`并`fp_contract`杂注不受`pragma float_control(push/pop)`。

调用杂注`float_control(precise, on)`将启用和`float_control(precise, off)`将禁用精确模式下的语义。 同样，杂注`float_control(except, on)`将启用和`float_control(except, off)`将禁用异常语义。 精确的语义也已启用时，才会启用异常语义。 时可选`push`存在，则参数的状态`float_control`选项推送之前更改语义。

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>在函数的函数的基础上设置的浮点语义模式

命令行开关实际上是设置四个其他浮点杂注的简写。 若要显式选择特定的浮点语义模式，在函数的函数的基础上，选择每个四个浮点选项杂注下表中所述：

||||||
|-|-|-|-|-|
||float_control(precise)|float_control(except)|fp_contract|fenv_access|
|/fp:strict|on|on|关闭|on|
|/fp:strict /fp:except-|on|关闭|关闭|on|
|/fp:precise|on|关闭|on|关闭|
|/fp:precise /fp:except|on|on|on|关闭|
|/fp:fast|关闭|关闭|on|关闭|

例如，以下显式启用 /fp: fast 语义。

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> 必须关闭"精确"的语义之前关闭异常语义。

## <a name="enabling-floating-point-exception-semantics"></a>启用浮点异常语义

某些异常的浮点条件，如除以零，可能会导致 FPU 发出信号的硬件异常。 默认情况下禁用浮点异常。 通过修改 FPU 控制字与启用了浮点异常`_controlfp`函数。 例如，下面的代码可让被零除的浮点异常：

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

启用被零除异常后，任何使用分母等于零的除法运算会导致 FPU 异常信号。

若要还原为默认模式 FPU 控制字，请调用`_controlfp(_CW_DEFAULT, ~0)`。

启用浮点异常具有语义 **/fp： 除**标志不是与启用浮点异常相同。 当启用浮点异常语义时，编译器必须考虑任何浮点运算可能会引发异常的可能性。 由于 FPU 是一个单独的处理器单元，可以同时其他单元的说明执行 FPU 上执行的说明。

启用浮点异常后，FPU 将暂停执行有问题的指令，然后通过设置 FPU 状态字信号异常情况。 当在 CPU 达到下一步浮点指令时，它将首先检查任何挂起的 FPU 异常。 如果没有挂起的异常，处理器将捕获它通过调用由操作系统提供的异常处理程序。 这意味着，当浮点运算遇到异常情况时，相应的异常不会检测到直到执行下一步浮点运算。 例如，下面的代码捕获被零除异常：

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

如果在表达式中出现被零除情况 = b/c，FPU 不会陷阱/引发表达式 2.0 中的下一步浮点操作直到异常 * b。 这会导致以下输出：

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

Printf 对应于输出的第一行应尚未达到;它已达到因为直到执行达到 2.0 不引发的浮点异常引起的表达式 b/c * b。 若要引发的异常之后执行 b/c，则编译器必须引入"等待"指令：

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

此"等待"指令强制与 FPU 的状态同步，并处理任何挂起的异常的处理器。 编译器将仅生成这些"等待"的说明时启用浮点语义。 当这些语义都被禁用，因为默认情况下时，程序使用浮点异常时可能遇到的同步错误，类似于更高版本。

如果启用了浮点语义，编译器不会仅引入"等待"说明，它还会阻止编译器从非法优化浮点代码出现可能的异常的情况下。 这包括更改引发异常的点的任何转换。 由于这些因素，启用浮点语义可能会显著降低所生成的机器代码，这样会降低应用程序的性能的效率。

Fp 在默认情况下启用浮点异常语义： 严格模式。 若要启用这些语义在 fp： 精确模式下，添加 **/fp： 除**切换到命令行编译器。 浮点异常语义也可以启用和禁用函数的函数使用`float_control`杂注。

### <a name="floating-point-exceptions-as-c-exceptions"></a>浮点异常作为 c + + 异常

所有硬件例外情况之外，浮点异常本质上不会导致 c + + 异常，但改为触发结构化的异常。 若要将结构化的浮点异常映射到 c + + 异常，用户可以引入的自定义 SEH 异常转换器。 首先，引入了与每个浮点异常相对应的 c + + 异常：

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

然后，引入了一个将检测浮点 SEH 异常并引发相应的 c + + 异常的转换函数。 若要使用此函数，设置当前进程线程使用结构化异常处理程序转换器[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)从运行时库函数。

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

初始化此映射，浮点异常的行为就好像它们是 c + + 异常。 例如：

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

[关于浮点算术，每个计算机科学家应知道什么](http://pages.cs.wisc.edu/~david/courses/cs552/S12/handouts/goldberg-floating-point.pdf)由 David 翰伟。

## <a name="see-also"></a>请参阅

[优化代码](../optimizing-your-code.md)<br/>
