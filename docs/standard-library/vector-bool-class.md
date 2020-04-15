---
title: vector&lt;bool&gt; 类
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::flip
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: 6c67e3d9ba1b33cb99a7d3afb2522f443003fa38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376086"
---
# <a name="vectorltboolgt-class"></a>vector&lt;bool&gt; 类

该`vector<bool>`类是**bool**类型元素[矢量](../standard-library/vector-class.md)的部分专业化化。 它具有专门化使用的基础类型的分配器，通过每位存储一个**bool**值来提供空间优化。

## <a name="syntax"></a>语法

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>备注

除了本文中说明的差异以外，此类模板专用化的行为类似于矢量。

处理**布尔**类型的操作对应于容器存储中的值。 `allocator_traits::construct` 不用于构造这些值。

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[const_pointer](#const_pointer)|`const_iterator` 的 typedef，可用作指向 `vector<bool>` 的布尔值元素的常量指针。|
|[const_reference](#const_reference)|**布尔**的 typedef。 初始化之后，它不观察对原始值的更新。|
|[指针 (pointer)](#pointer)|`iterator` 的 typedef，可用作指向 `vector<bool>` 的布尔值元素的指针。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[flip](#flip)|反转 `vector<bool>` 中的所有位。|
|[交换](#swap)|交换两个 `vector<bool>` 的元素。|
|[operator&#91;&#93;](#op_at)|返回对指定位置的 `vector<bool>` 元素的模拟引用。|
|`at`|与非专用的 [vector](../standard-library/vector-class.md)::at 函数的作用相同，但它使用代理类 [vector\<bool>::reference](#reference_class)。 另请参阅 [operator[]](#op_at)。|
|`front`|与非专用的 [vector](../standard-library/vector-class.md)::front 函数的作用相同，但它使用代理类 [vector\<bool>::reference](#reference_class)。 另请参阅 [operator[]](#op_at)。|
|`back`|与非专用的 [vector](../standard-library/vector-class.md)::backt 函数的作用相同，但它使用代理类 [vector\<bool>::reference](#reference_class)。 另请参阅 [operator[]](#op_at)。|

### <a name="proxy-class"></a>代理类

|||
|-|-|
|[vector\<bool> reference 类](#reference_class)|一种用做代理以模拟 `bool&` 行为的类，其对象可提供对 `vector<bool>` 对象中的元素（一位）的引用。|

## <a name="requirements"></a>要求

**标题** \<： 矢量>

**命名空间:** std

## <a name="vectorboolconst_pointer"></a><a name="const_pointer"></a>矢\<量布尔>：：const_pointer

该类型描述可作为常量指针的对象，该指针指向 `vector<bool>` 对象所包含序列中的布尔元素。

```cpp
typedef const_iterator const_pointer;
```

## <a name="vectorboolconst_reference"></a><a name="const_reference"></a>矢\<量布尔>：：const_reference

该类型描述可作为常量引用的对象，它引用 `vector<bool>` 对象所包含序列中的布尔元素。

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>备注

有关详细信息和代码示例，请参阅 [vector&lt;bool&gt;::reference::operator=](#reference_operator_eq)。

## <a name="vectorboolflip"></a><a name="flip"></a>矢\<量布尔>：翻转

反转 `vector<bool>` 中的所有位。

```cpp
void flip();
```

### <a name="example"></a>示例

```cpp
// vector_bool_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha; // format output for subsequent code

    vector<bool> vb = { true, false, false, true, true };
    cout << "The vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vb.flip();

    cout << "The flipped vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

## <a name="vectorbooloperator"></a><a name="op_at"></a>矢\<量布尔>：：运算符*

返回对指定位置的 `vector<bool>` 元素的模拟引用。

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|-|-|
|*Pos*|`vector<bool>` 元素的位置。|

### <a name="return-value"></a>返回值

包含索引元素值的 [vector\<bool>::reference](#reference_class) 或 [vector\<bool>::const_reference](#const_reference) 对象。

如果指定的位置大于或等于容器大小，则结果为 undefined。

### <a name="remarks"></a>备注

如果使用_ITERATOR_DEBUG_LEVEL集进行编译，则如果尝试访问向量边界外的元素，则会发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md)。

### <a name="example"></a>示例

此代码示例显示了 正确使用`vector<bool>::operator[]`和两个常见的编码错误，这些错误被注释掉。这些错误会导致错误，因为无法获取`vector<bool>::reference``vector<bool>::operator[]`返回的对象的地址。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;
    vector<bool> vb;

    vb.push_back(true);
    vb.push_back(false);

    //    bool* pb = &vb[1]; // conversion error - do not use
    //    bool& refb = vb[1];   // conversion error - do not use
    bool hold = vb[1];
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;

    // Note this doesn't modify hold.
    vb[1] = true;
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;
}
```

## <a name="vectorboolpointer"></a><a name="pointer"></a>矢\<量布尔>：:pointer

一种类型，用于描述一个对象来充当指针，以便指向 `vector<bool>` 对象所包含序列的布尔元素。

```cpp
typedef iterator pointer;
```

## <a name="vectorboolreference-class"></a><a name="reference_class"></a>矢\<量布尔>：参考类

`vector<bool>::reference` 类是 [vector\<bool> 类](../standard-library/vector-bool-class.md) 为模拟 `bool&` 而提供的一种代理类。

### <a name="remarks"></a>备注

必须使用模拟引用，因为 C++ 不允许直接引用位。 `vector<bool>` 每个元素只使用一个位，这可以使用此代理类来引用。 但是，引用模拟不会完成，原因是某些赋值无效。 例如，因为无法采用 `vector<bool>::reference` 对象的地址，所以下列使用 [vector\<bool>::operator[]](#op_at) 的代码是错误的：

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="vectorboolreferenceflip"></a><a name="reference_flip"></a>矢\<量布尔>：：参考：：翻转

反转引用的 [vector\<bool>](../standard-library/vector-bool-class.md) 元素的布尔值。

```cpp
void flip();
```

#### <a name="example"></a>示例

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

### <a name="vectorboolreferenceoperator-bool"></a><a name="reference_operator_bool"></a>矢\<量布尔>：：参考：：运算符布尔

提供从`vector<bool>::reference` **bool**的隐式转换。

```cpp
operator bool() const;
```

#### <a name="return-value"></a>返回值

vector\<bool> 对象元素的布尔值。

#### <a name="remarks"></a>备注

`vector<bool>` 对象无法通过此运算符修改。

### <a name="vectorboolreferenceoperator"></a><a name="reference_operator_eq"></a>矢\<量布尔>：：参考：：运算符*

将布尔值赋给一个位，或将引用的元素所保存的值赋给一个位。

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>参数

*对*\
要将值赋给位的元素引用。

*瓦尔*\
要赋给位的布尔值。

#### <a name="example"></a>示例

```cpp
// vector_bool_ref_op_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    print("The vector is: ", vb);

    // Invoke vector<bool>::reference::operator=()
    vector<bool>::reference refelem1 = vb[0];
    vector<bool>::reference refelem2 = vb[1];
    vector<bool>::reference refelem3 = vb[2];

    bool b1 = refelem1;
    bool b2 = refelem2;
    bool b3 = refelem3;
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;
    cout << endl;

    refelem2 = refelem1;

    print("The vector after assigning refelem1 to refelem2 is now: ", vb);

    refelem3 = true;

    print("The vector after assigning false to refelem1 is now: ", vb);

    // The initial values are still stored in the bool variables and remained unchanged
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;
    cout << endl;
}
```

```Output
The vector is: true false false true true
The original value of the 1st element stored in a bool: true
The original value of the 2nd element stored in a bool: false
The original value of the 3rd element stored in a bool: false

The vector after assigning refelem1 to refelem2 is now: true true false true true
The vector after assigning false to refelem1 is now: true true true true true
The original value of the 1st element still stored in a bool: true
The original value of the 2nd element still stored in a bool: false
The original value of the 3rd element still stored in a bool: false
```

## <a name="vectorboolswap"></a><a name="swap"></a>矢\<量布尔>：交换

通过使用代理类 [vector\<bool>::reference](#reference_class) 交换布尔矢量 ( `vector<bool>`) 的两个元素的静态成员函数。

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>参数

*离开*\
要与*右*元素交换的元素。

*对*\
要与*左*元素交换的元素。

### <a name="remarks"></a>备注

此重载支持 `vector<bool>` 的特殊代理要求。 [vector](../standard-library/vector-class.md)::swap 的功能与 `vector<bool>::swap()` 的单参数重载相同。

## <a name="see-also"></a>另请参阅

[C++标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
