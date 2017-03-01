---
title: "fisher_f_distribution 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fisher_f_distribution
- std::fisher_f_distribution
- random/std::fisher_f_distribution
- std::fisher_f_distribution::reset
- random/std::fisher_f_distribution::reset
- std::fisher_f_distribution::m
- random/std::fisher_f_distribution::m
- std::fisher_f_distribution::n
- random/std::fisher_f_distribution::n
- std::fisher_f_distribution::param
- random/std::fisher_f_distribution::param
- std::fisher_f_distribution::min
- random/std::fisher_f_distribution::min
- std::fisher_f_distribution::max
- random/std::fisher_f_distribution::max
- std::fisher_f_distribution::operator()
- random/std::fisher_f_distribution::operator()
- std::fisher_f_distribution::param_type
- random/std::fisher_f_distribution::param_type
- std::fisher_f_distribution::param_type::m
- random/std::fisher_f_distribution::param_type::m
- std::fisher_f_distribution::param_type::n
- random/std::fisher_f_distribution::param_type::n
- std::fisher_f_distribution::param_type::operator==
- random/std::fisher_f_distribution::param_type::operator==
- std::fisher_f_distribution::param_type::operator!=
- random/std::fisher_f_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- fisher_f_distribution class
ms.assetid: 9513b6ce-3309-4be1-829b-f504bca35bbf
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: f293f074f2b8e2334dc70fbebba8e6f4c17efecc
ms.openlocfilehash: 3a0fc233334909249f75978ba095cb3f31af90dc
ms.lasthandoff: 02/24/2017

---
# <a name="fisherfdistribution-class"></a>fisher_f_distribution 类
生成 Fisher F 分布。  
  
## <a name="syntax"></a>语法  
```  
template<class RealType = double>
class fisher_f_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  // constructor and reset functions  
   explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
   explicit fisher_f_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions  
   result_type m() const;
   result_type n() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```  
#### <a name="parameters"></a>参数  
*RealType*  
浮点结果类型，默认为 `double`。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。  
  
*URNG* 均匀随机数生成器引擎。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>备注  
 此模板类描述了生成用户指定浮点类型或根据 Fisher 的 F-分布分配的 `double` 类型（如果未提供任何内容）的值的分配。 下表链接到有关各个成员的文章。  
  
||||  
|-|-|-|  
|[fisher_f_distribution::fisher_f_distribution](#fisher_f_distribution__fisher_f_distribution)|`fisher_f_distribution::m`|`fisher_f_distribution::param`|  
|`fisher_f_distribution::operator()`|`fisher_f_distribution::n`|[fisher_f_distribution::param_type](#fisher_f_distribution__param_type)|  
  
 属性函数 `m()` 和 `n()` 将分别返回存储的分布参数 `m` 和 `n` 的值。  
  
属性成员 `param()` 将设置或返回 `param_type` 存储的分布参数包。  

`min()` 和 `max()` 成员函数将分别返回最小可能结果和最大可能结果。  
  
`reset()` 成员函数将放弃所有缓存的值，使下一个对 `operator()` 的调用的结果不取决于在调用之前从引擎获得的任何值。  
  
`operator()` 成员函数将根据 URNG 引擎，从当前参数包或指定参数包返回下一个生成的值。
  
 有关分布类及其成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。  
  
 有关 F-分布的详细信息，请参阅 Wolfram MathWorld 文章 [F-分布](http://go.microsoft.com/fwlink/LinkId=400899)。  
  
## <a name="example"></a>示例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double m, const double n, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1701);  
  
    std::fisher_f_distribution<> distr(m, n);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "m() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.m() << std::endl;  
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;  
  
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
    double m_dist = 1;  
    double n_dist = 1;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the \'m\' distribution parameter (must be greater than zero): ";  
    std::cin >> m_dist;  
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";  
    std::cin >> n_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(m_dist, n_dist, samples);  
}  
  
```  
  
## <a name="output"></a>输出  
 首次运行：  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 1.0000000000  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0204569549  
    2: 0.0221376644  
    3: 0.0297234962  
    4: 0.1600937252  
    5: 0.2775342196  
    6: 0.3950701700  
    7: 0.8363200295  
    8: 0.9512500702  
    9: 2.7844815974  
    10: 3.4320929653  
```  
  
 第二次运行：  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 1.0000000000  
n() == 0.1000000000  
Distribution for 10 samples:  
    1: 0.0977725649  
    2: 0.5304122767  
    3: 4.9468518084  
    4: 25.1012074939  
    5: 48.8082121613  
    6: 401.8075539377  
    7: 8199.5947873699  
    8: 226492.6855335717  
    9: 2782062.6639740225  
    10: 20829747131.7185860000  
```  
  
 第三次运行：  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): .1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 0.1000000000  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0000000000  
    2: 0.0000000000  
    3: 0.0000000000  
    4: 0.0000000000  
    5: 0.0000000033  
    6: 0.0000073975  
    7: 0.0000703800  
    8: 0.0280427735  
    9: 0.2660239949  
    10: 3.4363333954  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<random>  
  
 **命名空间：** std  
  
##  <a name="a-namefisherfdistributionfisherfdistributiona--fisherfdistributionfisherfdistribution"></a><a name="fisher_f_distribution__fisher_f_distribution"></a>  fisher_f_distribution::fisher_f_distribution  
 构造分布。  
  
```  
explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
explicit fisher_f_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>参数  
*m*  
 `m` 分布参数。  
  
*n*  
 `n` 分布参数。  
  
*parm*  
 用于构造分布的 `param_type` 结构。  
  
### <a name="remarks"></a>备注  
 **前置条件：**`0.0 < m` 和 `0.0 < n`  
  
 第一个构造函数将构造一个其存储的 `m` 值保留值 *m*，而其存储的 `n` 值保留值 *n* 的对象。  
  
 第二个构造函数将构造一个从 *parm* 初始化其存储的参数的对象。 通过调用 `param()` 成员函数，可获取和设置当前的现有分发参数。  
  
##  <a name="a-namefisherfdistributionparamtypea--fisherfdistributionparamtype"></a><a name="fisher_f_distribution__param_type"></a>  fisher_f_distribution::param_type  
 存储分布的参数。  
  
```cpp  
struct param_type {  
   typedef fisher_f_distribution<result_type> distribution_type;  
   param_type(result_type m = 1.0, result_type n = 1.0);
   result_type m() const;
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
### <a name="parameters"></a>参数  
*m*  
 `m` 分布参数。  
  
*n*  
 `n` 分布参数。  
  
*right*  
要与它进行比较的 `param_type` 对象。  
  
### <a name="remarks"></a>备注  
 **前置条件：**`0.0 < m` 和 `0.0 < n`  
  
 在实例化时，可将此结构传递给分布的类构造函数、传递给 `param()` 成员函数以设置现有分布的存储参数，并传递给 `operator()` 以代替存储参数使用。  
  
## <a name="see-also"></a>另请参阅  
 [\<random>](../standard-library/random.md)




