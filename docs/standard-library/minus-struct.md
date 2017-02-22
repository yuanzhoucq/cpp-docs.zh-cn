---
title: "minus 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "minus"
  - "std.minus"
  - "std::minus"
  - "xfunctional/std::minus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "minus 结构"
  - "minus 类"
ms.assetid: 7bce784e-2be6-413a-b516-004e9ecb2a39
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# minus 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

预定义在参数上执行减运算 \(二元 `operator-`\)的函数对象。  
  
## 语法  
  
```  
template<class Type = void>  
   struct minus : public binary_function <Type, Type, Type>   
   {  
      Type operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator-  
template<>  
   struct minus<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            - std::forward<Type2>(Right));  
   };  
  
```  
  
#### 参数  
 `Type`, `Type1`, `Type2`  
 支持二进制`operator-` 使用指定或者推导类型的操作数的类型。  
  
 `Left`  
 操作符的左操作数。  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type1`的左值和右值引用参数。  
  
 `Right`  
 操作符的右操作数。  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type2`的左值和右值引用参数。  
  
## 返回值  
 `Left` `-` `Right` 的结果。  拥有通过`operator-`返回的类型的专有模版确实完美地遵循了结果。  
  
## 示例  
  
```  
// functional_minus.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <int> v1, v2, v3 ( 6 );  
   vector <int>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 4 * i + 1);  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j++ )  
   {  
      v2.push_back( 3 * j - 1);  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise diference of the elements of v1 & v2  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      minus<int>( ) );  
  
   cout << "The element-wise differences between v1 and v2 are: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **The vector v1 \= \( 1 5 9 13 17 21 \)**  
**The vector v2 \= \( \-1 2 5 8 11 14 \)**  
**The element\-wise differences between v1 and v2 are: \( 2 3 4 5 6 7 \)**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)