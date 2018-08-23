---
title: tuple_size 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
dev_langs:
- C++
helpviewer_keywords:
- std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c03c47502fdd9309b3d6553c3f46f9685d4eaa9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958261"
---
# <a name="tuplesize-class"></a>tuple_size 类

包含 `tuple` 包含的元素数目。

## <a name="syntax"></a>语法

```cpp
// TEMPLATE STRUCT tuple_size
template <class Tuple>
   struct tuple_size;

// number of elements in array
template <class Elem, size_t Size>
   struct tuple_size<array<Elem, Size>>
      : integral_constant<size_t, Size>;

// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>>
      : integral_constant<size_t, 2>

// size of tuple
template <class... Types>
   struct tuple_size<tuple<Types...>>
      : integral_constant<size_t, sizeof...(Types)>;

// size of const tuple
template <class Tuple>
   struct tuple_size<const Tuple>;

// size of volatile tuple
template <class Tuple>
   struct tuple_size<volatile Tuple>;

// size of const volatile tuple
template <class Tuple>
   struct tuple_size<const volatile Tuple>;
```

### <a name="parameters"></a>参数

*Tuple*  
元组的类型。

*Elem*  
数组元素的类型。

*Size*  
数组大小。

T1  
对的第一个成员的类型。

T2  
对的第二个成员的类型。

*类型*  
元组元素的类型。

## <a name="remarks"></a>备注

此模板类有一个成员`value`，它是其值为元组类型的范围的整型常量表达式*元组*。

数组的模板专用化有一个成员`value`，它是其值是整数常量表达式*大小*，它是数组的大小。

对的模板专用化拥有成员 `value`，它是整型常数表达式，值为 2。

## <a name="example"></a>示例

```cpp
#include <tuple>
#include <iostream>

using namespace std;

typedef tuple<int, double, int, double> MyTuple;
int main()
{
    MyTuple c0(0, 1.5, 2, 3.7);

    // display contents " 0 1 2 3"
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0);
    cout << " " << get<2>(c0);
    cout << " " << get<3>(c0) << endl;

    // display size " 4"
    cout << " " << tuple_size<MyTuple>::value << endl;
}
```

```Output
 0 1.5 2 3.7
```

## <a name="requirements"></a>要求

**标头：** \<元组 >**标头：** \<数组 > （适用于数组专用化）**标头：** \<实用程序 > （适用于对专用化）

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<tuple>](../standard-library/tuple.md)<br/>
[tuple](../standard-library/tuple-class.md)<br/>
[tuple_element 类](../standard-library/tuple-element-class-tuple.md)<br/>
