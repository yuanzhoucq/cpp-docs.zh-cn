---
title: extreme_value_distribution 类
ms.date: 11/04/2016
f1_keywords:
- random/std::extreme_value_distribution
- random/std::extreme_value_distribution::reset
- random/std::extreme_value_distribution::a
- random/std::extreme_value_distribution::b
- random/std::extreme_value_distribution::param
- random/std::extreme_value_distribution::min
- random/std::extreme_value_distribution::max
- random/std::extreme_value_distribution::operator()
- random/std::extreme_value_distribution::param_type
- random/std::extreme_value_distribution::param_type::a
- random/std::extreme_value_distribution::param_type::b
- random/std::extreme_value_distribution::param_type::operator==
- random/std::extreme_value_distribution::param_type::operator!=
helpviewer_keywords:
- std::extreme_value_distribution [C++]
- std::extreme_value_distribution [C++], reset
- std::extreme_value_distribution [C++], a
- std::extreme_value_distribution [C++], b
- std::extreme_value_distribution [C++], param
- std::extreme_value_distribution [C++], min
- std::extreme_value_distribution [C++], max
- std::extreme_value_distribution [C++], param_type
- std::extreme_value_distribution [C++], param_type
ms.assetid: a0cd8370-0a54-4e26-9388-8b9678fb57da
ms.openlocfilehash: 865fac1f1452e30b64a0ada9b115186916ff491c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212340"
---
# <a name="extreme_value_distribution-class"></a>extreme_value_distribution 类

生成极值分布。

## <a name="syntax"></a>语法

```cpp
template<class RealType = double>
class extreme_value_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   explicit extreme_value_distribution(result_type a = 0.0, result_type b = 1.0);
   explicit extreme_value_distribution(const param_type& parm);
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

*RealType*\
浮点结果类型，默认为 **`double`** 。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md) 。

*URNG*\
随机数生成器引擎。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md) 。

## <a name="remarks"></a>备注

类模板描述产生用户指定的浮点类型的值的分布， **`double`** 如果未提供任何值，则根据极端值分布来分配值。 下表链接到有关各个成员的文章。

||||
|-|-|-|
|[extreme_value_distribution](#extreme_value_distribution)|`extreme_value_distribution::a`|`extreme_value_distribution::param`|
|`extreme_value_distribution::operator()`|`extreme_value_distribution::b`|[param_type](#param_type)|

属性函数 `a()` 和 `b()` 返回存储的分布参数 `a` 和 `b` 的各自值。

有关分布类及其成员的详细信息，请参阅 [\<random>](../standard-library/random.md) 。

有关极值分布的详细信息，请参阅 Wolfram MathWorld 文章[极值分布](https://go.microsoft.com/fwlink/p/?linkid=401110)。

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

    std::extreme_value_distribution<> distr(a, b);

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
    std::cout << "Enter a floating point value for the \'a\' distribution parameter: ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the \'b\' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter: 0
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
a() == 0.0000000000
b() == 1.0000000000
Distribution for 10 samples:
    1: -0.8813940331
    2: -0.7698972281
    3: 0.2951258007
    4: 0.3110450734
    5: 0.4210546820
    6: 0.4210688771
    7: 0.4598857960
    8: 1.3155194200
    9: 1.5379170046
    10: 2.0568757061
```

## <a name="requirements"></a>要求

**标头：**\<random>

**命名空间:** std

## <a name="extreme_value_distributionextreme_value_distribution"></a><a name="extreme_value_distribution"></a>extreme_value_distribution：： extreme_value_distribution

构造分布。

```cpp
explicit extreme_value_distribution(result_type a_value = 0.0, result_type b_value = 1.0);
explicit extreme_value_distribution(const param_type& parm);
```

### <a name="parameters"></a>参数

*a_value*\
`a` 分布参数。

*b_value*\
`b` 分布参数。

*parm*\
用于构造分布的 `param_type` 结构。

### <a name="remarks"></a>备注

**前提条件：**`0.0 < b`

第一个构造函数将构造一个其存储的 `a` 值保留值 *a_value*，并且其存储的 `b` 值保留值 *b_value* 的对象。

第二个构造函数将构造一个从 parm** 初始化其存储的参数的对象。 通过调用 `param()` 成员函数，可获取和设置当前的现有分发参数。

## <a name="extreme_value_distributionparam_type"></a><a name="param_type"></a>extreme_value_distribution：:p aram_type

存储分布的参数。

```cpp
struct param_type {
   typedef extreme_value_distribution<result_type> distribution_type;
   param_type(result_type a_value = 0.0, result_type b_value = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>参数

*a_value*\
`a` 分布参数。

*b_value*\
`b` 分布参数。

*然后*\
要与它进行比较的 `param_type` 对象。

### <a name="remarks"></a>备注

**前提条件：**`0.0 < b`

在实例化时，可将此结构传递给分布的类构造函数、传递给 `param()` 成员函数以设置现有分布的存储参数，并传递给 `operator()` 以代替存储参数使用。

## <a name="see-also"></a>另请参阅

[\<random>](../standard-library/random.md)
