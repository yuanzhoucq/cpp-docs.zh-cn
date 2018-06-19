---
title: '&lt;random&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 08/24/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <random>
dev_langs:
- C++
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdfae58c03d18638ad44f844909d585b41d710cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862905"
---
# <a name="ltrandomgt"></a>&lt;random&gt;

定义随机数生成设备，从而允许创建均匀分布的随机数。

## <a name="syntax"></a>语法

```cpp
#include <random>
```

## <a name="summary"></a>总结

*随机数生成器*是指可产生伪随机值序列的对象。 可产生在指定范围内均匀分布的值的生成器称为*均匀随机数生成器* (URNG)。 如果模板类具有某些共同的特点，则将旨在充当 URNG 的模板类称为*引擎*（将在本文后面对此进行讨论）。 通过将 URNG 作为自变量传递到分布的 `operator()`，URNG 可以（通常也会）和*分布*一起使用，从而产生以该分布定义的方式分布的值。

这些链接将跳转到本文的主要部分：

- [示例](#code)

- [分类列表](#listing)

- [引擎和分布](#engdist)

- [备注](#comments)

### <a name="quick-tips"></a>快速提示

下面是一些提示使用时，需要注意\<随机 >:

- 在大多数情况下，URNG 将产生必须由分布形成的原始位。 （一个值得注意的例外是 [std::shuffle()](../standard-library/algorithm-functions.md#shuffle)，因为它直接使用 URNG。）

- 无法同时安全地调用 URNG 或分布的单一实例化，因为运行 URNG 或分布是修改操作。 有关详细信息，请参阅 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)。

- 提供了几个引擎的[预定义 typedef](#typedefs)；如果正在使用引擎，则这是创建 URNG 的首选方法。

- 对于大多数应用程序而言，最有用的配对是 `mt19937` 引擎和 `uniform_int_distribution`，如本文后面的[代码示例](#code)中所示。

有许多选项可供选择在\<随机 > 标头，并且其中任何优于过时的 C 运行时函数`rand()`。 有关问题信息`rand()`以及如何\<随机 > 处理这些不足，请参阅[此视频](http://go.microsoft.com/fwlink/p/?linkid=397615)。

## <a name="code"></a>示例

以下代码示例显示如何生成一些随机数字，本例中有 5 个是使用生成器用非确定性种子生成的。

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
                        // replace the call to rd() with a
                        // constant value to get repeatable
                        // results.

    for (int i = 0; i < 5; ++i) {
        cout << gen() << " "; // print the raw output of the generator.
    }
    cout << endl;
}
```

```Output
2430338871 3531691818 2723770500 3252414483 3632920437
```

虽然这些是高质量随机数字并且此程序每次运行时生成的数字都不一样，但它们不一定在有用范围之内。 若要控制范围，应使用均匀分布，如以下代码所示：

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
    uniform_int_distribution<> dist(1,6); // distribute results between 1 and 6 inclusive.

    for (int i = 0; i < 5; ++i) {
        cout << dist(gen) << " "; // pass the generator to the distribution.
    }
    cout << endl;
}
```

```Output
5 1 6 1 2
```

下一个代码示例显示更为实际的一组用例，即使用均匀分布的随机数生成器随机排列矢量内容和数组内容。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <array>
#include <iostream>
#include <random>
#include <string>
#include <vector>
#include <functional> // ref()

using namespace std;

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

template <class URNG>
void test(URNG& urng) {

    // Uniform distribution used with a vector
    // Distribution is [-5, 5] inclusive
    uniform_int_distribution<int> dist(-5, 5);
    vector<int> v;

    for (int i = 0; i < 20; ++i) {
        v.push_back(dist(urng));
    }

    cout << "Randomized vector: ";
    print(v);

    // Shuffle an array
    // (Notice that shuffle() takes a URNG, not a distribution)
    array<string, 26> arr = { { "H", "He", "Li", "Be", "B", "C", "N", "O", "F",
        "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca", "Sc",
        "Ti", "V", "Cr", "Mn", "Fe" } };

    shuffle(arr.begin(), arr.end(), urng);

    cout << "Randomized array: ";
    print(arr);
    cout << "--" << endl;
}

int main()
{
    // First run: non-seedable, non-deterministic URNG random_device
    // Slower but crypto-secure and non-repeatable.
    random_device rd;
    cout << "Using random_device URNG:" << endl;
    test(rd);

    // Second run: simple integer seed, repeatable results
    cout << "Using constant-seed mersenne twister URNG:" << endl;
    mt19937 engine1(12345);
    test(engine1);

    // Third run: random_device as a seed, different each run
    // (Desirable for most purposes)
    cout << "Using non-deterministic-seed mersenne twister URNG:" << endl;
    mt19937 engine2(rd());
    test(engine2);

    // Fourth run: "warm-up" sequence as a seed, different each run
    // (Advanced uses, allows more than 32 bits of randomness)
    cout << "Using non-deterministic-seed \"warm-up\" sequence mersenne twister URNG:" << endl;
    array<unsigned int, mt19937::state_size> seed_data;
    generate_n(seed_data.begin(), seed_data.size(), ref(rd));
    seed_seq seq(begin(seed_data), end(seed_data));
    mt19937 engine3(seq);
    test(engine3);
}
```

```Output
Using random_device URNG:
Randomized vector: 5 -4 2 3 0 5 -2 0 4 2 -1 2 -4 -3 1 4 4 1 2 -2
Randomized array: O Li V K C Ti N Mg Ne Sc Cl B Cr Mn Ca Al F P Na Be Si Ar Fe S He H
--
Using constant-seed mersenne twister URNG:
Randomized vector: 3 -1 -5 0 0 5 3 -4 -3 -4 1 -3 0 -3 -2 -4 5 1 -1 -1
Randomized array: Al O Ne Si Na Be C N Cr Mn H V F Sc Mg Fe K Ca S Ti B P Ar Cl Li He
--
Using non-deterministic-seed mersenne twister URNG:
Randomized vector: 5 -4 0 2 1 -2 4 4 -4 0 0 4 -5 4 -5 -1 -3 0 0 3
Randomized array: Si Fe Al Ar Na P B Sc H F Mg Li C Ti He N Mn Be O Ca Cr V K Ne Cl S
--
Using non-deterministic-seed "warm-up" sequence mersenne twister URNG:
Randomized vector: -1 3 -2 4 1 3 0 -5 5 -5 0 0 5 0 -3 3 -4 2 5 0
Randomized array: Si C Sc H Na O S Cr K Li Al Ti Cl B Mn He Fe Ne Be Ar V P Ca N Mg F
--
```

此代码使用测试模板函数演示了两种不同的随机化过程（随机化整数矢量和随机排列索引数据的数组）。 首次调用测试函数时，使用安全加密的、非确定性的、不可设定种子的、不可重复的 URNG `random_device`。 第二次测试运行将 `mersenne_twister_engine` 用作 URNG，以及确定性的 32 位常量种子，这意味着结果是可重复的。 第三次测试运行使用来自 `mersenne_twister_engine` 的 32 位非确定性结果设定 `random_device` 的种子。 第四次测试运行通过使用以 `random_device` 结果填充的[种子序列](../standard-library/seed-seq-class.md)对此进行扩展，这可有效地提供超过 32 位的非确定性随机性（但仍非安全加密的）。 有关详细信息，请继续阅读。

## <a name="listing"></a>分类列表

###  <a name="urngs"></a>均匀随机数生成器

通常根据这些属性来描述 URNG：

1. **周期长度**：重复生成的数字序列所需的迭代数。 越长越好。

2. **性能**：生成数字的速度和所需的内存量。 越小越好。

3. **质量**：生成的序列与真正的随机数的接近程度。 这通常称为“*随机性*”。

以下各节列出均匀随机数生成器 (Urng) 中提供\<随机 > 标头。

####  <a name="rd"></a>非确定性生成器

|||
|-|-|
|[random_device 类](../standard-library/random-device-class.md)|通过使用外部设备，生成非确定性的、安全加密的随机序列。 通常用于为引擎设定种子。 低性能，高质量。 有关更多信息，请参见[备注](#comments)。|

####  <a name="typedefs"></a>具有预定义参数的引擎 Typedef

适用于实例化引擎和引擎适配器。 有关详细信息，请参阅[引擎和分布](#engdist)。

- `default_random_engine`默认引擎。
 `typedef mt19937 default_random_engine;`

- `knuth_b`Knuth 引擎。
 `typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;`

- `minstd_rand0`1988 最小标准引擎（Lewis、Goodman 和 Miller，1969）。
 `typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;`

- `minstd_rand`更新的最小标准引擎 `minstd_rand0`（Park、Miller 和 Stockmeyer，1993）。
 `typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;`

- `mt19937`32 位梅森旋转引擎（Matsumoto 和 Nishimura，1998）。
 `typedef mersenne_twister_engine<unsigned int, 32, 624, 397,      31, 0x9908b0df,      11, 0xffffffff,      7, 0x9d2c5680,      15, 0xefc60000,      18, 1812433253> mt19937;`

- `mt19937_64`64 位梅森旋转引擎（Matsumoto 和 Nishimura，2000）。
 `typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,      31, 0xb5026f5aa96619e9ULL,      29, 0x5555555555555555ULL,      17, 0x71d67fffeda60000ULL,      37, 0xfff7eee000000000ULL,      43, 6364136223846793005ULL> mt19937_64;`

- `ranlux24` 24 位 RANLUX 引擎 （Martin Lüscher 和 Fred James，1994年）。
 `typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;`

- `ranlux24_base`用作 `ranlux24` 的基础。
 `typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

- `ranlux48` 48 位 RANLUX 引擎 （Martin Lüscher 和 Fred James，1994年）。
 `typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;`

- `ranlux48_base`用作 `ranlux48` 的基础。
 `typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

####  <a name="eng"></a>引擎模板

引擎模板将用作独立的 URNG 或传递给[引擎适配器](#engadapt)的基引擎。 通常，使用[预定义引擎 typedef](#typedefs) 实例化这些模板引擎并将其传递给[分布](#distributions)。 有关详细信息，请参阅[引擎和分布](#engdist)部分。

|||
|-|-|
|[linear_congruential_engine 类](../standard-library/linear-congruential-engine-class.md)|通过使用线性同余算法生成随机序列。 最简单且质量最低。|
|[mersenne_twister_engine 类](../standard-library/mersenne-twister-engine-class.md)|通过使用梅森旋转算法生成随机序列。 最复杂且质量最高（random_device 类除外）。 性能非常快。|
|[subtract_with_carry_engine 类](../standard-library/subtract-with-carry-engine-class.md)|通过使用带进位减法算法生成随机序列。 `linear_congruential_engine` 的改进，但是质量和性能都比 `mersenne_twister_engine` 低得多。|

####  <a name="engadapt"></a>引擎适配器模板

引擎适配器是适应其他（基）引擎的模板。 通常，使用[预定义引擎 typedef](#typedefs) 实例化这些模板引擎并将其传递给[分布](#distributions)。 有关详细信息，请参阅[引擎和分布](#engdist)部分。

|||
|-|-|
|[discard_block_engine 类](../standard-library/discard-block-engine-class.md)|通过丢弃由其基引擎返回的值，生成随机序列。|
|[independent_bits_engine 类](../standard-library/independent-bits-engine-class.md)|通过再次从其基引擎返回的值中打包位，生成具有指定位数的随机序列。|
|[shuffle_order_engine 类](../standard-library/shuffle-order-engine-class.md)|通过对从其基引擎中返回的值进行重新排序，生成随机序列。|

[[引擎模板](#eng)]

###  <a name="distributions"></a>随机数分布

下列部分列出了中提供的分布\<随机 > 标头。 这些分布是后处理机制，通常将 URNG 输出用作输入并通过定义的统计概率密度函数分布输出。 有关详细信息，请参阅[引擎和分布](#engdist)部分。

#### <a name="uniform-distributions"></a>均匀分布

|||
|-|-|
|[uniform_int_distribution 类](../standard-library/uniform-int-distribution-class.md)|在闭区间 \[a，b]（包含起始值和结束值）范围内产生均匀整数值分布。|
|[uniform_real_distribution 类](../standard-library/uniform-real-distribution-class.md)|在半开区间 [a，b)（包含起始值，不包含结束值）范围内产生均匀真（浮点）值分布。|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|产生 [0，1)（包含起始值，不包含结束值）上给定精度的真（浮点）值的均匀分布。|

[[随机数分布](#distributions)]

#### <a name="bernoulli-distributions"></a>伯努利分布

|||
|-|-|
|[bernoulli_distribution 类](../standard-library/bernoulli-distribution-class.md)|产生 `bool` 值的伯努利分布。|
|[binomial_distribution 类](../standard-library/binomial-distribution-class.md)|产生整数值的二项式分布。|
|[geometric_distribution 类](../standard-library/geometric-distribution-class.md)|产生整数值的几何分布。|
|[negative_binomial_distribution 类](../standard-library/negative-binomial-distribution-class.md)|产生整数值的负二项式分布。|

[[随机数分布](#distributions)]

#### <a name="normal-distributions"></a>正态分布

|||
|-|-|
|[cauchy_distribution 类](../standard-library/cauchy-distribution-class.md)|产生真（浮点）值的柯西分布。|
|[chi_squared_distribution 类](../standard-library/chi-squared-distribution-class.md)|产生真（浮点）值的卡方分布。|
|[fisher_f_distribution 类](../standard-library/fisher-f-distribution-class.md)|产生的 F-分布 （也称为 Snedecor 的 F 分布或 Fisher Snedecor 分布） 的真 （浮点） 值。|
|[lognormal_distribution 类](../standard-library/lognormal-distribution-class.md)|产生真（浮点）值的对数正态分布。|
|[normal_distribution 类](../standard-library/normal-distribution-class.md)|产生真（浮点）值的正态（高斯）分布。|
|[student_t_distribution 类](../standard-library/student-t-distribution-class.md)|产生真（浮点）值的学生 *t*-分布。|

[[随机数分布](#distributions)]

#### <a name="poisson-distributions"></a>泊松分布

|||
|-|-|
|[exponential_distribution 类](../standard-library/exponential-distribution-class.md)|产生真（浮点）值的指数分布。|
|[extreme_value_distribution 类](../standard-library/extreme-value-distribution-class.md)|产生真（浮点）值的极值分布。|
|[gamma_distribution 类](../standard-library/gamma-distribution-class.md)|产生真（浮点）值的 gamma 分布。|
|[poisson_distribution 类](../standard-library/poisson-distribution-class.md)|产生整数值的泊松分布。|
|[weibull_distribution 类](../standard-library/weibull-distribution-class.md)|产生真（浮点）值的韦伯分布。|

[[随机数分布](#distributions)]

#### <a name="sampling-distributions"></a>示例分布

|||
|-|-|
|[discrete_distribution 类](../standard-library/discrete-distribution-class.md)|产生离散型整数分布。|
|[piecewise_constant_distribution 类](../standard-library/piecewise-constant-distribution-class.md)|产生真（浮点）值的分段常数分布。|
|[piecewise_linear_distribution 类](../standard-library/piecewise-linear-distribution-class.md)|产生真（浮点）值的分段线性分布。|

[[随机数分布](#distributions)]

### <a name="utility-functions"></a>实用函数

本部分列出了中提供的一般实用函数\<随机 > 标头。

|||
|-|-|
|[seed_seq 类](../standard-library/seed-seq-class.md)|生成无偏混合种子序列。 用于避免随机变量流的复制。 在许多 URNG 从引擎中进行实例化时很有用。|

### <a name="operators"></a>运算符

本部分列出了中提供的运算符\<随机 > 标头。

|||
|-|-|
|`operator==`|测试运算符左侧的 URNG 是否等于右侧的引擎。|
|`operator!=`|测试运算符左侧的 URNG 是否不等于右侧的引擎。|
|`operator<<`|将状态信息写入流。|
|`operator>>`|从流中提取状态信息。|

## <a name="engdist"></a>引擎和分布

请参阅有关每个模板类类别中定义的以下部分\<随机 >。 这两个模板类类别都采用类型作为参数，并使用共享模板参数名称来描述允许作为实际参数类型的类型的属性，如下所示：

- `IntType` 指示 `short`、`int`、`long`、`long long`、`unsigned short`、`unsigned int`、`unsigned long` 或 `unsigned long long`。

- `UIntType` 指示 `unsigned short`、`unsigned int`、`unsigned long` 或 `unsigned long long`。

- `RealType` 指示 `float`、`double` 或 `long double`。

### <a name="engines"></a>引擎

[引擎模板](#eng)和[引擎适配器模板](#engadapt)是模板，其参数可自定义创建的生成器。

*引擎*是类或模板类，其实例（生成器）可充当在最小值和最大值之间均匀分布的随机数的源。 通过采用由一些其他的随机数引擎产生的值并对这些值应用某种算法，*引擎适配器*可提供具有不同随机性属性的值的序列。

每个引擎和引擎适配器都具有以下成员：

- `typedef``numeric-type``result_type` 是由生成器的 `operator()` 返回的类型。 在实例化时，`numeric-type` 将作为模板参数传递。

- `result_type operator()` 将返回在 `min()` 和 `max()` 之间均匀分布的值。

- `result_type min()` 将返回由生成器的 `operator()` 返回的最小值。 引擎适配器使用基引擎的 `min()` 结果。

- `result_type max()` 将返回由生成器的 `operator()` 返回的最大值。 当 `result_type` 是整（整数值）型时，`max()` 是可实际返回的最大值（包括其本身）；当 `result_type` 是浮点（真值）型时，`max()` 是大于所有可返回的值的最小值（不包括其本身）。 引擎适配器使用基引擎的 `max()` 结果。

- `void seed(result_type s)` 使用种子值 `s` 为生成器设定种子。 对于引擎，默认参数支持的签名为 `void seed(result_type s = default_seed)`（引擎适配器定义单独的 `void seed()`，请参阅下一小节）。

- `template <class Seq> void seed(Seq& q)` 使用 [seed_seq](../standard-library/seed-seq-class.md)`Seq` 为生成器设定种子。

- 具有类似通过调用 `result_type x` 创建设定了种子的生成器的参数 `seed(x)` 的显式构造函数。

- 具有类似通过调用 `seed_seq& seq` 创建设定了种子的生成器的参数 `seed(seq)` 的显式构造函数。

- `void discard(unsigned long long count)` 有效地调用 `operator()` `count` 次，然后丢弃每个值。

此外，**引擎适配器**还支持这些成员（`Engine` 是引擎适配器的第一个模板参数，用于指定基引擎的类型）：

- 类似从基引擎的默认构造函数初始化生成器的默认构造函数。

- 具有参数 `const Engine& eng` 的显式构造函数。 这是为了支持使用基引擎复制构造。

- 具有参数 `Engine&& eng` 的显式构造函数。 这是为了支持使用基引擎移动构造。

- 使用基引擎的默认种子值初始化生成器的 `void seed()`。

- 返回用于构造生成器的基引擎的 `const Engine& base()` 属性函数。

每个引擎都会保留*状态*，该状态可确定通过对 `operator()` 的后续调用将生成的值的序列。 通过使用 `operator==` 和 `operator!=`，可比较从同一类型的引擎中实例化的两个生成器的状态。 如果两个状态的比较结果相等，则它们将生成同一序列的值。 通过使用生成器的 `operator<<`，可将对象的状态作为 32 位无符号的值的序列保存到流中。 保存状态并不会更改状态。 通过使用 `operator>>`，可将保存的状态读取到从同一类型的引擎实例化的生成器中。

### <a name="distributions"></a>分布

[随机数分布](#distributions)是类或模板类，其实例可将从引擎中获得的均匀分布的随机数的流转换为具有特殊分布的随机数的流。 每个分布都具有以下成员：

- `typedef``numeric-type``result_type` 是由分布的 `operator()` 返回的类型。 在实例化时，`numeric-type` 将作为模板参数传递。

- 通过将 `gen` 用作均匀分布的随机值的源和存储的*分布参数*，`template <class URNG> result_type operator()(URNG& gen)` 可返回根据分布的定义分布的值。

- 通过将 `template <class URNG> result_type operator()(URNG& gen, param_type p)` 用作均匀分布的随机值的源和参数结构 `gen`，`p` 可返回根据分布的定义分布的值。

- `typedef``unspecified-type``param_type` 是选择性地传递给 `operator()` 的参数包，用于代替存储的参数来生成其返回值。

- `const param&` 构造函数从其参数中初始化存储的参数。

- `param_type param() const` 将获取存储的参数。

- `void param(const param_type&)` 将从其参数中设置存储的参数。

- `result_type min()` 将返回由分布的 `operator()` 返回的最小值。

- `result_type max()` 将返回由分布的 `operator()` 返回的最大值。 当 `result_type` 是整（整数值）型时，`max()` 是可实际返回的最大值（包括其本身）；当 `result_type` 是浮点（真值）型时，`max()` 是大于所有可返回的值的最小值（不包括其本身）。

- `void reset()` 将丢弃所有缓存的值，以便下一个对 `operator()` 的调用的结果不取决于在调用之前从引擎获得的任何值。

参数结构是指存储分布所需的所有参数的对象。 它包括：

- `typedef``distribution-type``distribution_type`，是其分布的类型。

- 一个或多个采用与分布构造函数所采用的参数列表相同的构造函数。

- 与分布相同的参数访问函数。

- 相等和不相等比较运算符。

有关详细信息，请参阅本文之前链接的此子主题下面的参考子主题。

## <a name="comments"></a>备注

Visual Studio 中存在两个非常有用的 URNG（`mt19937` 和 `random_device`），如此比较表中所示：

|URNG|快速|安全加密|可设定种子|是确定的|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|是|No|是|是<sup>*</sup>|
|`random_device`|否|是|No|否|

<sup>* 在提供了已知种子的情况下。</sup>

虽然 ISO C++ 标准不需要对 `random_device` 进行安全加密，但是在 Visual Studio 中，会对其实现安全加密。 （术语“安全加密”并不暗示保证，但是表示给定随机化算法提供的熵的最低级别，因此也是可预测级别。 有关详细信息，请参阅 Wikipedia 文章[安全加密的伪随机数生成器](http://go.microsoft.com/fwlink/p/?linkid=398017)。）因为 ISO C++ 标准不需要它，所以其他平台可能会将 `random_device` 实现为简单的伪随机数生成器（非安全加密），并且可能仅适合用作另一个生成器的种子源。 在跨平台代码中使用 `random_device` 时，请查看适用于这些平台的文档。

根据定义，`random_device` 结果是不可复制的，而且副作用是，它的运行速度可能会显著慢于其他 URNG。 虽然你可能希望通过对 `random_device` 的调用来为应用程序设定种子，但大多数不需要进行安全加密的应用程序都使用 `mt19937` 或类似引擎，如[代码示例](#code)中所示。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
