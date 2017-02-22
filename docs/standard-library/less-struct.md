---
title: "less 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::less"
  - "std.less"
  - "less"
  - "xfunctional/std::less"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "less 结构"
  - "less 函数"
ms.assetid: 39349da3-11cd-4774-b2cc-b46af5aae5d7
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# less 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

二进制预先表明了进行参数的小于操作 \(`operator<`\)。  
  
## 语法  
  
```  
template<class Type = void>  
   struct less : public binary_function <Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator<  
template<>  
   struct less<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            < std::forward<Type2>(Right));  
   };  
  
```  
  
#### 参数  
 `Type`, `Type1`, `Type2`  
 任何支持`operator<` 使用指定或者推导类型的操作数的类型。  
  
 `Left`  
 小于运算的左侧操作数。  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type1`的左值和右值引用参数。  
  
 `Right`  
 小于运算的右侧操作数。  未指定的模版需要类型`Type`的左值引用参数。  专有模版确实完美地继承了推断类型`Type2`的左值和右值引用参数。  
  
## 返回值  
 `Left` `<` `Right` 的结果。  拥有通过`operator<`返回的类型的专有模版确实完美地遵循了结果。  
  
## 备注  
 二进制预测`less`\<`Type`\> 提供了一个严格的根据等价值元素类型`Type`值排序，当且仅当类型满足如此排序的标准数学要求。  任何指针类型的专用化服从元素排序，不同值的所有元素排序互相遵守。  
  
## 示例  
  
```  
// functional_less.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
struct MyStruct {  
   MyStruct(int i) : m_i(i){}  
  
   bool operator < (const MyStruct & rhs) const {  
      return m_i < rhs.m_i;  
   }     
  
   int m_i;  
};  
  
int main() {  
   using namespace std;  
   vector <MyStruct> v1;  
   vector <MyStruct>::iterator Iter1;  
   vector <MyStruct>::reverse_iterator rIter1;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )       
       v1.push_back( MyStruct(rand()));  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )   
cout << Iter1->m_i << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   sort( v1.begin( ), v1.end( ), less<MyStruct>());  
  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )   
cout << Iter1->m_i << " ";  
   cout << ")" << endl;  
 }  
```  
  
## Output  
  
```  
Original vector v1 = ( 41 18467 6334 26500 19169 15724 11478 )  
Sorted vector v1 = ( 41 6334 11478 15724 18467 19169 26500 )  
```  
  
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [标准模板库](../misc/standard-template-library.md)