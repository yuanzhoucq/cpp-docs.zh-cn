---
title: "uniform_real_distribution 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::uniform_real_distribution
- random/std::uniform_real_distribution::reset
- random/std::uniform_real_distribution::a
- random/std::uniform_real_distribution::b
- random/std::uniform_real_distribution::param
- random/std::uniform_real_distribution::min
- random/std::uniform_real_distribution::max
- random/std::uniform_real_distribution::operator()
- random/std::uniform_real_distribution::param_type
- random/std::uniform_real_distribution::param_type::a
- random/std::uniform_real_distribution::param_type::b
- random/std::uniform_real_distribution::param_type::operator==
- random/std::uniform_real_distribution::param_type::operator!=
dev_langs: C++
helpviewer_keywords:
- std::uniform_real_distribution [C++]
- std::uniform_real_distribution [C++], reset
- std::uniform_real_distribution [C++], a
- std::uniform_real_distribution [C++], b
- std::uniform_real_distribution [C++], param
- std::uniform_real_distribution [C++], min
- std::uniform_real_distribution [C++], max
- std::uniform_real_distribution [C++], param_type
- std::uniform_real_distribution [C++], param_type
ms.assetid: 5cf906fd-0319-4984-b21b-98425cd7532d
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 484997806cadb75b0322e9d194fe37ab30dae3b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="uniformrealdistribution-class"></a>uniform_real_distribution 类
在包含起始值不包含结束值的输出范围中生成均匀的（每个值的概率都均等）浮点分布。  
  
## <a name="syntax"></a>语法  
```  
template<class RealType = double>
   class uniform_real_distribution {
public:
   // types 
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions 
   explicit uniform_real_distribution(
      result_type a = 0.0, result_type b = 1.0);
   explicit uniform_real_distribution(const param_type& parm);
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
*RealType*  
浮点结果类型，默认为 `double`。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>备注  
模板类描述了包含起始值不包含结束值的分布，该分布使用某个分布产生用户指定的浮点整型值，以便每个值的概率都均等。 下表链接到有关各个成员的文章。  
  
||||  
|-|-|-|  
|[uniform_real_distribution](#uniform_real_distribution)|`uniform_real_distribution::a`|`uniform_real_distribution::param`|  
|`uniform_real_distribution::operator()`|`uniform_real_distribution::b`|[param_type](#param_type)|  
  
属性成员 `a()` 将返回分布当前存储的下限，而 `b()` 将返回当前存储的上限。 对于此分布类，这些最小值和最大值与 [\<random>](../standard-library/random.md) 主题中描述的常用属性函数 `min()` 和 `max()` 返回的值相同。  
  
属性成员 `param()` 将设置或返回 `param_type` 存储的分布参数包。  

`min()` 和 `max()` 成员函数将分别返回最小可能结果和最大可能结果。  
  
`reset()` 成员函数将放弃所有缓存的值，使下一个对 `operator()` 的调用的结果不取决于在调用之前从引擎获得的任何值。  
  
`operator()` 成员函数将根据 URNG 引擎，从当前参数包或指定参数包返回下一个生成的值。
  
若要深入了解分布类及其成员，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="example"></a>示例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double a, const double b, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::uniform_real_distribution<> distr(a,b);  
  
    std::cout << "lower bound == " << distr.a() << std::endl;  
    std::cout << "upper bound == " << distr.b() << std::endl;  
  
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
            << std::setprecision(10) << elem.first << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    double a_dist = 1.0;  
    double b_dist = 1.5;  
  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the lower bound of the distribution: ";  
    std::cin >> a_dist;  
    std::cout << "Enter a floating point value for the upper bound of the distribution: ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the lower bound of the distribution: 0
Enter a floating point value for the upper bound of the distribution: 1
Enter an integer value for the sample count: 10
lower bound == 0
upper bound == 1
Distribution for 10 samples:
          1: 0.0288609485
          2: 0.2007994386
          3: 0.3027480117
          4: 0.4124758695
          5: 0.4413777133
          6: 0.4846447405
          7: 0.6225745916
          8: 0.6880935217
          9: 0.7541936723
         10: 0.8795716566
```  
  
## <a name="requirements"></a>惠?  
 **标头：**\<random>  
  
 **命名空间：** std  
  
##  <a name="uniform_real_distribution"></a>uniform_real_distribution::uniform_real_distribution  
构造分布。  
  
```  
explicit uniform_real_distribution(result_type a = 0.0, result_type b = 1.0);
explicit uniform_real_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>参数  
*a*  
随机值的下限（包含下限）。  
  
*b*  
随机值的上限（不包含上限）。  
  
*parm*  
用于构造分布的 `param_type` 结构。  
  
### <a name="remarks"></a>备注  
 **前置条件：**`a < b`  
  
第一个构造函数将构造一个对象，该对象存储的 `a` 值保留值 a，并且存储的 `b` 值保留值 b。  
  
第二个构造函数将构造一个从 parm 初始化其存储的参数的对象。 通过调用 `param()` 成员函数，可获取和设置当前的现有分发参数。  
  
##  <a name="param_type"></a>uniform_real_distribution::param_type  
 存储分布的所有参数。  
  
```  
struct param_type {  
   typedef uniform_real_distribution<result_type> distribution_type;  
   param_type(result_type a = 0.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
### <a name="parameters"></a>参数  
*a*  
随机值的下限（包含下限）。  
  
*b*  
随机值的上限（不包含上限）。  
  
*right*  
要与它进行比较的 `param_type` 对象。  
  
### <a name="remarks"></a>备注  
 **前置条件：**`a < b`  
  
在实例化时，可将此结构传递给分布的类构造函数、传递给 `param()` 成员函数以设置现有分布的存储参数，并传递给 `operator()` 以代替存储参数使用。  
  
## <a name="see-also"></a>请参阅  
 [\<random>](../standard-library/random.md)



