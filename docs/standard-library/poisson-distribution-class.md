---
title: "poisson_distribution 类 | Microsoft Docs"
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
  - "poisson_distribution"
  - "std.tr1.poisson_distribution"
  - "random/std::tr1::poisson_distribution"
  - "std::tr1::poisson_distribution"
  - "tr1.poisson_distribution"
  - "tr1::poisson_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "poisson_distribution 类"
  - "poisson_distribution 类 [TR1]"
ms.assetid: 09614281-349a-45f7-8e95-c0196be0a937
caps.latest.revision: 19
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# poisson_distribution 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成泊松分布。  
  
## 语法  
  
```  
template<class IntType = int> class poisson_distribution { public:     // types     typedef IntType result_type;     struct param_type;     // constructors and reset functions     explicit poisson_distribution(double mean = 1.0);     explicit poisson_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     double mean() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 参数  
 `IntType`  
 整数结果类型，默认为 `int`。  有关可能的类型，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 模板类将描述使用泊松分布产生用户指定的整型值的分布。  下表链接到有关各个成员的文章。  
  
||||  
|-|-|-|  
|[poisson\_distribution::poisson\_distribution](../Topic/poisson_distribution::poisson_distribution.md)|`poisson_distribution::mean`|`poisson_distribution::param`|  
|`poisson_distribution::operator()`||[poisson\_distribution::param\_type](../Topic/poisson_distribution::param_type.md)|  
  
 属性函数 `mean()` 将返回存储的分布参数 `mean` 的值。  
  
 有关分布类及其成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
 有关泊松分布的详细信息，请参阅 Wolfram MathWorld 文章[泊松分布](http://go.microsoft.com/fwlink/?LinkId=401112)。  
  
## 示例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double p, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
    std::mt19937 gen(1701);  
  
    std::poisson_distribution<> distr(p);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "p() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.mean() << std::endl;  
  
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
    double p_dist = 1.0;  
  
    int samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the 'mean' distribution parameter (must be greater than zero): ";  
    std::cin >> p_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(p_dist, samples);  
}  
  
```  
  
## 输出  
 首次测试：  
  
  **使用 CTRL\-Z 跳过数据输入并使用默认值运行。  输入“mean”分布参数的浮点值（必须大于零）：1**  
**输入示例计数的整数值：100**  
**min\(\) \=\= 0**  
**max\(\) \=\= 2147483647**  
**p\(\) \=\= 1.0000000000**  
**100 个示例的分布：**  
 **0 ::::::::::::::::::::::::::::::**  
 **1 ::::::::::::::::::::::::::::::::::::::**  
 **2 :::::::::::::::::::::::**  
 **3 ::::::::**  
**5 :**  第二次测试：  
  
  **使用 CTRL\-Z 跳过数据输入并使用默认值运行。  输入“mean”分布参数的浮点值（必须大于零）：10**  
**输入示例计数的整数值：100**  
**min\(\) \=\= 0**  
**max\(\) \=\= 2147483647**  
**p\(\) \=\= 10.0000000000**  
**100 个示例的分布：**  
 **3 :**  
 **4 ::**  
 **5 ::**  
 **6 ::::::::**  
 **7 ::::**  
 **8 ::::::::**  
 **9 ::::::::::::::**  
 **10 ::::::::::::**  
 **11 ::::::::::::::::**  
 **12 :::::::::::::::**  
 **13 ::::::::**  
 **14 ::::::**  
 **15 :**  
 **16 ::**  
**17 :**    
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)