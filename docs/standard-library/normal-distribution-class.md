---
title: "normal_distribution 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1::normal_distribution"
  - "normal_distribution"
  - "std::tr1::normal_distribution"
  - "random/std::tr1::normal_distribution"
  - "std.tr1.normal_distribution"
  - "tr1.normal_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "normal_distribution 类"
  - "normal_distribution 类 [TR1]"
ms.assetid: bf92cdbd-bc72-4d4a-b588-173d748f0d7d
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# normal_distribution 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成正态分布。  
  
## 语法  
  
```  
template<class RealType = double> class normal_distribution { public:     // types     typedef RealType result_type;     struct param_type;     // constructors and reset functions     explicit normal_distribution(RealType mean = 0.0, RealType stddev = 1.0);     explicit normal_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     RealType mean() const;     RealType stddev() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 参数  
 `RealType`  
 浮点结果类型，默认为 `double`。  有关可能的类型，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 如果未根据正态分布提供和分布任何类型，则模板类将描述产生用户指定的整型值或 `double` 型值的分布。  下表链接到有关各个成员的文章。  
  
||||  
|-|-|-|  
|[normal\_distribution::normal\_distribution](../Topic/normal_distribution::normal_distribution.md)|`normal_distribution::mean`|`normal_distribution::param`|  
|`normal_distribution::operator()`|`normal_distribution::stddev`|[normal\_distribution::param\_type](../Topic/normal_distribution::param_type.md)|  
  
 属性函数 `mean()` 和 `stddev()` 将分别返回存储的分布参数 `mean` 和 `stddev` 的值。  
  
 有关分布类及其成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
 有关正态分布的详细信息，请参阅 Wolfram MathWorld 文章[正态分布](http://go.microsoft.com/fwlink/?LinkId=400924)。  
  
## 示例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
using namespace std;  
  
void test(const double m, const double s, const int samples) {  
  
    // uncomment to use a non-deterministic seed  
    //    random_device gen;  
    //    mt19937 gen(rd());  
    mt19937 gen(1701);  
  
    normal_distribution<> distr(m, s);  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.mean() << endl;  
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.stddev() << endl;  
  
    // generate the distribution as a histogram  
    map<double, int> histogram;  
    for (int i = 0; i < samples; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    cout << "Distribution for " << samples << " samples:" << endl;  
    int counter = 0;  
    for (const auto& elem : histogram) {  
        cout << fixed << setw(11) << ++counter << ": "  
            << setw(14) << setprecision(10) << elem.first << endl;  
    }  
    cout << endl;  
}  
  
int main()  
{  
    double m_dist = 1;  
    double s_dist = 1;  
    int samples = 10;  
  
    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;  
    cout << "Enter a floating point value for the 'mean' distribution parameter: ";  
    cin >> m_dist;  
    cout << "Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): ";  
    cin >> s_dist;  
    cout << "Enter an integer value for the sample count: ";  
    cin >> samples;  
  
    test(m_dist, s_dist, samples);  
}  
  
```  
  
## 输出  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'mean' distribution parameter: 0  
Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
  
min() == -1.79769e+308  
max() == 1.79769e+308  
m() == 0.0000000000  
s() == 1.0000000000  
Distribution for 10 samples:  
          1:  -0.8845823965  
          2:  -0.1995761116  
          3:  -0.1162665130  
          4:  -0.0685154932  
          5:   0.0403741461  
          6:   0.1591327792  
          7:   1.0414389924  
          8:   1.5876269426  
          9:   1.6362637713  
         10:   2.7821317338  
```  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)