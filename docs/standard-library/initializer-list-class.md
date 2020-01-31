---
title: initializer_list 类
description: 在 Visual Studio 中由 Microsoft 实现的C++标准库中的 initializer_list 类的引用。
ms.date: 01/28/2020
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.openlocfilehash: 6be51835958a07162ce22ff9d619fb793102669f
ms.sourcegitcommit: 684181561490e0d1955cf601d222f67f09af6d00
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2020
ms.locfileid: "76894328"
---
# <a name="initializer_list-class"></a>initializer_list 类

提供访问元素数组的权限，其中数组的每个成员均具有指定的类型。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>参数

*类型*\
要在 `initializer_list` 中存储的元素数据类型。

## <a name="remarks"></a>备注

使用大括号内的初始值设定项列表可构造 `initializer_list`。

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

每当函数签名需要 `initializer_list` 时，编译器将具有同类元素的大括号内的初始值设定项列表转换为 `initializer_list`。 有关使用 `initializer_list`的详细信息，请参阅[统一初始化和委托构造函数](../cpp/uniform-initialization-and-delegating-constructors.md)

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[initializer_list](#initializer_list)|构造 `initializer_list` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|`value_type`|`initializer_list` 中元素的类型。|
|`reference`|一个类型，它提供对 `initializer_list` 中元素的引用。|
|`const_reference`|一个类型，它提供对 `initializer_list` 中元素的常量引用。|
|`size_type`|一个类型，它表示 `initializer_list` 中元素的数目。|
|`iterator`|一个类型，它为 `initializer_list` 提供迭代器。|
|`const_iterator`|一个类型，它为 `initializer_list` 提供常量迭代器。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[begin](#begin)|返回指向 `initializer_list` 中第一个元素的指针。|
|[end](#end)|返回指向 `initializer_list` 中最后一个元素之后的元素的指针。|
|[size](#size)|返回 `initializer_list` 中的元素数量。|

## <a name="requirements"></a>需求

**标头：** \<initializer_list >

**命名空间：** std

## <a name="begin"></a>initializer_list::begin

返回指向 `initializer_list` 中第一个元素的指针。

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>返回值

指向 `initializer_list` 的第一个元素的指针。 如果列表为空，该指针对于列表的开头和末尾都相同。

## <a name="end"></a>initializer_list::end

返回指向 `initializer list` 中最后一个元素之后的元素的指针。

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>返回值

指向列表中最后一个元素之后的元素的指针。 如果列表为空，则它与指向列表中第一个元素的指针相同。

## <a name="initializer_list"></a>initializer_list::initializer_list

构造 `initializer_list` 类型的对象。

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>参数

*第一个*\
要复制的范围元素中的第一个元素的位置。

*最后*\
要复制的元素范围以外的第一个元素的位置。

### <a name="remarks"></a>备注

`initializer_list` 基于指定类型的对象数组。 复制 `initializer_list` 会创建指向相同对象的列表的第二个实例;不会复制基础对象。

### <a name="example"></a>示例

```cpp
// initializer_list_class.cpp
// compile with: /EHsc
#include <initializer_list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty initializer_list c0
    initializer_list <int> c0;

    // Create an initializer_list c1 with 1 element
    initializer_list <int> c1{ 3 };

    // Create an initializer_list c2 with 5 elements
    initializer_list <int> c2{ 5, 4, 3, 2, 1 };

    // Create a copy, initializer_list c3, of initializer_list c2
    initializer_list <int> c3(c2);

    // Create a initializer_list c4 by copying the range c3[ first,  last)
    const int* c3_ptr = c3.begin();
    c3_ptr++;
    c3_ptr++;
    initializer_list <int> c4(c3.begin(), c3_ptr);

    // Move initializer_list c4 to initializer_list c5
    initializer_list <int> c5(move(c4));

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3
c2 = 5 4 3 2 1
c3 = 5 4 3 2 1
c5 = 5 4
```

## <a name="size"></a>initializer_list::size

返回列表中元素的数目。

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>返回值

列表中元素的数目。

## <a name="see-also"></a>另请参阅

[<forward_list>](../standard-library/forward-list.md)
