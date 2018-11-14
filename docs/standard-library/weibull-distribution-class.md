---
title: weibull_distribution 类
ms.date: 11/04/2016
f1_keywords:
- random/std::weibull_distribution
- random/std::weibull_distribution::reset
- random/std::weibull_distribution::a
- random/std::weibull_distribution::b
- random/std::weibull_distribution::param
- random/std::weibull_distribution::min
- random/std::weibull_distribution::max
- random/std::weibull_distribution::operator()
- random/std::weibull_distribution::param_type
- random/std::weibull_distribution::param_type::a
- random/std::weibull_distribution::param_type::b
- random/std::weibull_distribution::param_type::operator==
- random/std::weibull_distribution::param_type::operator!=
helpviewer_keywords:
- std::weibull_distribution [C++]
- std::weibull_distribution [C++], reset
- std::weibull_distribution [C++], a
- std::weibull_distribution [C++], b
- std::weibull_distribution [C++], param
- std::weibull_distribution [C++], min
- std::weibull_distribution [C++], max
- std::weibull_distribution [C++], param_type
- std::weibull_distribution [C++], param_type
ms.assetid: f20b49d3-1b9a-41af-8db4-baf800eaa02b
ms.openlocfilehash: bbcfa23ae84d0a035d4b00d1c154da4b4281be32
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522345"
---
# <a name="weibulldistribution-class"></a>weibull_distribution 类

生成韦伯分布。

## <a name="syntax"></a>语法

```cpp
class weibull_distribution
   {
   public:
    // types
   typedef RealType result_type;
   struct param_type;

    // constructor and reset functions
   explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
   explicit weibull_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
      result_type operator()(URNG& gen);
   template <class URNG>
      result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>参数

*RealType*<br/>
浮点结果类型，默认为**double**。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>备注

此模板类将描述产生用户指定的浮点数的值类型**double**如果未提供任何内容韦伯分布根据分布。 下表链接到有关各个成员的文章。

||||
|-|-|-|
|[weibull_distribution](#weibull_distribution)|`weibull_distribution::a`|`weibull_distribution::param`|
|`weibull_distribution::operator()`|`weibull_distribution::b`|[param_type](#param_type)|

属性函数 `a()` 和 `b()` 分别返回存储的分布参数 a 和 b 的值。

属性成员 `param()` 将设置或返回 `param_type` 存储的分布参数包。

`min()` 和 `max()` 成员函数将分别返回最小可能结果和最大可能结果。

`reset()` 成员函数将放弃所有缓存的值，使下一个对 `operator()` 的调用的结果不取决于在调用之前从引擎获得的任何值。

`operator()` 成员函数将根据 URNG 引擎，从当前参数包或指定参数包返回下一个生成的值。

若要深入了解分布类及其成员，请参阅 [\<random>](../standard-library/random.md)。

有关韦伯分布的详细信息，请参阅 Wolfram MathWorld 文章[韦伯分布](http://mathworld.wolfram.com/WeibullDistribution.html)。

## <a name="example"></a>示例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::weibull_distribution<> distr(a, b);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "a() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.a() << std::endl;
    std::cout << "b() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.b() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double a_dist = 0.0;
    double b_dist = 1;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'a' distribution parameter (must be greater than zero): ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the 'b' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

## <a name="output"></a>输出

首次运行：

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): 1
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
a() == 1.0000000000
b() == 1.0000000000
Distribution for 10 samples:
    1: 0.0936880533
    2: 0.1225944894
    3: 0.6443593183
    4: 0.6551171649
    5: 0.7313457551
    6: 0.7313557977
    7: 0.7590097389
    8: 1.4466885214
    9: 1.6434088411
    10: 2.1201210996
```

第二次运行：

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): .5
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 5.5
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
a() == 0.5000000000
b() == 5.5000000000
Distribution for 10 samples:
    1: 0.0482759823
    2: 0.0826617486
    3: 2.2835941207
    4: 2.3604817485
    5: 2.9417663742
    6: 2.9418471657
    7: 3.1685268104
    8: 11.5109922290
    9: 14.8543594043
    10: 24.7220241239
```

## <a name="requirements"></a>要求

**标头：**\<random>

**命名空间：** std

## <a name="weibull_distribution"></a>weibull_distribution::weibull_distribution

```cpp
explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
explicit weibull_distribution(const param_type& parm);
```

### <a name="parameters"></a>参数

*a*<br/>
`a` 分布参数。

*b*<br/>
`b` 分布参数。

*parm*<br/>
用于构造分布的 `param_type` 结构。

### <a name="remarks"></a>备注

**前置条件：**`0.0 < a` 和 `0.0 < b`

第一个构造函数将构造一个对象，该对象存储的 `a` 值保留值 a，并且存储的 `b` 值保留值 b。

第二个构造函数将构造一个从 parm 初始化其存储的参数的对象。 通过调用 `param()` 成员函数，可获取和设置当前的现有分发参数。

## <a name="param_type"></a>weibull_distribution::param_type

存储分布的参数。

```cpp
struct param_type {
   typedef weibull_distribution<result_type> distribution_type;
   param_type(result_type a = 1.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>参数

*a*<br/>
`a` 分布参数。

*b*<br/>
`b` 分布参数。

*right*<br/>
要与它进行比较的 `param_type` 对象。

### <a name="remarks"></a>备注

**前置条件：**`0.0 < a` 和 `0.0 < b`

在实例化时，可将此结构传递给分布的类构造函数、传递给 `param()` 成员函数以设置现有分布的存储参数，并传递给 `operator()` 以代替存储参数使用。

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)<br/>
