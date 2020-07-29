---
title: pair 结构
ms.date: 11/04/2016
f1_keywords:
- utility/std::pair
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
ms.openlocfilehash: 504bd4fad47d85b0f92603b2cf77a6fca1e9876b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233010"
---
# <a name="pair-structure"></a>pair 结构

一种结构，该结构提供了将两个对象视为单个对象的的功能。

## <a name="syntax"></a>语法

```cpp
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    pair(const pair&) = default;
    pair(pair&&) = default;
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);

    template <class... Args1, class... Args2>
    pair(piecewise_construct_t, tuple<Args1...> first_args, tuple<Args2...> second_args);

    pair& operator=(const pair& p);
    template<class U1, class U2> pair& operator=(const pair<U1, U2>& p);
    pair& operator=(pair&& p) noexcept(see below );
    template<class U1, class U2> pair& operator=(pair<U1, U2>&& p);

    void swap(pair& p) noexcept(see below );
};

template<class T1, class T2>
    pair(T1, T2) -> pair<T1, T2>;
```

### <a name="parameters"></a>参数

*Val1*\
初始化 `pair` 的第一个元素的值。

*Val2*\
初始化 `pair` 的第二个元素的值。

*然后*\
一个对，其值将用于初始化另一对的元素。

## <a name="return-value"></a>返回值

第一个（默认）构造函数将该对的第一个元素初始化为类型的默认值 `T1` 和第二个元素的默认值 `T2` 。

第二个构造函数将该对的第一个元素初始化为*Val1* ，并将秒初始化为*Val2。*

第三个（模板）构造函数将该对的第一个元素初始化为 `Right`. **first** 并将第二个元素初始化为 `Right`. **second**。

第四个构造函数使用[右值引用声明符](../cpp/rvalue-reference-declarator-amp-amp.md)将*Val1*的第一个元素和第二个元素初始化为*Val2* ：  &&。

## <a name="remarks"></a>备注

模板结构分别存储类型为和的一对 `T1` 对象 `T2` 。 类型与 `first_type` 模板参数相同 `T1` ，类型与 `second_type` 模板参数相同 `T2` 。 `T1``T2`每个只需要提供一个默认构造函数、一个参数构造函数和一个析构函数。 此类型的所有成员 `pair` 都是公共的，因为该类型声明为 **`struct`** 而不是 **`class`** 。 对的两种最常见用法是作为返回两个值的函数的返回类型以及作为关联容器类 [map 类](../standard-library/map-class.md)和 [multimap 类](../standard-library/multimap-class.md)的元素，这些类具有与每个元素相关联的键和值类型。 后者满足对关联容器的要求，并具有形式的值类型 `pair` <  **`const`** `key_type` `mapped_type`>。

## <a name="example"></a>示例

```cpp
// utility_pair.cpp
// compile with: /EHsc
#include <utility>
#include <map>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;

   // Using the constructor to declare and initialize a pair
   pair <int, double> p1 ( 10, 1.1e-2 );

   // Compare using the helper function to declare and initialize a pair
   pair <int, double> p2;
   p2 = make_pair ( 10, 2.22e-1 );

   // Making a copy of a pair
   pair <int, double> p3 ( p1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;

   // Using a pair for a map element
   map <int, int> m1;
   map <int, int>::iterator m1_Iter;

   typedef pair <int, int> Map_Int_Pair;

   m1.insert ( Map_Int_Pair ( 1, 10 ) );
   m1.insert ( Map_Int_Pair ( 2, 20 ) );
   m1.insert ( Map_Int_Pair ( 3, 30 ) );

   cout << "The element pairs of the map m1 are:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " ( " << m1_Iter -> first << ", "
           << m1_Iter -> second << " )";
   cout   << "." << endl;

   // Using pair as a return type for a function
   pair< map<int,int>::iterator, bool > pr1, pr2;
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );

   if( pr1.second == true )
   {
      cout << "The element (4,40) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }

   if( pr2.second == true )
   {
      cout << "The element (1,10) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }
}
```

```Output
The pair p1 is: ( 10, 0.011 ).
The pair p2 is: ( 10, 0.222 ).
The pair p3 is: ( 10, 0.011 ).
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).
The element (4,40) was inserted successfully in m1.
The element with a key value of
( (pr2.first) -> first ) = 1 is already in m1,
so the insertion failed.
```
