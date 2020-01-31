---
title: logical_and 结构
ms.date: 11/04/2016
f1_keywords:
- functional/std::logical_and
helpviewer_keywords:
- logical_and class
- logical_and struct
ms.assetid: 1a375cc2-0592-4d57-a553-78009c7ad610
ms.openlocfilehash: cc75c93d5173ceb7fa12b9722a797499b4225a53
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821611"
---
# <a name="logical_and-struct"></a>logical_and 结构

一个预定义的函数对象，它对其参数执行逻辑与运算（`operator&&`）。

## <a name="syntax"></a>语法

```
template <class Type = void>
struct logical_and : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator&&
template <>
struct logical_and<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) && std::forward<U>(Right));
};
```

### <a name="parameters"></a>参数

*Type*、 *T*、 *U*\
支持 `operator&&` 接受指定或推断类型的操作数的任何类型。

*左*\
逻辑连接运算的左操作数。 非专用化的模板*采用类型为*的左值引用参数。 专用模板完全转发推断类型*T*的左值和右值引用参数。

*Right*\
逻辑连接运算的右操作数。 非专用化的模板*采用类型为*的左值引用参数。 专用模板完全转发推断类型*U*的左值和右值引用参数。

## <a name="return-value"></a>返回值

`Left && Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator&&` 返回的类型。

## <a name="remarks"></a>备注

对于用户定义类型，没有任何短路操作数计算。 这两个参数都通过 `operator&&` 计算。

## <a name="example"></a>示例

```cpp
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
   cout << "The deque which is the conjunction of d1 & d2 is:\n d3 = ( " ;
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )
      cout << *iter3 << " ";
   cout << ")" << endl;
}
```

```Output
Original deque:
d1 = ( true true true true true false false )
Original deque:
d2 = ( true false true true false true false )
The deque which is the conjunction of d1 & d2 is:
d3 = ( true false true true false false false )
```
