---
title: less 结构 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::less
dev_langs:
- C++
helpviewer_keywords:
- less struct
- less function
ms.assetid: 39349da3-11cd-4774-b2cc-b46af5aae5d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fac4528c976e99a77ceec8bc170323846a0e3a28
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858911"
---
# <a name="less-struct"></a>less 结构

一个二元谓词，该谓词对其参数执行小于运算 ( `operator<`)。

## <a name="syntax"></a>语法

```cpp
template <class Type = void>
struct less : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<
template <>
struct less<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) <std::forward<U>(Right));
};
```

### <a name="parameters"></a>参数

`Type``T`，`U`支持任何类型`operator<`接受的操作数的指定或推断类型。

`Left` 小于的左的操作数的操作相比，前者。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `T` 的左值和右值引用参数。

`Right` 小于的右操作数的操作相比，前者。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `U` 的左值和右值引用参数。

## <a name="return-value"></a>返回值

`Left < Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator<` 返回的类型。

## <a name="remarks"></a>备注

二元谓词 `less`< `Type`> 向等价类提供类型为 `Type` 的一组元素值的严格弱排序（在且仅在此类型满足如此进行排序的标准数学要求时）。 任何指针类型的专用化都会产生元素的全序，所有不同值的元素都会相对于彼此进行排序。

## <a name="example"></a>示例

```cpp
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

## <a name="output"></a>输出

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500)
```

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
