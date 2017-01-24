---
title: "logical_not 结构 | Microsoft Docs"
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
  - "std.logical_not"
  - "logical_not"
  - "xfunctional/std::logical_not"
  - "std::logical_not"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "logical_not 类"
  - "logical_not 结构"
ms.assetid: 892db678-31da-4540-974b-17b05efc0849
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# logical_not 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

预定义在参数上执行逻辑非操作 运算\(`operator!`\)的函数对象。  
  
## 语法  
  
```  
template<class Type = void>  
   struct logical_not : public unary_function<Type, bool>   
   {  
      bool operator()(  
         const Type& Left  
      ) const;  
   };  
  
// specialized transparent functor for operator!  
template<>  
   struct logical_not<void>  
   {  
      template<class Type>  
      auto operator()(Type&& Left) const  
         -> decltype(!std::forward<Type>(Left));  
   };  
  
```  
  
#### 参数  
 `Type`  
 任何支持`operator!` 使用指定或者推导类型的操作数的类型。  
  
 `Left`  
 逻辑"非"运算的操作数。  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type`的左值和右值引用参数。  
  
## 返回值  
 `!` `Left`的结果。  拥有通过`operator!`返回的类型的专有模版确实完美地遵循了结果。  
  
## 示例  
  
```  
// functional_logical_not.cpp  
// compile with: /EHsc  
#include <deque>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   deque<bool> d1, d2 ( 7 );  
   deque<bool>::iterator iter1, iter2;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )  
   {  
      d1.push_back((bool)((i % 2) != 0));  
   }  
  
   cout << boolalpha;    // boolalpha I/O flag on  
  
   cout << "Original deque:\n d1 = ( " ;  
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )  
      cout << *iter1 << " ";  
   cout << ")" << endl;  
  
   // To flip all the truth values of the elements,  
   // use the logical_not function object  
   transform( d1.begin( ), d1.end( ), d2.begin( ),logical_not<bool>( ) );  
   cout << "The deque with its values negated is:\n d2 = ( " ;  
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )  
      cout << *iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **原始双端队列：**  
 **d1 \= \( false true false true false true false \)**  
**The deque with its values negated is:**  
 **d2 \= \( true false true false true false true \)**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)