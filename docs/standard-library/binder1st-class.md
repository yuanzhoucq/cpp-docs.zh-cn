---
title: "binder1st 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xfunctional/std::binder1st"
  - "std::binder1st"
  - "binder1st"
  - "std.binder1st"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binder1st 类"
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# binder1st 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类提供一个构造函数，通过将二元函数的第一个参数绑定到指定值，将二元函数对象转换成一个一元函数对象。  
  
## 语法  
  
```  
template<class Operation>  
class binder1st  
   : public unary_function <  
      typename Operation::second_argument_type,  
      typename Operation::result_type>   
  {  
   public:  
   typedef typename Operation::argument_type argument_type;  
   typedef typename Operation::result_type result_type;  
   binder1st(  
      const Operation & _Func,  
      const typename Operation::first_argument_type& _Left  
   );  
   result_type operator()(  
      const argument_type& _Right  
   ) const;  
   result_type operator()(  
      const argument_type& _Right  
   ) const;  
   protected:  
   Operation op;  
   typename Operation::first_argument_type value;  
   };  
```  
  
#### 参数  
 `_Func`  
 要平移的二进制函数对象。一元函数对象。  
  
 `_Left`  
 二进制函数对象第一个参数将绑定的值。  
  
 `_Right`  
 适应的二进制对象相对于第二个参数中的固定值参数的值。  
  
## 返回值  
 产生的二进制对象绑定函数的第一个参数为 `_Left.`值的一元函数对象  
  
## 备注  
 模板类存储二进制函数对象 `_Func` 的副本。**op**和 `_Left` 的副本。**值**。  它定义了其成员函数为 `operator()` 返回 **op**\(**值**，`_Right`\)。  
  
 如果 `_Func` 为 **操作** 类型对象，`c` 是常数，则 [bind1st](../Topic/bind1st%20Function.md) \( `_Func`，`c` \) 的 `binder1st` 类构造函数**操作**\>`binder1st`\<\( `_Func`，`c` \) 等效的、更方便。  
  
## 示例  
  
```  
// functional_binder1st.cpp  
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
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1;  
    result1 = count_if(v1.begin(), v1.end(),  
        binder1st<less<int> >(less<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    // Compare use of binder2nd fixing 2nd argument:  
    // count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(),  
        binder2nd<less<int> >(less<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
  **The vector v1 \= \( 0 5 10 15 20 25 \)**  
**元素的数目。大于 v1 的大于 10 是：3.**  
**元素的数目。v1 的小于 10:2.**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)