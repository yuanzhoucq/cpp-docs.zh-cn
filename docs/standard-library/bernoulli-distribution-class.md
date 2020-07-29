---
title: bernoulli_distribution 类
ms.date: 11/04/2016
f1_keywords:
- random/std::bernoulli_distribution
- random/std::bernoulli_distribution::reset
- random/std::bernoulli_distribution::p
- random/std::bernoulli_distribution::param
- random/std::bernoulli_distribution::min
- random/std::bernoulli_distribution::max
- random/std::bernoulli_distribution::operator()
- random/std::bernoulli_distribution::param_type
- random/std::bernoulli_distribution::param_type::p
- random/std::bernoulli_distribution::param_type::operator==
- random/std::bernoulli_distribution::param_type::operator!=
helpviewer_keywords:
- std::bernoulli_distribution [C++]
- std::bernoulli_distribution [C++], reset
- std::bernoulli_distribution [C++], p
- std::bernoulli_distribution [C++], param
- std::bernoulli_distribution [C++], min
- std::bernoulli_distribution [C++], max
- std::bernoulli_distribution [C++], param_type
- std::bernoulli_distribution [C++], param_type
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
ms.openlocfilehash: 8b8e433b5ea1283fb60273a2fd21106c65867c0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230254"
---
# <a name="bernoulli_distribution-class"></a>bernoulli_distribution 类

生成伯努利分布。

## <a name="syntax"></a>语法

```cpp
class bernoulli_distribution
   {
public:
   // types
   typedef bool result_type;
   struct param_type;

   // constructors and reset functions
   explicit bernoulli_distribution(double p = 0.5);
   explicit bernoulli_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>参数

*URNG*\
统一随机数生成器引擎。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md) 。

## <a name="remarks"></a>备注

类描述产生类型的值的分布 **`bool`** ，根据伯努利分布离散概率函数进行分布。 下表链接到有关各个成员的文章。

||||
|-|-|-|
|[bernoulli_distribution](#bernoulli_distribution)|`bernoulli_distribution::p`|`bernoulli_distribution::param`|
|`bernoulli_distribution::operator()`||[param_type](#param_type)|

属性函数 `p()` 将返回当前存储的分布参数值 `p`。

属性成员 `param()` 将设置或返回 `param_type` 存储的分布参数包。

`min()` 和 `max()` 成员函数将分别返回最小可能结果和最大可能结果。

`reset()` 成员函数将放弃所有缓存的值，使下一个对 `operator()` 的调用的结果不取决于在调用之前从引擎获得的任何值。

`operator()` 成员函数将根据 URNG 引擎，从当前参数包或指定参数包返回下一个生成的值。

有关分布类及其成员的详细信息，请参阅 [\<random>](../standard-library/random.md) 。

有关伯努利分布离散型概率函数的详细信息，请参阅 Wolfram MathWorld 文章[伯努利分布](https://go.microsoft.com/fwlink/p/?linkid=398467)。

## <a name="example"></a>示例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double p, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::bernoulli_distribution distr(p);

    std::cout << "p == " << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<bool, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::boolalpha << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double p_dist = 0.5;
    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(p_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45
Enter an integer value for a sample count: 100
p == 0.45
Histogram for 100 samples:
false :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
true :::::::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>要求

**标头：**\<random>

**命名空间:** std

## <a name="bernoulli_distributionbernoulli_distribution"></a><a name="bernoulli_distribution"></a>bernoulli_distribution：： bernoulli_distribution

构造分布。

```cpp
explicit bernoulli_distribution(double p = 0.5);
explicit bernoulli_distribution(const param_type& parm);
```

### <a name="parameters"></a>参数

*h-p*\
存储的 `p` 分布参数。

*parm*\
用于构造分布的 `param_type` 结构。

### <a name="remarks"></a>备注

**前提条件：**`0.0 ≤ p ≤ 1.0`

第一个构造函数将构造一个其存储的 `p` 值保留值 *p* 的对象。

第二个构造函数将构造一个从 parm** 初始化其存储的参数的对象。 通过调用 `param()` 成员函数，可获取和设置当前的现有分发参数。

## <a name="bernoulli_distributionparam_type"></a><a name="param_type"></a>bernoulli_distribution：:p aram_type

包含分布的参数。

struct param_type {typedef bernoulli_distribution distribution_type; param_type （double p = 0.5）; double p （） const;

   bool operator==(const param_type& right) const; bool operator!=(const param_type& right) const; };

### <a name="parameters"></a>参数

*h-p*\
存储的 `p` 分布参数。

### <a name="remarks"></a>备注

**前提条件：**`0.0 ≤ p ≤ 1.0`

在实例化时，可将此结构传递给分布的类构造函数、传递给 `param()` 成员函数以设置现有分布的存储参数，并传递给 `operator()` 以代替存储参数使用。

## <a name="see-also"></a>另请参阅

[\<random>](../standard-library/random.md)
