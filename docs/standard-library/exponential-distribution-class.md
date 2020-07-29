---
title: exponential_distribution 类
ms.date: 11/04/2016
f1_keywords:
- random/std::exponential_distribution
- random/std::exponential_distribution::reset
- random/std::exponential_distribution::lambda
- random/std::exponential_distribution::param
- random/std::exponential_distribution::min
- random/std::exponential_distribution::max
- random/std::exponential_distribution::operator()
- random/std::exponential_distribution::param_type
- random/std::exponential_distribution::param_type::lambda
- random/std::exponential_distribution::param_type::operator==
- random/std::exponential_distribution::param_type::operator!=
helpviewer_keywords:
- std::exponential_distribution [C++]
- std::exponential_distribution [C++], reset
- std::exponential_distribution [C++], lambda
- std::exponential_distribution [C++], param
- std::exponential_distribution [C++], min
- std::exponential_distribution [C++], max
- std::exponential_distribution [C++], param_type
- std::exponential_distribution [C++], param_type
ms.assetid: d54f3126-a09b-45f9-a30b-0d94d03bcdc9
ms.openlocfilehash: db176bef55455c0553e5865e268c4e4e8fed089d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212353"
---
# <a name="exponential_distribution-class"></a>exponential_distribution 类

生成指数分布。

## <a name="syntax"></a>语法

```cpp
template<class RealType = double>
class exponential_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit exponential_distribution(result_type lambda = 1.0);
   explicit exponential_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type lambda() const;
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

**`double`** 如果未根据指数分布提供和分布任何类型，则类模板将描述产生用户指定的整型值的分布。 下表链接到有关各个成员的文章。

||||
|-|-|-|
|[exponential_distribution](#exponential_distribution)|`exponential_distribution::lambda`|`exponential_distribution::param`|
|`exponential_distribution::operator()`||[param_type](#param_type)|

属性成员函数 `lambda()` 将返回存储的分布参数 `lambda` 的值。

属性成员函数 `param()` 将设置或返回 `param_type` 存储分布参数包。

有关分布类及其成员的详细信息，请参阅 [\<random>](../standard-library/random.md) 。

有关指数分布的详细信息，请参阅 Wolfram MathWorld 文章[指数分布](https://go.microsoft.com/fwlink/p/?linkid=401098)。

## <a name="example"></a>示例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double l, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::exponential_distribution<> distr(l);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "lambda() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.lambda() << std::endl;

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
    double l_dist = 0.5;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): ";
    std::cin >> l_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(l_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
lambda() == 1.0000000000
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

## <a name="requirements"></a>要求

**标头：**\<random>

**命名空间:** std

## <a name="exponential_distributionexponential_distribution"></a><a name="exponential_distribution"></a>exponential_distribution：： exponential_distribution

构造分布。

```cpp
explicit exponential_distribution(result_type lambda = 1.0);
explicit exponential_distribution(const param_type& parm);
```

### <a name="parameters"></a>参数

*lambda*\
`lambda` 分布参数。

*parm*\
用于构造分布的参数包。

### <a name="remarks"></a>备注

**前提条件：**`0.0 < lambda`

第一个构造函数将构造一个其存储的 `lambda` 值保留值 *lambda* 的对象。

第二个构造函数将构造一个从 parm** 初始化其存储的参数的对象。 通过调用 `param()` 成员函数，可获取和设置当前的现有分发参数。

## <a name="exponential_distributionparam_type"></a><a name="param_type"></a>exponential_distribution：:p aram_type

存储分布的参数。

```cpp
struct param_type {
   typedef exponential_distribution<result_type> distribution_type;
   param_type(result_type lambda = 1.0);
   result_type lambda() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>参数

*lambda*\
`lambda` 分布参数。

*然后*\
要与它进行比较的 `param_type` 对象。

### <a name="remarks"></a>备注

**前提条件：**`0.0 < lambda`

在实例化时，可将此结构传递给分布的类构造函数、传递给 `param()` 成员函数以设置现有分布的存储参数，并传递给 `operator()` 以代替存储参数使用。

## <a name="see-also"></a>另请参阅

[\<random>](../standard-library/random.md)
