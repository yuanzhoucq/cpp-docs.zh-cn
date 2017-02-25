---
title: "not_equal_to 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.not_equal_to"
  - "std::not_equal_to"
  - "not_equal_to"
  - "xfunctional/std::not_equal_to"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "not_equal_to 函数"
  - "not_equal_to 结构"
ms.assetid: 333fce09-4f51-44e0-ba26-533bccffd485
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# not_equal_to 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

二进制预先表明了进行参数的等于操作 \(`operator!=`\)。  
  
## 语法  
  
```  
template<class Type = void>  
   struct not_equal_to : public binary_function<Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator!=  
template<>  
   struct not_equal_to<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
      -> decltype(std::forward<Type1>(Left)  
         != std::forward<Type2>(Right));  
   };  
  
```  
  
#### 参数  
 `Type`, `Type1`, `Type2`  
 任何支持`operator!=` 使用指定或者推导类型的操作数的类型。  
  
 `Left`  
 不等于运算的左侧操作。  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type1`的左值和右值引用参数。  
  
 `Right`  
 不等运算的右侧操作。  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type2`的左值和右值引用参数。  
  
## 返回值  
 `Left` `!=` `Right` 的结果。  拥有通过`operator!=`返回的类型的专有模版确实完美地遵循了结果。  
  
## 备注  
 `Type`类型的对象必须相等。  这需要对象的集合中定义的`operator!=`满足等价关系的数学性质。  所有内置数字和指针类型都满足此要求。  
  
## 示例  
  
```  
// functional_not_equal_to.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 (6);  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i+=2 )  
   {  
      v1.push_back( 2.0 *i );  
      v1.push_back( 2.0 * i + 1.0 );  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j+=2 )  
   {  
      v2.push_back( - 2.0 * j );  
      v2.push_back( 2.0 * j + 1.0 );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Testing for the element-wise equality between v1 & v2  
   transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ),   
      not_equal_to<double>( ) );  
  
   cout << "The result of the element-wise not_equal_to comparsion\n"  
      << "between v1 & v2 is: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **The vector v1 \= \( 0 1 4 5 8 9 \)**  
**The vector v2 \= \( \-0 1 \-4 5 \-8 9 \)**  
**The result of the element\-wise not\_equal\_to comparsion**  
**between v1 & v2 is: \( 0 0 1 0 1 0 \)**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [标准模板库](../misc/standard-template-library.md)