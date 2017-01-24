---
title: "seed_seq 类 | Microsoft Docs"
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
  - "tr1::seed_seq"
  - "std::tr1::seed_seq"
  - "tr1.seed_seq"
  - "seed_seq"
  - "std.tr1.seed_seq"
  - "random/std::tr1::seed_seq"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "seed_seq 类"
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
caps.latest.revision: 19
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# seed_seq 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存储可以为随机数引擎提供随机化种子的无符号整数值的矢量。  
  
## 语法  
  
```  
class seed_seq  
{  
public:  
    // types  
    typedef unsigned int result_type;  
  
    // constructors  
    seed_seq();  
  
    template<class T>  
    seed_seq(initializer_list<T> initlist);  
  
    template<class InputIterator>  
    seed_seq(InputIterator begin, InputIterator end);  
  
    // generating functions  
    template<class RandomAccessIterator>  
    void generate(RandomAccessIterator begin, RandomAccessIterator end);  
  
    // property functions  
    size_t size() const;  
  
    template<class OutputIterator>  
    void param(OutputIterator dest) const;  
  
    // no copy functions  
    seed_seq(const seed_seq&) = delete;  
    void operator=(const seed_seq&) = delete;  
};  
```  
  
## 类型  
 `typedef unsigned int result_type;`   
种子序列的元素的类型。 一个 32 位无符号的整数类型。  
  
## 构造函数  
 `seed_seq();`   
默认构造函数，具有空的内部序列进行初始化。  
  
 `template<class T>`   
 `seed_seq(initializer_list<T> initlist);`   
使用 `initlist` 设置内部序列。  
`T` 必须是整数类型。  
  
 `template<class InputIterator>`   
 `seed_seq(InputIterator begin, InputIterator end);`   
初始化内部序列使用提供的输入迭代器范围中的所有元素。  
`iterator_traits<InputIterator>::value_type` 必须是整数类型。  
  
## 成员  
  
### 生成函数  
 `template<class RandomAccessIterator> void generate(RandomAccessIterator begin, RandomAccessIterator end);`   
填充使用内部算法所提供序列的元素。 此算法受的内部序列 `seed_seq` 已初始化。  
不执行任何操作如果 `begin == end`。  
  
### 属性函数  
 `size_t size() const;`   
返回中的元素数 `seed_seq`。  
  
 `template<class OutputIterator> void param(OutputIterator dest) const;`   
将内部序列复制到输出迭代器 `dest`。  
  
## 示例  
 以下代码示例练习了三种构造函数，并且从分配到数组时生成的 `seed_seq` 实例中生成输出。 有关使用示例， `seed_seq` 与随机数生成器，请参阅 [\<random\>](../standard-library/random.md)。  
  
```cpp  
#include <iostream>  
#include <random>  
#include <string>  
#include <array>  
  
using namespace std;  
  
void test(const seed_seq& sseq) {  
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;  
  
    cout << "seed_seq::param(): ";  
    ostream_iterator<unsigned int> out(cout, " ");  
    sseq.param(out);  
    cout << endl;  
  
    cout << "Generating a sequence of 5 elements into an array: " << endl;  
    array<unsigned int, 5> seq;  
    sseq.generate(seq.begin(), seq.end());  
    for (unsigned x : seq) { cout << x << endl; }  
}  
  
int main()  
{  
    seed_seq seed1;  
    test(seed1);  
  
    seed_seq seed2 = { 1701, 1729, 1791 };  
    test(seed2);  
  
    string sstr = "A B C D"; // seed string  
    seed_seq seed3(sstr.begin(), sstr.end());  
    test(seed3);  
}  
```  
  
## 输出  
  
```Output  
  
seed_seq::size(): 0 seed_seq::param(): 5 个元素的序列转换为数组生成︰ 505382999 163489202 3932644188 763126080 73937346 seed_seq::size(): 3 seed_seq::param(): 1701年 1729年 1791年 5 个元素的序列转换为数组生成︰ 1730669648 1954224479 2809786021 1172893117 2393473414 seed_seq::size(): 7 seed_seq::param(): 65 32 66 32 67 32 68 生成 5 个元素的序列转换为数组: 3139879222 3775111734 1084804564 2485037668 1985355432  
```  
  
## 备注  
 此类的成员函数不引发异常。  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)