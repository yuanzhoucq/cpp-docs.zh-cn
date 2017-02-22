---
title: "discrete_distribution 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "random/std::tr1::discrete_distribution"
  - "std::tr1::discrete_distribution"
  - "tr1.discrete_distribution"
  - "std.tr1.discrete_distribution"
  - "discrete_distribution"
  - "tr1::discrete_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "discrete_distribution 类"
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# discrete_distribution 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成包含以等概率分布在每个区间中的等宽区间的离散型整数分布。  
  
## 语法  
  
```  
template<class IntType = int> class discrete_distribution { public:     // types     typedef IntType result_type;     struct param_type;     // constructor and reset functions     discrete_distribution();     template<class InputIterator>     discrete_distribution(InputIterator firstW, InputIterator lastW);     discrete_distribution(initializer_list<double> weightlist);     template<class UnaryOperation>     discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);     explicit discrete_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     vector<double> probabilities() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 参数  
 `IntType`  
 整数结果类型，默认为 `int`。  有关可能的类型，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 此示例分布包含以等概率分布在每个区间中的等宽区间。  有关其他示例分布的信息，请参阅 [piecewise\_linear\_distribution 类](../standard-library/piecewise-linear-distribution-class.md) 和 [piecewise\_constant\_distribution 类](../standard-library/piecewise-constant-distribution-class.md)。  
  
 下表链接到有关各个成员的文章：  
  
|||  
|-|-|  
|[discrete\_distribution::discrete\_distribution](../Topic/discrete_distribution::discrete_distribution.md)|`discrete_distribution::param`|  
|`discrete_distribution::operator()`|[discrete\_distribution::param\_type](../Topic/discrete_distribution::param_type.md)|  
  
 属性函数 `vector<double> probabilities()` 将返回每个生成的整数的各自概率。  
  
 有关分布类及其成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 示例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
using namespace std;  
  
void test(const int s) {  
  
    // uncomment to use a non-deterministic generator  
    // random_device rd;  
    // mt19937 gen(rd());  
    mt19937 gen(1701);  
  
    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "probabilities (value: probability):" << endl;  
    vector<double> p = distr.probabilities();  
    int counter = 0;  
    for (const auto& n : p) {  
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;  
        ++counter;  
    }  
    cout << endl;  
  
    // generate the distribution as a histogram  
    map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    cout << "Distribution for " << s << " samples:" << endl;  
    for (const auto& elem : histogram) {  
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;  
    }  
    cout << endl;  
}  
  
int main()  
{  
    int samples = 100;  
  
    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;  
    cout << "Enter an integer value for the sample count: ";  
    cin >> samples;  
  
    test(samples);  
}  
  
```  
  
## 输出  
  **使用 CTRL\-Z 跳过数据输入并使用默认值运行。  输入示例计数的整数值：100**  
**min\(\) \=\= 0**  
**max\(\) \=\= 4**  
**概率（值：概率）：**  
 **0:   0.0666666667**  
 **1:   0.1333333333**  
 **2:   0.2000000000**  
 **3:   0.2666666667**  
 **4:   0.3333333333**  
**100 个示例的分布：**  
 **0 :::::**  
 **1 ::::::::::::::**  
 **2 :::::::::::::::::**  
 **3 ::::::::::::::::::::::::::::::**  
**4 ::::::::::::::::::::::::::::::::::**    
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)