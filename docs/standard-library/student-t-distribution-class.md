---
title: "student_t_distribution 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::student_t_distribution
- random/std::student_t_distribution::result_type
- random/std::student_t_distribution::reset
- random/std::student_t_distribution::operator()
- random/std::student_t_distribution::n
- random/std::student_t_distribution::param
- random/std::student_t_distribution::min
- random/std::student_t_distribution::max
- random/std::student_t_distribution::param_type
dev_langs: C++
helpviewer_keywords:
- std::student_t_distribution [C++]
- std::student_t_distribution [C++], result_type
- std::student_t_distribution [C++], reset
- std::student_t_distribution [C++], n
- std::student_t_distribution [C++], param
- std::student_t_distribution [C++], min
- std::student_t_distribution [C++], max
- std::student_t_distribution [C++], param_type
ms.assetid: 87b48127-9311-4d07-95df-833ed46bf0b1
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ac4d4e6a27c7686cb6a8f34209870fe3f89c265
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="studenttdistribution-class"></a>student_t_distribution 类
生成学生的 *t*-分布。  
  
## <a name="syntax"></a>语法  
```  
template<class RealType = double>
class student_t_distribution {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  
   
   // constructor and reset functions  
   explicit student_t_distribution(result_type n = 1.0);
   explicit student_t_distribution(const param_type& parm);
   void reset();
   
   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);
   
   // property functions  
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
  
## <a name="remarks"></a>备注  
 如果未根据学生的 `double`t*-分布提供和分布任何类型，则模板类将描述产生用户指定的整型值或*  型值的分布。 下表链接到有关各个成员的文章。  
  
||||  
|-|-|-|  
|[student_t_distribution](#student_t_distribution)|`student_t_distribution::n`|`student_t_distribution::param`|  
|`student_t_distribution::operator()`||[param_type](#param_type)|  
  
 属性函数 `n()` 将返回存储的分布参数 `n` 的值。  
  
 若要深入了解分布类及其成员，请参阅 [\<random>](../standard-library/random.md)。  
  
 有关学生的 *t* 分布的详细信息，请参阅 Wolfram MathWorld 文章[学生的 t-分布](http://go.microsoft.com/fwlink/LinkId=401094)。  
  
## <a name="example"></a>示例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double n, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
    std::mt19937 gen(1701);  
  
    std::student_t_distribution<> distr(n);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
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
    double n_dist = 0.5;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the 'n' distribution parameter (must be greater than zero): ";  
    std::cin >> n_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(n_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: -1.3084956212  
    2: -1.0899518684  
    3: -0.9568771388  
    4: -0.9372088821  
    5: -0.7381334669  
    6: -0.2488074854  
    7: -0.2028714601  
    8: 1.4013074495  
    9: 5.3244792236  
    10: 92.7084335614  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<random>  
  
 **命名空间：** std  
  
##  <a name="student_t_distribution"></a>  student_t_distribution::student_t_distribution  
 构造分布。  
  
```  
explicit student_t_distribution(RealType n = 1.0);
explicit student_t_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>参数  
*n*  
 `n` 分布参数。  
  
*parm*  
 用于构造分布的参数包。  
  
### <a name="remarks"></a>备注  
 **前置条件：**`0.0 < n`  
  
 第一个构造函数构造一个对象，其存储`n`值保留值 *n* 。  
  
 第二个构造函数将构造一个从 *parm* 初始化其存储的参数的对象。 通过调用 `param()` 成员函数，可获取和设置当前的现有分发参数。  
  
##  <a name="param_type"></a>  student_t_distribution::param_type  
 存储分布的所有参数。  
```cpp    
struct param_type {  
   typedef student_t_distribution<result_type> distribution_type;  
   param_type(result_type n = 1.0);
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
  
### <a name="parameters"></a>参数  
*n*  
`n` 分布参数。  
  
*right*  
要与它进行比较的 `param_type` 对象。  
  
### <a name="remarks"></a>备注  
 **前置条件：**`0.0 < n`  
  
 在实例化时，可将此结构传递给分布的类构造函数、传递给 `param()` 成员函数以设置现有分布的存储参数，并传递给 `operator()` 以代替存储参数使用。  
  
## <a name="see-also"></a>另请参阅  
 [\<random>](../standard-library/random.md)



