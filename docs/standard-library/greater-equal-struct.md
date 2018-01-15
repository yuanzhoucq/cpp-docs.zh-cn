---
title: "greater_equal 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::greater_equal
dev_langs: C++
helpviewer_keywords:
- greater_equal struct
- greater_equal function
ms.assetid: a8ba911b-7af8-4653-b972-d8618f4df7d5
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e6fbffd75fedd267f8034e919bedefd79a63838e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="greaterequal-struct"></a>greater_equal 结构
一个对其参数执行大于或等于运算 ( `operator>=`) 的二元谓词。  
  
## <a name="syntax"></a>语法  
  
```
template <class Type = void>
struct greater_equal : public binary_function <Type, Type, bool>  
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator>=
template <>
struct greater_equal<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left)>= std::forward<U>(Right));
 };
```  
  
#### <a name="parameters"></a>参数  
 `Type`, `T`, `U`  
 支持 `operator>=` 接受指定或推断类型的操作数的任何类型。  
  
 `Left`  
 大于或等于运算的左操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `T` 的左值和右值引用参数。  
  
 `Right`  
 大于或等于运算的右操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `U` 的左值和右值引用参数。  
  
## <a name="return-value"></a>返回值  
 `Left >= Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator>=` 返回的类型。  
  
## <a name="remarks"></a>备注  
 二元谓词 `greater_equal`< `Type`> 向等价类提供类型为 `Type` 的一组元素值的严格弱排序（在且仅在此类型满足如此进行排序的标准数学要求时）。 任何指针类型的专用化都会产生元素的全序，所有不同值的元素都会相对于彼此进行排序。  
  
## <a name="example"></a>示例  
  
```cpp  
// functional_greater_equal.cpp  
// compile with: /EHsc  
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
  
   int i;  
   v1.push_back( 6262 );  
   v1.push_back( 6262 );  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      v1.push_back( rand( ) );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use default binary predicate less<int>( )  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order,   
   // specify binary predicate greater_equal<int>( )  
   sort( v1.begin( ), v1.end( ), greater_equal<int>( ) );  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
## <a name="output"></a>输出  
  
```
Original vector v1 = (6262 6262 41 18467 6334 26500 19169)
Sorted vector v1 = (41 6262 6262 6334 18467 19169 26500)
Resorted vector v1 = (26500 19169 18467 6334 6262 6262 41)
```  
  
## <a name="requirements"></a>惠?  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)



