---
title: "unary_negate 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "unary_negate"
  - "std::unary_negate"
  - "std.unary_negate"
  - "xfunctional/std::unary_negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unary_negate 类"
ms.assetid: e3b86eec-3205-49b9-ab83-f55225af4e0c
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# unary_negate 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供消除一个指定的一元函数的返回值的成员函数的模板选件类。  
  
## 语法  
  
```  
  
   template<class Predicate>  
class unary_negate  
   : public unary_function<  
      typename Predicate::argument_type,  
      bool>   
{  
public:  
explicit unary_negate(  
   const Predicate& _Func  
);  
bool operator()(  
   const typename Predicate::argument_type& _Left ) const;  
};  
```  
  
#### 参数  
 `_Func`  
 将一元求反的函数。  
  
 `_Left`  
 将一元求反的函数的操作数。  
  
## 返回值  
 一元求反的函数。  
  
## 备注  
 模板类存储一元函数对象\_Func 的副本*。*它定义了其成员函数 `operator()` 返回\_Func 为 \#\#\#\!*\(\_Left\)。*  
  
 直接很少使用 `unary_negate` 构造函数。  帮助程序函数 [not1](../Topic/not1%20Function.md) 提供了一种简便的方式声明和使用 **unary\_negator** 适配器谓词。  
  
## 示例  
  
```  
// functional_unary_negate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 7; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result1;  
    // Count the elements greater than 10  
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    vector<int>::iterator::difference_type result2;  
    // Use the negator to count the elements less than or equal to 10  
    result2 = count_if(v1.begin(), v1.end(),  
        unary_negate<binder2nd <greater<int> > >(bind2nd(greater<int>(),10)));  
  
    // The following helper function not1 also works for the above line  
    // not1(bind2nd(greater<int>(), 10)));  
  
    cout << "The number of elements in v1 not greater than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
  **矢量 v1 \= \(0 5 10 15 20 25 30 35\)**  
**元素的数目。大于 v1 的大于 10 是：5.**  
**元素的数目。不大于 v1 的大于 10 是：3.**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)