---
title: "uniform_int_distribution 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1.uniform_int_distribution"
  - "random/std::tr1::uniform_int_distribution"
  - "uniform_int_distribution"
  - "tr1::uniform_int_distribution"
  - "std.tr1.uniform_int_distribution"
  - "std::tr1::uniform_int_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uniform_int_distribution 类"
ms.assetid: a1867dcd-3bd9-4787-afe3-4b62692c1d04
caps.latest.revision: 20
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# uniform_int_distribution 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在包含起始值和结束值的输出范围中生成均匀的（每个值的概率都均等）整数分布。  
  
## 语法  
  
```  
template<class IntType = int> class uniform_int_distribution { public:     // types     typedef IntType result_type;     struct param_type;     // constructors and reset functions     explicit uniform_int_distribution(IntType a = 0, IntType b = numeric_limits<IntType>::max());     explicit uniform_int_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     result_type a() const;     result_type b() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 参数  
 `IntType`  
 整数结果类型，默认为 `int`。  有关可能的类型，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 模板类描述了包含起始值和结束值的分布，该分布使用某个分布产生用户指定的整型值，以便每个值的概率都均等。  下表链接到有关各个成员的文章。  
  
||||  
|-|-|-|  
|[uniform\_int\_distribution::uniform\_int\_distribution](../Topic/uniform_int_distribution::uniform_int_distribution.md)|`uniform_int_distribution::a`|`uniform_int_distribution::param`|  
|`uniform_int_distribution::operator()`|`uniform_int_distribution::b`|[uniform\_int\_distribution::param\_type](../Topic/uniform_int_distribution::param_type.md)|  
  
 属性成员 `a()` 将返回分布当前存储的下限，而 `b()` 将返回当前存储的上限。  对于此分布类，这些最小值和最大值与 [\<random\>](../standard-library/random.md) 主题中描述的常用属性函数 `min()` 和 `max()` 返回的值相同。  
  
 有关分布类及其成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 示例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const int a, const int b, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::uniform_int_distribution<> distr(a, b);  
  
    std::cout << "lower bound == " << distr.a() << std::endl;  
    std::cout << "upper bound == " << distr.b() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Distribution for " << s << " samples:" << std::endl;  
    for (const auto& elem : histogram) {  
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    int a_dist = 1;  
    int b_dist = 10;  
  
    int samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter an integer value for the lower bound of the distribution: ";  
    std::cin >> a_dist;  
    std::cout << "Enter an integer value for the upper bound of the distribution: ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
  
```  
  
## 输出  
  **使用 CTRL\-Z 跳过数据输入并使用默认值运行。  输入分布下限的整数值：0**  
**输入分布上限的整数值：12**  
**输入示例计数的整数值：200**  
**下限 \=\= 0**  
**上限 \=\= 12**  
**200 个示例的分布：**  
 **0 :::::::::::::::**  
 **1 :::::::::::::::::::::**  
 **2 ::::::::::::::::::**  
 **3 :::::::::::::::**  
 **4 :::::::**  
 **5 :::::::::::::::::::::**  
 **6 :::::::::::::**  
 **7 ::::::::::**  
 **8 :::::::::::::::**  
 **9 :::::::::::::**  
 **10 ::::::::::::::::::::::**  
 **11 :::::::::::::**  
**12 :::::::::::::::::**    
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)