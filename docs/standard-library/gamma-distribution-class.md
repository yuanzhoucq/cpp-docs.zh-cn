---
title: "gamma_distribution 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "random/std::tr1::gamma_distribution"
  - "std::tr1::gamma_distribution"
  - "std.tr1.gamma_distribution"
  - "tr1.gamma_distribution"
  - "tr1::gamma_distribution"
  - "gamma_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gamma_distribution 类"
  - "gamma_distribution 类 [TR1]"
ms.assetid: 2a6798ac-6152-41d7-8ef6-d684d92f1572
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# gamma_distribution 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成 gamma 分布。  
  
## 语法  
  
```  
template<class RealType = double> class gamma_distribution { public:     // types     typedef RealType result_type;     struct param_type;     // constructors and reset functions     explicit gamma_distribution(RealType alpha = 1.0, RealType beta = 1.0);     explicit gamma_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     RealType alpha() const;     RealType beta() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 参数  
 `RealType`  
 浮点结果类型，默认为 `double`。  有关可能的类型，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 如果未根据 Gamma 分布提供和分布任何类型，则模板类将描述产生用户指定的整型值或 `double` 型值的分布。  下表链接到有关各个成员的文章。  
  
||||  
|-|-|-|  
|[gamma\_distribution::gamma\_distribution](../Topic/gamma_distribution::gamma_distribution.md)|`gamma_distribution::alpha`|`gamma_distribution::param`|  
|`gamma_distribution::operator()`|`gamma_distribution::beta`|[gamma\_distribution::param\_type](../Topic/gamma_distribution::param_type.md)|  
  
 属性函数 `alpha()` 和 `beta()` 返回存储的分布参数 `alpha` 和 `beta` 的各自值。  
  
 有关分布类及其成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
 有关 gamma 分布的详细信息，请参阅 Wolfram MathWorld 文章 [Gamma 分布](http://go.microsoft.com/fwlink/?LinkId=401111)。  
  
## 示例  
  
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
  
    std::gamma_distribution<> distr(a, b);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "alpha() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.alpha() << std::endl;  
    std::cout << "beta() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.beta() << std::endl;  
  
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
    std::cout << "Enter a floating point value for the 'alpha' distribution parameter (must be greater than zero): ";  
    std::cin >> a_dist;  
    std::cout << "Enter a floating point value for the 'beta' distribution parameter (must be greater than zero): ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
  
```  
  
## 输出  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'alpha' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'beta' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
  
min() == 4.94066e-324  
max() == 1.79769e+308  
alpha() == 1.0000000000  
beta() == 1.0000000000  
Distribution for 10 samples:  
          1:   0.0936880533  
          2:   0.1225944894  
          3:   0.6443593183  
          4:   0.6551171649  
          5:   0.7313457551  
          6:   0.7313557977  
          7:   0.7590097389  
          8:   1.4466885214  
          9:   1.6434088411  
         10:   2.1201210996  
```  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)