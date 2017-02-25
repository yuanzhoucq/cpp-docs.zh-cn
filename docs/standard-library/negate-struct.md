---
title: "negate 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "negate"
  - "std.negate"
  - "std::negate"
  - "xfunctional/std::negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "negate 结构"
  - "negate 类"
ms.assetid: 8a372686-786e-4262-b37c-ca13dc11e62f
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# negate 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

预定义在参数上执行算数否运算\(一元`operator-`\)的函数对象。  
  
## 语法  
  
```  
template<class Type = void>  
   struct negate : public unary_function<Type, Type>   
   {  
      Type operator()(  
         const Type& Left  
      ) const;  
   };  
  
// specialized transparent functor for unary operator-  
template<>  
   struct negate<void>  
   {  
      template<class Type>  
      auto operator()(Type&& Left) const  
         -> decltype(-std::forward<Type>(Left));  
   };  
  
```  
  
#### 参数  
 `Type`  
 任何支持`operator-` 使用指定或者推导类型的操作数的类型。  
  
 `Left`  
 将取否的操作数。  专有模版确实完美地继承了推断类型`Type`的左值和右值引用参数。  
  
## 返回值  
 `-` `Left.`的结果。拥有通过一元`operator-`返回类型的专有模版确实完美地传递了结果。  
  
## 示例  
  
```  
// functional_negate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <int> v1, v2 ( 8 );  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = -2 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise negatives of the vector v1  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), negate<int>( ) );  
  
   cout << "The negated elements of the vector = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **The vector v1 \= \( \-10 \-5 0 5 10 15 20 25 \)**  
**The negated elements of the vector \= \( 10 5 0 \-5 \-10 \-15 \-20 \-25 \)**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)