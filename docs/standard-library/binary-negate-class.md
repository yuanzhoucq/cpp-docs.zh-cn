---
title: "binary_negate 类 | Microsoft Docs"
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
  - "xfunctional/std::binary_negate"
  - "std::binary_negate"
  - "binary_negate"
  - "std.binary_negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary_negate 类"
ms.assetid: 7b86f02c-af7e-4c7f-9df1-08addae4dd65
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# binary_negate 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供消除一个指定的二元函数的返回值的成员函数的模板选件类。  
  
## 语法  
  
```  
  
   template<class Operation>  
class binary_negate  
   : public binary_function <  
      typename Operation::first_argument_type,  
      typename Operation::second_argument_type,   
      bool>   
{  
public:  
explicit binary_negate(  
   const Operation& _Func  
);  
bool operator()(  
   const typename Operation::first_argument_type& _Left,  
   const typename Operation::second_argument_type& _Right  
) const;  
};  
```  
  
#### 参数  
 `_Func`  
 将二进制对的函数。  
  
 `_Left`  
 将二进制求反的函数的左操作数。  
  
 `_Right`  
 将要求反的二进制函数的正确操作数。  
  
## 返回值  
 二进制函数的求反。  
  
## 备注  
 模板类存储二进制函数对象\_Func 的副本。  它定义了其成员函数 `operator()` 返回\_Func 为 \#\#\#\!*\(\_Left，\_Right\)。*  
  
 直接很少使用 `binary_negate` 构造函数。  帮助程序函数 [not2](../Topic/not2%20Function.md) 通常首选使用 **binary\_negator** 声明和适配器谓词。  
  
## 示例  
  
```  
// functional_binary_negate.cpp  
// compile with: /EHsc  
#define _CRT_RAND_S  
#include <stdlib.h>  
  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <unsigned int> v1;  
   vector <unsigned int>::iterator Iter1;  
  
   unsigned int i;  
   v1.push_back( 6262 );  
   v1.push_back( 6262 );  
   unsigned int randVal = 0;  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      rand_s(&randVal);  
      v1.push_back( randVal );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use default binary predicate less<unsigned int>( )  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order,  
   // use the binary_negate function  
   sort( v1.begin( ), v1.end( ),  
   binary_negate<less<unsigned int> >(less<unsigned int>( ) ) );  
  
   // The helper function not2 could also have been used  
   // in the above line and is usually preferred for convenience  
   // sort( v1.begin( ), v1.end( ), not2(less<unsigned int>( ) ) );  
  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **原始矢量 v1 \= \(6262 6262 2233879413 2621500314 580942933 3715465425 3739828298\)**  
**排序的矢量 v1 \= \(6262 6262 580942933 2233879413 2621500314 3715465425 3739828298\)**  
**将依赖的矢量 v1 \= \(3739828298 3715465425 2621500314 2233879413 580942933 6262 6262\)**   
## 要求  
 **标头：** \<起作用的\>  
  
 std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)