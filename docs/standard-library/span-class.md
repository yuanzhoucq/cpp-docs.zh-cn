---
title: span 类（c + + 标准库） |Microsoft Docs
ms.date: 05/28/2020
f1_keywords:
- span/std::span
- span/std::span::const_pointer
- span/std::span::const_reference
- span/std::span::difference_type
- span/std::span::element_type
- span/std::span::iterator
- span/std::span::pointer
- span/std::span::reference
- span/std::span::reverse_iterator
- span/std::span::size_type
- span/std::span::value_type
- span/std::span::at
- span/std::span::assign
- span/std::span::back
- span/std::span::begin
- span/std::span::data
- span/std::span::empty
- span/std::span::end
- span/std::span::front
- span/std::span::rbegin
- span/std::span::rend
- span/std::span::size
- span/std::span::size_bytes
- span/std::span::operator=
- span/std::span::operator[]
helpviewer_keywords:
- std::span [C++]
- std::span [C++], const_pointer
- std::span [C++], const_reference
- std::span [C++], difference_type
- std::span [C++], element_type
- std::span [C++], iterator
- std::span [C++], pointer
- std::span [C++], reference
- std::span [C++], reverse_iterator
- std::span [C++], size_type
- std::span [C++], value_type
- std::span [C++], assign
- std::span [C++], at
- std::span [C++], back
- std::span [C++], begin
- std::span [C++], data
- std::span [C++], empty
- std::span [C++], end
- std::span [C++], front
- std::span [C++], rbegin
- std::span [C++], rend
- std::span [C++], size
- std::span [C++], size_bytes
ms.openlocfilehash: 86ef4afcb5e6e7a9d244a8c2f2126bec7e1ace75
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217449"
---
# <a name="span-class-c-standard-library"></a>span 类（c + + 标准库）

为一系列连续的对象提供轻量视图。 跨度提供一种安全的方法，可在内存中循环访问（例如，存储在内置数组、或中的对象），并对这些对象进行索引。 `std::array` `std::vector`

如果您通常使用指针和索引访问一系列的后向后对象， `span` 则是一种更安全的轻型替代方法。

`span`可在编译时设置的大小，方法是将其指定为模板参数，或在运行时指定 `dynamic_extent` 。

## <a name="syntax"></a>语法

```cpp
template<class T, size_t Extent = dynamic_extent>
class span;
```

### <a name="template-parameters"></a>模板参数

|参数|描述|
|-|-|
|`T`| 范围中元素的类型。 |
|`Extent`| 如果在编译时指定，则为跨距中的元素数。 否则， `std::dynamic_extent` 如果在运行时将指定元素的数量，则为。 |

[扣缴指南](#deduction_guides)

## <a name="members"></a>成员

| **类型定义** | **说明** |
|-|-|
| [const_pointer](#pointer) | 指向元素的指针的类型 **`const`** 。 |
| [const_reference](#reference) | 对元素的引用的类型 **`const`** 。 |
| [difference_type](#difference_type) | 两个元素间的带符号距离的类型。 |
| [element_type](#element_type) | Span 元素的类型。 |
| [器](#iterator) | 范围的迭代器的类型。 |
| [变为](#pointer) | 指向元素的指针的类型。 |
| [reference](#reference) | 元素的引用的类型。 |
| [reverse_iterator](#reverse_iterator) | 跨度的反向迭代器的类型。 |
| [size_type](#size_type) | 范围内两个元素之间的无符号距离的结果类型。 |
| [value_type](#value_type) | 元素的类型，无 **`const`** 或 **`volatile`** 限定。 |
| **构造函数** | **说明** |
|[格](#span)| 构造 `span`。|
| **迭代器支持** | **说明** |
|[准备](#begin) | 获取一个迭代器，该迭代器指向范围中的第一个元素。|
|[end](#end) | 获取一个迭代器，该迭代器指向范围的末尾。 |
|[rbegin](#rbegin) | 获取一个反向迭代器，该迭代器指向范围的最后一个元素;即反向跨度的开头。|
|[rend](#rend) | 获取指向范围前部的反向迭代器;也就是说，已反转范围的结尾。|
| **访问元素**| **说明** |
|[返回](#back) | 获取跨度中的最后一个元素。|
|[data](#data) | 获取范围中第一个元素的地址。|
|[主](#front) | 获取范围中的第一个元素。|
|[操作员\[\]](#op_at) | 访问指定位置处的元素。|
| **观察程序** | **说明** |
|[empty](#empty)| 测试跨度是否为空。|
|[大小](#size) | 获取范围中的元素数。|
|[size_bytes](#size_bytes) | 获取范围的大小（以字节为单位）。|
| **子视图** | **说明**|
| [first](#first_view) | 从跨度的正面获取 subspan。|
| [last](#last_view) | 从范围的背面获取 subspan。|
| [subspan](#sub_view) | 从范围内的任意位置获取 subspan。|
| **运算符** | **说明** |
|[span：： operator =](#op_eq)| 替换跨度。|
|[span：：运算符\[\]](#op_at)| 获取指定位置处的元素。 |

## <a name="remarks"></a>备注

所有 `span` 成员函数都具有恒定的时间复杂性。

与 `array` 或不同 `vector` ，范围内的元素不 "拥有"。 范围不会释放其中的项的任何存储，因为它不拥有这些对象的存储。

## <a name="requirements"></a>要求

**标头：**\<span>

**命名空间:** std

**编译器选项：** /std： c + + 最新

## <a name="spanback"></a><a name="back"></a> `span::back`

获取跨度中的最后一个元素。

```cpp
constexpr reference back() const noexcept;
```

### <a name="return-value"></a>返回值

对跨距中最后一个元素的引用。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << mySpan.back();
}
```

```Output
2
```

## <a name="spanbegin"></a><a name="begin"></a> `span::begin`

获取一个迭代器，该迭代器指向范围中的第一个元素。

```cpp
constexpr iterator begin() const noexcept;
```

### <a name="return-value"></a>返回值

指向范围中第一个元素的迭代器。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.begin();
    cout << *i;
}
```

```Output
0
```

## <a name="spandata"></a><a name="data"></a> `span::data`

获取指向范围数据开始位置的指针。

```cpp
constexpr pointer data() const noexcept;
```

### <a name="return-value"></a>返回值

指向存储在跨度中的第一个项的指针。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    auto i = mySpan.data();
    cout << *i;
}
```

```Output
0
```

## <a name="spandifference_type"></a><a name="difference_type"></a> `span::difference_type`

范围中两个元素之间的元素数目。

```cpp
using difference_type = std::ptrdiff_t;
```

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::difference_type distance = mySpan.end() - mySpan.begin();
    cout << distance << std::endl;
}
```

```Output
3
```

## <a name="spanelement_type"></a><a name="element_type"></a> `span::element_type`

范围中元素的类型。

```cpp
using element_type = T;
```

### <a name="remarks"></a>备注

创建范围时，将从模板参数获取类型 `T` 。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::element_type et = mySpan[2];
    cout << et << endl;
}
```

```Output
2
```

## <a name="spanempty"></a><a name="empty"></a> `span::empty`

跨距是否包含元素。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>返回值

**`true`** 如果为 `this->size() == 0` ，则返回。 否则为 **`false`** 。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    bool isEmpty = mySpan.empty(); // isEmpty == false
}
```

## <a name="spanend"></a><a name="end"></a> `span::end`

获取到跨距末尾的迭代器。

```cpp
constexpr iterator end() const noexcept;
```

### <a name="return-value"></a>返回值

指向刚超出范围末尾的迭代器。

### <a name="remarks"></a>备注

`end` 用于测试迭代器是否超过了其范围的末尾。

不要取消引用此迭代器返回的值。 使用它来确定迭代器是否已到达范围中最后一个元素之外。

### <a name="example"></a>示例

```cpp
// Iteration
for (auto it = s1.begin(); it != s1.end(); ++it)
{
    cout << *it;
}
```

## <a name="spanfirst"></a><a name="first_view"></a> `span::first`

获取 subspan，从此范围的正面开始。

```cpp
constexpr auto first(size_type count) const noexcept;
template <size_t count> constexpr auto first() const noexcept;
```

### <a name="parameters"></a>参数

*计*\
要放置在 subspan 中的此跨度开头的元素数。  
元素数指定为模板的参数，或指定给函数，如下所示。

### <a name="return-value"></a>返回值

包含 `count` 此范围前面的元素的范围。

### <a name="remarks"></a>备注

如果可能，请使用此函数的模板版本在 `count` 编译时验证，并保留有关范围的信息，因为它返回的是一个固定区范围。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.first(2);
    cout << "mySpan.first(2): ";
    for (auto& i : first2)
    {
        cout << i;
    }

    cout << "\nmySpan.first<2>: ";
    auto viewSpan = mySpan.first<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.first(2): 01
mySpan.first<2>: 01
```

## <a name="spanfront"></a><a name="front"></a> `span::front`

获取范围中的第一个元素。

```cpp
constexpr reference front() const noexcept;
```

### <a name="return-value"></a>返回值

对跨距中第一个元素的引用。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.front();
    cout << i;
}
```

```Output
0
```

## <a name="spaniterator"></a><a name="iterator"></a> `span::iterator`

跨范围元素的迭代器的类型。

```cpp
using iterator = implementation-defined-iterator-type;
```

### <a name="remarks"></a>备注

此类型充当范围内的元素的迭代器。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::iterator it = mySpan.begin();
    cout << *it++ << *it++ << *it;
}
```

```Output
012
```

## <a name="spanlast"></a><a name="last_view"></a> `span::last`

获取 subspan，从此范围的结尾开始。

```cpp
constexpr span<element_type, dynamic_extent> last(const size_type count) const noexcept;
template <size_t count> constexpr span<element_type, count> last() const noexcept;
```

### <a name="parameters"></a>参数

*计*\
要放置在 subspan 中的元素的数目。
可以将该数字指定为模板的参数，或指定给函数，如下所示。

### <a name="return-value"></a>返回值

包含 `count` 此范围中最后一个元素的范围。

### <a name="remarks"></a>备注

如果可能，请使用此函数的模板版本在 `count` 编译时验证，并保留有关范围的信息，因为它返回的是一个固定区范围。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.last(2);
    cout << "mySpan.last(2): ";
    for (auto& i : last2)
    {
        cout << i;
    }

    cout << "\nmySpan.last<2>: ";
    auto viewSpan = mySpan.last<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.last(2): 12
mySpan.last<2>: 12
```

## <a name="spanoperator"></a><a name="op_at"></a> `span::operator[]`

获取范围中指定位置的元素。

```cpp
constexpr reference operator[](size_type offset) const;
```

### <a name="parameters"></a>参数

*抵销*\
要访问的范围内从零开始的元素。

### <a name="return-value"></a>返回值

对位置*偏移量*处的元素的引用。 如果该位置无效，则该行为是不确定的。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan[1];
}
```

```Output
1
```

## <a name="spanoperator"></a><a name="op_eq"></a> `span::operator=`

向此分配另一个范围。

```cpp
constexpr span& operator=(const span& other) noexcept = default;
```

### <a name="parameters"></a>参数

*以外*\
要分配给此的跨度。

### <a name="return-value"></a>返回值

`*this`

### <a name="remarks"></a>备注

赋值将对数据指针和大小进行浅表复制。 浅表副本是安全的，因为 `span` 不会为其包含的元素分配内存。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    span<int> mySpan2;
    mySpan2 = mySpan;
    for (auto &i : mySpan2)
    {
        cout << it;
    }
}
```

```Output
012
```

## <a name="spanpointer"></a><a name="pointer"></a> `span::pointer`

指向范围元素的指针和指针的类型 **`const`** 。

```cpp
using pointer = T*;
using const_pointer = const T*;
```

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // pointer
    span<int>::pointer ptr = &mySpan[2];
    *ptr = 9;
    cout << mySpan[2];

    // const pointer
    span<int>::const_pointer cPtr = &mySpan[0];
    // *cPtr = 9; error - const
    cout << *cPtr;
}
```

```Output
90
```

## <a name="spanrbegin"></a><a name="rbegin"></a> `span::rbegin`

获取指向此范围中最后一个元素的反向迭代器。

```cpp
constexpr reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>返回值

指向反向跨度开头的迭代器。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

```Output
210
```

## <a name="spanreference"></a><a name="reference"></a> `span::reference`

引用的类型和对 **`const`** span 元素的引用。

```cpp
using reference = T&;
using const_reference = const T&;
```

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // reference
    span<int>::reference ref = mySpan[0];
    ref = 9;
    cout << mySpan[0];
    // const reference
    span<int>::const_reference cRef = mySpan[1];
    // cRef = 9; error because const
    cout << cRef;
}
```

```Output
91
```

## <a name="spanrend"></a><a name="rend"></a> `span::rend`

获取一个随机访问迭代器，该迭代器指向刚刚超出反向范围末尾的位置。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>返回值

反向迭代器指向反向范围中最后一个元素之后的占位符;也就是说，非反向范围中第一个元素之前的占位符。

### <a name="remarks"></a>备注

`rend`与反向跨度一起使用，正如[span：： end](#end)用于跨距。 用于测试反向迭代器是否已到达其跨度的终点。

返回的值 `rend` 不应被取消引用。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

## <a name="spanreverse_iterator"></a><a name="reverse_iterator"></a> `span::reverse_iterator`

跨度的反向迭代器的类型。

```cpp
using reverse_iterator = std::reverse_iterator<iterator>;
```

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::reverse_iterator rIt = mySpan.rbegin();
    cout << *rIt++ << *rIt++ << *rIt;
}
```

```Output
210
```

## <a name="spansize"></a><a name="size"></a> `span::size`

获取范围中的元素数。

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>返回值

跨度中的元素数。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size();
}
```

```Output
3
```

## <a name="spansize_bytes"></a><a name="size_bytes"></a> `span::size_bytes`

获取范围中元素的大小（以字节为单位）。

```cpp
constexpr size_type size_bytes() const noexcept;
```

### <a name="return-value"></a>返回值

跨度中所有元素占用的字节数;也就是说， `sizeof(element_type)` 乘以范围中的元素数。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size_bytes(); // 3 elements * 4 (size of an int)
}
```

```Output
12
```

## <a name="spansize_type"></a><a name="size_type"></a> `span::size_type`

一种无符号类型，适用于存储范围中的元素数。

```cpp
using size_type = size_t;
```

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::size_type szType = mySpan.size();
    cout << szType;
}
```

```Output
3
```

## <a name="spanspan"></a><a name="span"></a> `span::span`

`span`函数.

```cpp
constexpr span() noexcept
requires (Extent == 0 || Extent == dynamic_extent) = default;

template <class It>
constexpr explicit(Extent != dynamic_extent)
span(It first, size_type count) noexcept

template <class It, class End>
constexpr explicit(Extent != dynamic_extent)
span(It first, End last) noexcept(noexcept(last - first))

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<T (*)[], T (*)[]>
constexpr span(array<T, N>& arr) noexcept

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<const T (*)[], T (*)[]>
constexpr span(const array<T, N>& arr) noexcept

template <size_t N>
requires (Extent == dynamic_extent || Extent == N)
constexpr span(type_identity_t<T> (&arr)[N]) noexcept

template <class R>
constexpr explicit(Extent != dynamic_extent)
span(R&& r)

// default copy ctor
constexpr span(const span& other) noexcept = default;

// converting  ctor
template <class T, size_t OtherExtent>
requires (Extent == dynamic_extent || OtherExtent == dynamic_extent ||
              Extent == OtherExtent) && is_convertible_v<T (*)[], T (*)[]>
constexpr explicit(Extent != dynamic_extent && OtherExtent == dynamic_extent)
span(const span<T, OtherExtent>& other) noexcept
```

### <a name="parameters"></a>参数

*arr*\
从数组构造范围。

*计*\
将位于范围内的元素的数目。

*1*\
指向范围中第一个元素的迭代器。

*时间*\
迭代器到越过范围中最后一个元素的范围。

*北*\
将位于范围内的元素的数目。

*以外*\
复制此范围。

*迅驰*\
从此范围构造范围。

### <a name="remarks"></a>备注

跨度不会释放范围内的项的存储，因为它不拥有其中的对象的存储。

|构造函数  | 说明  |
|---------|---------|
|`span()` | 构造空范围。 仅当模板参数为或时，才考虑重载解析过程 `Extent` `0` `dynamic_extent` 。|
|`span(It first, size_type count)` | 从迭代器中的第一个元素构造范围 `count` `first` 。  仅当模板参数不为时，才考虑重载解析过程 `Extent` `dynamic_extent` 。 |
|`span(It first, End last)` | 从迭代器中的元素构造范围 `first` 直到到达结束为止 `last` 。 仅当模板参数不为时，才考虑重载解析过程 `Extent` `dynamic_extent` 。 `It`必须是 `contiguous_iterator` 。  |
|`span(array<T, N>& arr) noexcept;`<br /><br />`span(const array<T, N>& arr) noexcept;`<br /><br />`span(type_identity_t<element_type> (&arr)[N]) noexcept;` |  从 `N` 指定数组的元素构造范围。 仅当模板参数 `Extent` 为或相等时才考虑重载解析过程 `dynamic_extent` `N` 。 |
|`span(R&& r)` |  从范围构造范围。 如果模板参数不是，则仅参与重载决策 `Extent` `dynamic_extent` 。|
|`span(const span& other)` |  编译器生成的复制构造函数。 数据指针的浅表副本是安全的，因为跨距不会分配内存来保存元素。 |
|`span(const span<OtherElementType, OtherExtent>& s) noexcept;` | 转换构造函数：构造另一个范围内的范围。 如果模板参数 `Extent` 为 `dynamic_extent` ，或者 `N` 为 `dynamic_extent` 或等于， `Extent` 则仅参与重载决策。|

### <a name="example"></a>示例

```cpp
#include <span>

using namespace std;

int main()
{
    const int MAX=10;

    int x[MAX];
    for (int i = 0; i < MAX; i++)
    {
        x[i] = i;
    }

    span<int, MAX> span1{ x }; // fixed-size span: compiler error if size of x doesn't match template argument MAX
    span<int> span2{ x }; // size is inferred from x
    span<const int> span3 = span2; // converting constructor
    span<int> span4( span2 ); // copy constructor
}
```

## <a name="spansubspan"></a><a name="sub_view"></a> `span::subspan`

获取此范围的 subspan。

```cpp
constexpr auto subspan(size_type offset, size_type count = dynamic_extent) const noexcept;

template <size_t offset, size_t count = dynamic_extent>
constexpr auto subspan() const noexcept
```

### <a name="parameters"></a>参数

*计*\
要放入 subspan 中的元素的数目。 如果 `count` 为 `dynamic_extent` （默认值），则从 subspan `offset` 到此跨度的末尾。

*抵销*\
此范围中启动 subspan 的位置。

### <a name="return-value"></a>返回值

`offset`从此范围中开始的范围。 包含 `count` 元素。

### <a name="remarks"></a>备注

此函数的模板版本可用来检查编译时的计数，该计数通过返回一段固定区来保留范围的相关信息。

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << "mySpan.subspan(1,2): ";
    for (auto& i : mySpan.subspan(1,2))
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1,2>: ";
    for (auto& i : mySpan.subspan<1,2>())
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1>: ";
    for (auto& i : mySpan.subspan<1>)
    {
        cout << i;
    }
}
```

```Output
mySpan.subspan(1,2): 12
mySpan.subspan<1,2>: 12
mySpan.subspan<1>: 12
```

## <a name="spanvalue_type"></a><a name="value_type"></a> `span::value_type`

跨度中的元素的类型，无 **`const`** 或 **`volatile`** 限定。

```cpp
using value_type = std::remove_cv_t<T>;
```

### <a name="example"></a>示例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::value_type vType = mySpan[2];
    cout << vType;
}
```

```Output
2
```

## <a name="deduction-guides"></a><a name="deduction_guides"></a>扣缴指南

为范围提供以下扣缴指南。

```cpp
// Allows the extent to be deduced from std::array and C++ built-in arrays

template <class T, size_t Extent>
span(T (&)[Extent]) -> span<T, Extent>;

template <class T, size_t Size>
span(array<T, Size>&) -> span<T, Size>;

template <class T, size_t Size>
span(const array<T, Size>&) -> span<const T, Size>;

// Allows the element type to be deduced from the iterator and the end of the span.
// The iterator must be contiguous

template <contiguous_iterator It, class End>
span(It, End) -> span<remove_reference_t<iter_reference_t<It>>>;

// Allows the element type to be deduced from a range.
// The range must be contiguous

template <ranges::contiguous_range Rng>
span(Rng &&) -> span<remove_reference_t<ranges::range_reference_t<Rng>>>;
```

## <a name="see-also"></a>另请参阅

[\<span>](../standard-library/span.md)  
[如何使用类模板参数推导](https://devblogs.microsoft.com/cppblog/how-to-use-class-template-argument-deduction/)
