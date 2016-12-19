---
title: "logical_and 结构 | Microsoft Docs"
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
  - "std::logical_and"
  - "xfunctional/std::logical_and"
  - "std.logical_and"
  - "logical_and"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "logical_and 类"
  - "logical_and 结构"
ms.assetid: 1a375cc2-0592-4d57-a553-78009c7ad610
caps.latest.revision: 22
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# logical_and 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

预定义在参数上执行与运算\(`operator&&`\)的函数对象。  
  
## 语法  
  
```  
template<class Type = void>  
   struct logical_and : public binary_function<Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator&&  
template<>  
   struct logical_and<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            && std::forward<Type2>(Right));  
   };  
  
```  
  
#### 参数  
 `Type`, `Type1`, `Type2`  
 任何支持`operator&&` 使用指定或者推导类型的操作数的类型。  
  
 `Left`  
 逻辑与操作的左操作。  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type1`的左值和右值引用参数。  
  
 `Right`  
 逻辑与操作的右操作。  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type2`的左值和右值引用参数。  
  
## 返回值  
 `Left` `&&` `Right` 的结果。  拥有通过`operator&&`返回的类型的专有模版确实完美地遵循了结果。  
  
## 备注  
 对于用户定义的类型，而不是短路操作的计算。  所有参数由`operator&&`评价。  
  
## 示例  
  
```  
// functional_logical_and.cpp  
// compile with: /EHsc  
  
#define _CRT_RAND_S  
#include <stdlib.h>  
#include <deque>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   deque<bool> d1, d2, d3( 7 );  
   deque<bool>::iterator iter1, iter2, iter3;  
  
   unsigned int randomValue;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )  
   {  
      if ( rand_s( &randomValue ) == 0 )  
      {  
         d1.push_back((bool)(( randomValue % 2 ) != 0));  
      }  
  
   }  
  
   int j;  
   for ( j = 0 ; j < 7 ; j++ )  
   {  
      if ( rand_s( &randomValue ) == 0 )  
      {  
         d2.push_back((bool)(( randomValue % 2 ) != 0));  
      }  
   }  
  
   cout << boolalpha;    // boolalpha I/O flag on  
  
   cout << "Original deque:\n d1 = ( " ;  
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )  
      cout << *iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "Original deque:\n d2 = ( " ;  
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )  
      cout << *iter2 << " ";  
   cout << ")" << endl;  
  
   // To find element-wise conjunction of the truth values  
   // of d1 & d2, use the logical_and function object  
   transform( d1.begin( ), d1.end( ), d2.begin( ),  
      d3.begin( ), logical_and<bool>( ) );  
   cout << "The deque which is the conjuction of d1 & d2 is:\n d3 = ( " ;  
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )  
      cout << *iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **原始双端队列：**  
 **d1 \= \( true true true true true false false \)**  
**原始双端队列：**  
 **d2 \= \( true false true true false true false \)**  
**与d1 & d2 的双端队列为：**  
 **d3 \= \( true false true true false false false \)**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)