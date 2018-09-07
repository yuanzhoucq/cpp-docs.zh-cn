---
title: plus 结构 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::plus
dev_langs:
- C++
helpviewer_keywords:
- plus class
- plus struct
ms.assetid: 4594abd5-b2f2-4fac-9b6b-fc9a2723f8cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81dee8442d38a4436b503da83f2853c030b652da
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103209"
---
# <a name="plus-struct"></a>plus 结构

对其自变量执行加法运算（二元 `operator+`）的预定义函数对象。

## <a name="syntax"></a>语法

```
template <class Type = void>
struct plus : public binary_function <Type, Type, Type>
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator+
template <>
struct plus<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) + std::forward<U>(Right));
};
```

### <a name="parameters"></a>参数

*类型*， *T*， *U*支持二进制文件的类型`operator+`接受指定或推断类型的操作数。

左侧<br/>
加法运算的左操作数。 专用化的模板采用类型的左值引用参数*类型*。 专用化的模板可完美转移左值和右值引用参数的类型推断*T*。

右侧<br/>
加法运算的右操作数。 专用化的模板采用类型的左值引用参数*类型*。 专用化的模板可完美转移左值和右值引用参数的类型推断*U*。

## <a name="return-value"></a>返回值

`Left + Right` 的结果。 专用化模板可完美转移结果，该结果具有由二元 `operator+` 返回的类型。

## <a name="example"></a>示例

```cpp
// functional_plus.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <double> v1, v2, v3 ( 6 );
   vector <double>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1.push_back( 4 * i );

   int j;
   for ( j = 0 ; j <= 5 ; j++ )
      v2.push_back( -2.0 * j - 4 );

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Finding the element-wise sums of the elements of v1 & v2
   transform (v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ), plus<double>( ) );

   cout << "The element-wise sums are: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
\* Output:
The vector v1 = ( 0 4 8 12 16 20 )
The vector v2 = ( -4 -6 -8 -10 -12 -14 )
The element-wise sums are: ( -4 -2 0 2 4 6 )
*\
```

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
