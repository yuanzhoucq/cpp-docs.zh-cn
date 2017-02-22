---
title: "negative_binomial_distribution 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1::negative_binomial_distribution"
  - "tr1.negative_binomial_distribution"
  - "std.tr1.negative_binomial_distribution"
  - "random/std::tr1::negative_binomial_distribution"
  - "std::tr1::negative_binomial_distribution"
  - "negative_binomial_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "negative_binomial_distribution 类"
ms.assetid: 7f5f0967-7fdd-4578-99d4-88f292b4fe9c
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# negative_binomial_distribution 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成负二项式分布。  
  
## 语法  
  
```  
template<class IntType = int> class negative_binomial_distribution { public:     // types     typedef IntType result_type;     struct param_type;     // constructor and reset functions     explicit negative_binomial_distribution(IntType k = 1, double p = 0.5);     explicit negative_binomial_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     IntType k() const;     double p() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 参数  
 `IntType`  
 整数结果类型，默认为 `int`。  有关可能的类型，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 如果未根据负二项式分布离散型概率函数提供和分布任何类型，则模板类将描述产生用户指定的整型值或 `int` 型值的分布。  下表链接到有关各个成员的文章。  
  
||||  
|-|-|-|  
|[negative\_binomial\_distribution::negative\_binomial\_distribution](../Topic/negative_binomial_distribution::negative_binomial_distribution.md)|`negative_binomial_distribution::k`|`negative_binomial_distribution::param`|  
|`negative_binomial_distribution::operator()`|`negative_binomial_distribution::p`|[negative\_binomial\_distribution::param\_type](../Topic/negative_binomial_distribution::param_type.md)|  
  
 属性成员 `k()` 和 `p()` 将分别返回当前存储的分布参数值 `k` 和 `p`。  
  
 有关分布类及其成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
 有关负二项式分布离散型概率函数的详细信息，请参阅 Wolfram MathWorld 文章[负二项式分布](http://go.microsoft.com/fwlink/?LinkId=400516)。  
  
## 示例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const int k, const double p, const int& s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::negative_binomial_distribution<> distr(k, p);  
  
    std::cout << std::endl;  
    std::cout << "k == " << distr.k() << std::endl;  
    std::cout << "p == " << distr.p() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Histogram for " << s << " samples:" << std::endl;  
    for (const auto& elem : histogram) {  
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    int    k_dist = 1;  
    double p_dist = 0.5;  
    int    samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter an integer value for k distribution (where 0 < k): ";  
    std::cin >> k_dist;  
    std::cout << "Enter a double value for p distribution (where 0.0 < p <= 1.0): ";  
    std::cin >> p_dist;  
    std::cout << "Enter an integer value for a sample count: ";  
    std::cin >> samples;  
  
    test(k_dist, p_dist, samples);  
}  
  
```  
  
## 输出  
 首次运行：  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter an integer value for k distribution (where 0 < k): 1  
Enter a double value for p distribution (where 0.0 < p <= 1.0): .5  
Enter an integer value for a sample count: 100  
  
k == 1  
p == 0.5  
Histogram for 100 samples:  
    0 :::::::::::::::::::::::::::::::::::::::::::  
    1 ::::::::::::::::::::::::::::::::  
    2 ::::::::::::  
    3 :::::::  
    4 ::::  
    5 ::  
```  
  
 第二次运行：  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter an integer value for k distribution (where 0 < k): 100  
Enter a double value for p distribution (where 0.0 < p <= 1.0): .667  
Enter an integer value for a sample count: 100  
  
k == 100  
p == 0.667  
Histogram for 100 samples:  
   31 ::  
   32 :  
   33 ::  
   34 :  
   35 ::  
   37 ::  
   38 :  
   39 :  
   40 ::  
   41 :::  
   42 :::  
   43 :::::  
   44 :::::  
   45 ::::  
   46 ::::::  
   47 ::::::::  
   48 :::  
   49 :::  
   50 :::::::::  
   51 :::::::  
   52 ::  
   53 :::  
   54 :::::  
   56 ::::  
   58 :  
   59 :::::  
   60 ::  
   61 :  
   62 ::  
   64 :  
   69 ::::  
```  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)