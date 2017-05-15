---
title: "discrete_distribution 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- discrete_distribution
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
- random/std::discrete_distribution::param_type
dev_langs:
- C++
helpviewer_keywords:
- discrete_distribution class
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 270dd20a29333c64526c103c3eabe847c1c6e3c9
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="discretedistribution-class"></a>discrete_distribution 类
生成包含以等概率分布在每个区间中的等宽区间的离散型整数分布。  
  
## <a name="syntax"></a>语法  
  
```  
template<class IntType = int>
class discrete_distribution  
   {  
public:  
   // types  
   typedef IntType result_type;  
   struct param_type;  
   
   // constructor and reset functions  
   discrete_distribution();
   template <class InputIterator>  
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>  
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions  
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```   
#### <a name="parameters"></a>参数  
*IntType*  
 整数结果类型，默认为 `int`。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>备注  
 此示例分布包含以等概率分布在每个区间中的等宽区间。 有关其他示例分布的信息，请参阅 [piecewise_linear_distribution 类](../standard-library/piecewise-linear-distribution-class.md)和 [piecewise_constant_distribution 类](../standard-library/piecewise-constant-distribution-class.md)。  
  
 下表链接到有关各个成员的文章：  
  
|||  
|-|-|  
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|  
|`discrete_distribution::operator()`|[param_type](#param_type)|  
  
 属性函数 `vector<double> probabilities()` 将返回每个生成的整数的各自概率。  
  
 有关分布类及其成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter an integer value for the sample count: 100  
min() == 0  
max() == 4  
probabilities (value: probability):  
          0:   0.0666666667  
          1:   0.1333333333  
          2:   0.2000000000  
          3:   0.2666666667  
          4:   0.3333333333  
  
Distribution for 100 samples:  
    0 :::  
    1 ::::::::::::::  
    2 ::::::::::::::::::  
    3 :::::::::::::::::::::::::::::  
    4 ::::::::::::::::::::::::::::::::::::    
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<random>  
  
 **命名空间：** std  
  
##  <a name="discrete_distribution"></a>  discrete_distribution::discrete_distribution  
 构造分布。  
  
```  
// default constructor  
discrete_distribution();  
  
// construct using a range of weights, [firstW, lastW)  
template <class InputIterator>  
discrete_distribution(InputIterator firstW, InputIterator lastW);  
  
// construct using an initializer list for range of weights  
discrete_distribution(initializer_list<double> weightlist);  
  
// construct using unary operation function  
template <class UnaryOperation>  
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);  
  
// construct from an existing param_type structure  
explicit discrete_distribution(const param_type& parm);  
```  
  
### <a name="parameters"></a>参数  
*firstW*  
 从中构造分布的列表中的第一个迭代器。  
  
*lastW*  
 从中构造分布的列表中的最后一个迭代器（不包含此迭代器，因为迭代器末尾使用空元素）。  
  
*weightlist*  
 从中构造分布的 [initializer_list](../cpp/initializers.md)。  
  
*count*  
 分布范围中的元素数。 如果 `count==0`，则等效于默认构造函数（始终生成零）。  
  
*low*  
 分布范围中的最低值。  
  
*high*  
 分布范围中的最高值。  
  
*weightfunc*  
 表示分布的概率函数的对象。 参数和返回值都必须可转换为 `double`。  
  
*parm*  
 用于构造分布的 `param_type` 结构。  
  
### <a name="remarks"></a>备注  
默认构造函数构造其存储的概率值仅具有附带值 1 的一个元素的对象。 这将产生始终生成零的分布。  
  
包含 *firstW* 和 *lastW* 参数的迭代器范围构造函数使用通过区间序列 [*firstW*, *lastW*) 的迭代器中获取的加权值构造分布对象。  
  
包含 *weightlist* 参数的初始化表达式列表构造函数使用初始化表达式列表 *weightlist* 中的加权值构造分步对象。  
  
包含 *count*、*low*、*high*、和 *weightfunc* 参数的构造函数基于以下规则构造初始化的分布对象：  
-  如果 *count* < 1，则 **n** = 1，并且等效于默认构造函数（始终生成零）。  
-  如果 *count* > 0，则 **n** = *count*。 Provided **d** = (*high* - *low*) / **n** is greater than zero, using **d** uniform subranges, each weight is assigned as follows: `weight[k] = weightfunc(x)`, where **x** = *low* + **k** * **d** + **d** / 2, for **k** = 0, ..., **n** - 1.  
  
包含 `param_type` 参数 *parm* 的构造函数将 *parm* 用作存储的参数结构来构造分布对象。  
  
##  <a name="param_type"></a>  discrete_distribution::param_type  
 存储分布的所有参数。  
  
```  
struct param_type {  
   typedef discrete_distribution<result_type> distribution_type;  
   param_type();

   // construct using a range of weights, [firstW, lastW)  
   template <class InputIterator>  
   param_type(InputIterator firstW, InputIterator lastW);  
  
   // construct using an initializer list for range of weights  
   param_type(initializer_list<double> weightlist);  
  
   // construct using unary operation function  
   template <class UnaryOperation>  
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;
   
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```   
### <a name="parameters"></a>参数  
*firstW*  
 从中构造分布的列表中的第一个迭代器。  
  
*lastW*  
 从中构造分布的列表中的最后一个迭代器（不包含此迭代器，因为迭代器末尾使用空元素）。  
  
*weightlist*  
 从中构造分布的 [initializer_list](../cpp/initializers.md)。  
  
*count*  
 分布范围中的元素数。 如果 *count* 为 0，则等效于默认构造函数（始终生成零）。  
  
*low*  
 分布范围中的最低值。  
  
*high*  
 分布范围中的最高值。  
  
*weightfunc*  
 表示分布的概率函数的对象。 参数和返回值都必须可转换为 `double`。  
  
*right*  
 要与它进行比较的 `param_type` 对象。  
  
### <a name="remarks"></a>备注  
 此参数包可传递给 `operator()` 以生成返回值。  
  
## <a name="see-also"></a>另请参阅  
 [\<random>](../standard-library/random.md)






