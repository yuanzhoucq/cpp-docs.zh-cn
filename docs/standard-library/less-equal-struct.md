---
title: "less_equal 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::less_equal"
  - "xfunctional/std::less_equal"
  - "std.less_equal"
  - "less_equal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "less_equal 函数"
  - "less_equal 结构"
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# less_equal 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

二进制预先表明了进行参数的小于等于操作 \(`operator<=`\)。  
  
## 语法  
  
```  
template<class Type = void>  
   struct less_equal : public binary_function <Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator<=  
template<>  
   struct less_equal<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            <= std::forward<Type2>(Right));  
   };  
  
```  
  
#### 参数  
 `Type`, `Type1`, `Type2`  
 任何支持`operator<=` 使用指定或者推导类型的操作数的类型。  
  
 `Left`  
 在小于或等于操作左边的操作数  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type1`的左值和右值引用参数。  
  
 `Right`  
 在小于或等于操作右边的操作数  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type2`的左值和右值引用参数。  
  
## 返回值  
 `Left` `<=` `Right` 的结果。  拥有通过`operator<=`返回的类型的专有模版确实完美地遵循了结果。  
  
## 备注  
 二进制预测`less_equal`\<`Type`\> 提供了一个严格的根据等价值元素类型`Type`值排序，当且仅当类型满足如此排序的标准数学要求。  任何指针类型的专用化服从元素排序，不同值的所有元素排序互相遵守。  
  
## 示例  
  
```  
// functional_less_equal.cpp  
// compile with: /EHsc  
#define _CRT_RAND_S  
#include <stdlib.h>  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <cstdlib>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
   vector <int>::reverse_iterator rIter1;  
   unsigned int randomNumber;  
  
   int i;  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      if ( rand_s( &randomNumber ) == 0 )  
      {  
         // Convert the random number to be between 1 - 50000  
         // This is done for readability purposes  
         randomNumber = ( unsigned int) ((double)randomNumber /   
            (double) UINT_MAX * 50000) + 1;  
  
         v1.push_back( randomNumber );  
      }  
   }  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      v1.push_back( 2836 );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use the binary predicate less_equal<int>( )  
   sort( v1.begin( ), v1.end( ), less_equal<int>( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
## 示例输出  
  
```  
Original vector v1 = ( 31247 37154 48755 15251 6205 2836 2836 2836 )  
Sorted vector v1 = ( 2836 2836 2836 6205 15251 31247 37154 48755 )  
```  
  
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [标准模板库](../misc/standard-template-library.md)