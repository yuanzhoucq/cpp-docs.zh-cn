---
title: "cauchy_distribution 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cauchy_distribution
- std::cauchy_distribution
- random/std::cauchy_distribution
- std::cauchy_distribution::reset
- random/std::cauchy_distribution::reset
- std::cauchy_distribution::a
- random/std::cauchy_distribution::a
- std::cauchy_distribution::b
- random/std::cauchy_distribution::b
- std::cauchy_distribution::param
- random/std::cauchy_distribution::param
- std::cauchy_distribution::min
- random/std::cauchy_distribution::min
- std::cauchy_distribution::max
- random/std::cauchy_distribution::max
- std::cauchy_distribution::operator()
- random/std::cauchy_distribution::operator()
- std::cauchy_distribution::param_type
- random/std::cauchy_distribution::param_type
- std::cauchy_distribution::param_type::a
- random/std::cauchy_distribution::param_type::a
- std::cauchy_distribution::param_type::b
- random/std::cauchy_distribution::param_type::b
- std::cauchy_distribution::param_type::operator==
- random/std::cauchy_distribution::param_type::operator==
- std::cauchy_distribution::param_type::operator!=
- random/std::cauchy_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- cauchy_distribution class
ms.assetid: 21522351-f2f1-46d9-97f0-d358c932356c
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 02dd887f1b20b42145ccc83165570b9f682e693c
ms.openlocfilehash: 6cbe218a9bcac3b35952e6993cc496689e0290aa
ms.lasthandoff: 02/24/2017

---
# <a name="cauchydistribution-class"></a>cauchy_distribution 类
生成柯西分布。  
  
## <a name="syntax"></a>语法  
  
```  
template<class RealType = double>  
class cauchy_distribution {  
public:  
   // types 
   typedef RealType result_type;  
   struct param_type;  
   
   // constructor and reset functions  
   explicit cauchy_distribution(result_type a = 0.0, result_type b = 1.0);
   explicit cauchy_distribution(const param_type& parm);
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
  
*URNG* 均匀随机数生成器引擎。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。  

## <a name="remarks"></a>备注  
此模板类描述了生成用户指定浮点类型或根据柯西分步分配的 `double` 类型（如果未提供任何内容）的值的分配。 下表链接到有关各个成员的文章。  
  
||||  
|-|-|-|  
|[cauchy_distribution::cauchy_distribution](#cauchy_distribution__cauchy_distribution)|`cauchy_distribution::a`|`cauchy_distribution::param`|  
|`cauchy_distribution::operator()`|`cauchy_distribution::b`|[cauchy_distribution::param_type](#cauchy_distribution__param_type)|  
  
属性函数 `a()` 和 `b()` 返回存储的分布参数 `a` 和 `b` 的各自值。  
  
属性成员 `param()` 将设置或返回 `param_type` 存储的分布参数包。  

`min()` 和 `max()` 成员函数将分别返回最小可能结果和最大可能结果。  
  
`reset()` 成员函数将放弃所有缓存的值，使下一个对 `operator()` 的调用的结果不取决于在调用之前从引擎获得的任何值。  
  
`operator()` 成员函数将根据 URNG 引擎，从当前参数包或指定参数包返回下一个生成的值。
  
有关分布类及其成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。  
  
有关柯西分布的详细信息，请参阅 Wolfram MathWorld 文章[柯西分布](http://go.microsoft.com/fwlink/LinkId=400523)。  
  
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
  
    std::cauchy_distribution<> distr(a, b);  
  
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
    std::cout << "Enter a floating point value for the 'a' distribution parameter: ";  
    std::cin >> a_dist;  
    std::cout << "Enter a floating point value for the 'b' distribution parameter (must be greater than zero): ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
```  
  
首次运行：  
  
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
    1: -3.4650392984  
    2: -2.6369564174  
    3: -0.0786978867  
    4: -0.0609632093  
    5: 0.0589387400  
    6: 0.0589539764  
    7: 0.1004592006  
    8: 1.0965724260  
    9: 1.4389408122  
    10: 2.5253154706  
```  
  
第二次运行：  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'a' distribution parameter: 0  
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 10  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
a() == 0.0000000000  
b() == 10.0000000000  
Distribution for 10 samples:  
    1: -34.6503929840  
    2: -26.3695641736  
    3: -0.7869788674  
    4: -0.6096320926  
    5: 0.5893873999  
    6: 0.5895397637  
    7: 1.0045920062  
    8: 10.9657242597  
    9: 14.3894081218  
    10: 25.2531547063  
```  
  
第三次运行：  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'a' distribution parameter: 10  
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 10  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
a() == 10.0000000000  
b() == 10.0000000000  
Distribution for 10 samples:  
    1: -24.6503929840  
    2: -16.3695641736  
    3: 9.2130211326  
    4: 9.3903679074  
    5: 10.5893873999  
    6: 10.5895397637  
    7: 11.0045920062  
    8: 20.9657242597  
    9: 24.3894081218  
    10: 35.2531547063  
```  
  
## <a name="requirements"></a>要求  
**标头：**\<random>  
  
**命名空间：** std  
  
##  <a name="a-namecauchydistributioncauchydistributiona--cauchydistributioncauchydistribution"></a><a name="cauchy_distribution__cauchy_distribution"></a>  cauchy_distribution::cauchy_distribution  
构造分布。  
  
```  
explicit cauchy_distribution(result_type a = 0.0, result_type b = 1.0);
explicit cauchy_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>参数  
*a*  
`a` 分布参数。  
  
*b*  
`b` 分布参数。  
  
*parm*  
用于构造分布的 `param_type` 结构。  
  
### <a name="remarks"></a>备注  
**前提条件：**`0.0 < b`  
  
第一个构造函数将构造一个对象，该对象存储的 `a` 值保留值 a，并且存储的 `b` 值保留值 b。  
  
第二个构造函数将构造一个从 parm 初始化其存储的参数的对象。 通过调用 `param()` 成员函数，可获取和设置当前的现有分发参数。  
  
##  <a name="a-namecauchydistributionparamtypea--cauchydistributionparamtype"></a><a name="cauchy_distribution__param_type"></a>  cauchy_distribution::param_type  
存储分布的所有参数。  
  
```cpp    
struct param_type {  
   typedef cauchy_distribution<result_type> distribution_type;  
   param_type(result_type a = 0.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
  
### <a name="parameters"></a>参数  
*a*  
`a` 分布参数。  
  
*b*  
`b` 分布参数。  
  
*right*  
要与它进行比较的 `param_type` 对象。  
  
### <a name="remarks"></a>备注  
**前置条件：**`0.0 < b`  
  
在实例化时，可将此结构传递给分布的类构造函数、传递给 `param()` 成员函数以设置现有分布的存储参数，并传递给 `operator()` 以代替存储参数使用。  
  
## <a name="see-also"></a>另请参阅  
[\<random>](../standard-library/random.md)




