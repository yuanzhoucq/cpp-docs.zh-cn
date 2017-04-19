---
title: "logical_or 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- logical_or
- xfunctional/std::logical_or
dev_langs:
- C++
helpviewer_keywords:
- logical_or class
- logical_or struct
ms.assetid: ec8143f8-5755-4e7b-8025-507fb6bf6911
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 4928eb5d79877dd4d1e2c1a1c0f25dbc29e4ec1b
ms.lasthandoff: 02/24/2017

---
# <a name="logicalor-struct"></a>logical_or 结构
对其自变量执行逻辑析取运算 (`operator||`) 的预定义函数对象。  
  
## <a name="syntax"></a>语法  
  
```
template <class Type = void>
struct logical_or : public binary_function<Type, Type, bool>  
{
    bool operator()(const Type& Left, const Type& Right) const;
 };

// specialized transparent functor for operator||
template <>
struct logical_or<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) || std::forward<U>(Right));
 };
```  
  
#### <a name="parameters"></a>参数  
 `Type`, `T`, `U`  
 支持 `operator||` 接受指定或推断类型的操作数的任何类型。  
  
 `Left`  
 逻辑析取运算的左操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `T` 的左值和右值引用参数。  
  
 `Right`  
 逻辑析取运算的右操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `U` 的左值和右值引用参数。  
  
## <a name="return-value"></a>返回值  
 `Left``||``Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator||` 返回的类型。  
  
## <a name="remarks"></a>备注  
 对于用户定义类型，没有任何短路操作数计算。 这两个参数都通过 `operator||` 计算。  
  
## <a name="example"></a>示例  
  
```cpp  
// functional_logical_or.cpp  
// compile with: /EHsc  
#include <deque>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   deque <bool> d1, d2, d3( 7 );  
   deque <bool>::iterator iter1, iter2, iter3;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )  
   {  
      d1.push_back((bool)((rand() % 2) != 0));  
   }  
  
   int j;  
   for ( j = 0 ; j < 7 ; j++ )  
   {  
      d2.push_back((bool)((rand() % 2) != 0));  
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
  
   // To find element-wise disjunction of the truth values  
   // of d1 & d2, use the logical_or function object  
   transform( d1.begin( ), d1.end( ), d2.begin( ),  
      d3.begin( ), logical_or<bool>( ) );  
   cout << "The deque which is the disjuction of d1 & d2 is:\n d3 = ( " ;  
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )  
      cout << *iter3 << " ";  
   cout << ")" << endl;  
}  
\* Output:   
Original deque:  
 d1 = ( true true false false true false false )  
Original deque:  
 d2 = ( false false false true true true true )  
The deque which is the disjuction of d1 & d2 is:  
 d3 = ( true true false true true true true )  
*\  
  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




