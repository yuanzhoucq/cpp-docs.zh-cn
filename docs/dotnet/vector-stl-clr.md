---
title: vector (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
ms.openlocfilehash: c6a001797e90bd7381358abb16612926442e8d9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371820"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)

模板类描述控制具有随机访问的不同长度元素序列的对象。 使用容器`vector`将一系列元素作为连续存储块进行管理。 块作为按需增长的数组实现。

在下面的描述中，`GValue`与*Value*相同，除非后者是 ref 类型，在这种情况下，它是`Value^`。

## <a name="syntax"></a>语法

```cpp
template<typename Value>
    ref class vector
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IVector<GValue>
    { ..... };
```

### <a name="parameters"></a>参数

*“值”*<br/>
受控序列中的元素的类型。

## <a name="requirements"></a>要求

**标题**\<：cliext/矢量>

**命名空间**：cliext

## <a name="declarations"></a>声明

|类型定义|说明|
|---------------------|-----------------|
|[vector::const_iterator (STL/CLR)](#const_iterator)|受控序列的常量迭代器的类型。|
|[vector::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|
|[vector::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|
|[vector::generic_container (STL/CLR)](#generic_container)|容器的泛型接口的类型。|
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|容器的泛型接口的迭代器的类型。|
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型接口的反向迭代器的类型。|
|[vector::generic_value (STL/CLR)](#generic_value)|容器的泛型接口的元素的类型。|
|[vector::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|
|[vector::reference (STL/CLR)](#reference)|元素的引用的类型。|
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|受控序列的反向迭代器的类型。|
|[vector::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|
|[vector::value_type (STL/CLR)](#value_type)|元素的类型。|

|成员函数|说明|
|---------------------|-----------------|
|[vector::assign (STL/CLR)](#assign)|替换所有元素。|
|[vector::at (STL/CLR)](#at)|访问指定位置处的元素。|
|[vector::back (STL/CLR)](#back)|访问最后一个元素。|
|[vector::begin (STL/CLR)](#begin)|指定受控序列的开头。|
|[vector::capacity (STL/CLR)](#capacity)|报告为容器分配的存储大小。|
|[vector::clear (STL/CLR)](#clear)|删除所有元素。|
|[vector::empty (STL/CLR)](#empty)|测试元素是否存在。|
|[vector::end (STL/CLR)](#end)|指定受控序列的末尾。|
|[vector::erase (STL/CLR)](#erase)|移除指定位置处的元素。|
|[vector::front (STL/CLR)](#front)|访问第一个元素。|
|[vector::insert (STL/CLR)](#insert)|在指定位置添加元素。|
|[vector::pop_back (STL/CLR)](#pop_back)|删除最后一个元素。|
|[vector::push_back (STL/CLR)](#push_back)|添加新的最后一个元素。|
|[vector::rbegin (STL/CLR)](#rbegin)|指定反向受控序列的开头。|
|[vector::rend (STL/CLR)](#rend)|指定反向受控序列的末尾。|
|[vector::reserve (STL/CLR)](#reserve)|确保容器的最低增长能力。|
|[vector::resize (STL/CLR)](#resize)|更改元素的数量。|
|[vector::size (STL/CLR)](#size)|对元素数进行计数。|
|[vector::swap (STL/CLR)](#swap)|交换两个容器的内容。|
|[vector::to_array (STL/CLR)](#to_array)|将受控序列复制到新数组。|
|[vector::vector (STL/CLR)](#vector)|构造容器对象。|

|Property|说明|
|--------------|-----------------|
|[vector::back_item (STL/CLR)](#back_item)|访问最后一个元素。|
|[vector::front_item (STL/CLR)](#front_item)|访问第一个元素。|

|操作员|说明|
|--------------|-----------------|
|[vector::operator= (STL/CLR)](#op_as)|替换受控序列。|
|[vector::operator(STL/CLR)](#op)|访问指定位置处的元素。|
|[运算符！* （矢量） （STL/CLR）](#op_neq)|确定对象`vector`是否不等于其他`vector`对象。|
|[运算符<（矢量）（STL/CLR）](#op_lt)|确定`vector`对象是否小于其他`vector`对象。|
|[运算符<= （矢量） （STL/CLR）](#op_lteq)|确定对象是否`vector`小于或等于另一个`vector`对象。|
|[运算符* （矢量） （STL/CLR）](#op_eq)|确定对象是否`vector`等于另一个`vector`对象。|
|[operator> (vector) (STL/CLR)](#op_gt)|确定对象是否`vector`大于另一个`vector`对象。|
|[运算符>= （矢量） （STL/CLR）](#op_gteq)|确定对象是否`vector`大于或等于另一个`vector`对象。|

## <a name="interfaces"></a>接口

|接口|说明|
|---------------|-----------------|
|<xref:System.ICloneable>|复制对象。|
|<xref:System.Collections.IEnumerable>|通过元素排序。|
|<xref:System.Collections.ICollection>|维护元素组。|
|<xref:System.Collections.Generic.IEnumerable%601>|通过类型化元素进行排序。|
|<xref:System.Collections.Generic.ICollection%601>|维护类型化元素组。|
|<xref:System.Collections.Generic.IList%601>|维护有序的键入元素组。|
|IVector<值\>|维护通用容器。|

## <a name="remarks"></a>备注

对象通过存储*的值*元素数组为其控制的顺序分配和释放存储，该数组按需增长。 增长的方式是附加新元素的成本是摊销恒定时间。 换句话说，在末尾添加元素的成本不会随着受控序列的长度变大而增加。 因此，矢量是模板类[堆栈 （STL/CLR）](../dotnet/stack-stl-clr.md)的基础容器的良好候选项。

支持`vector`随机访问迭代器，这意味着您可以直接引用给定其数值位置的元素，从第一个（正面）元素的零计数到最后`size() - 1`一个（背面）元素。 这也意味着向量是模板类[priority_queue （STL/CLR）](../dotnet/priority-queue-stl-clr.md)的基础容器的良好候选项。

矢量迭代器将句柄存储到其关联的矢量对象，以及它指定的元素的偏差。 只能将迭代器与其关联的容器对象一起使用。 矢量元素的偏置与其位置相同。

插入或删除元素可以更改存储在给定位置的元素值，因此迭代器指定的值也可以更改。 （容器可能必须向上或向下复制元素，才能在插入之前创建孔，或在擦除后填充孔。然而，只要矢量迭代器的偏置在范围内`[0, size()]`，它仍然有效。 此外，有效的迭代器仍然可引用 - 只要其偏差不等于 ，就可以使用它来访问或更改它指定的元素值`size()`。

删除或删除元素将调用析构函数的存储值。 销毁容器会擦除所有元素。 因此，元素类型为 ref 类的容器可确保没有元素比容器寿命大。 但是请注意，句柄的容器不会破坏其元素。

## <a name="members"></a>成员

## <a name="vectorassign-stlclr"></a><a name="assign"></a>矢量：分配（STL/CLR）

替换所有元素。

### <a name="syntax"></a>语法

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>参数

*count*<br/>
要插入的元素数。

*第一*<br/>
要插入的范围的开始。

*最后*<br/>
要插入的范围结束。

*对*<br/>
要插入的枚举。

*瓦尔*<br/>
要插入的元素的值。

### <a name="remarks"></a>备注

第一个成员函数用值*val*的*计数*元素的重复替换受控序列。 使用它填充容器的元素都具有相同的值。

如果是`InIt`整数类型，则第二个成员函数的表示与 相同`assign((size_type)first, (value_type)last)`。 否则，它将受控序列替换为序列 *`first`。 `last` 使用它使受控序列成为另一个序列的副本。

第三个成员函数将受控序列替换为枚举器*右侧*指定的序列。 使用它使受控序列成为枚举器描述序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_vector_assign.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// assign a repetition of values
    cliext::vector<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an iterator range
    c2.assign(c1.begin(), c1.end() - 1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an enumeration
    c2.assign(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
x x x x x x
a b
a b c
```

## <a name="vectorat-stlclr"></a><a name="at"></a>矢量：在 （STL/CLR）

访问指定位置处的元素。

### <a name="syntax"></a>语法

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>参数

*Pos*<br/>
要访问的元素的位置。

### <a name="remarks"></a>备注

成员函数返回对位置*位置*处受控序列元素的引用。您可以使用它读取或写入您知道其位置的元素。

### <a name="example"></a>示例

```cpp
// cliext_vector_at.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using at
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// change an entry and redisplay
    c1.at(1) = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorback-stlclr"></a><a name="back"></a>矢量：回（STL/CLR）

访问最后一个元素。

### <a name="syntax"></a>语法

```cpp
reference back();
```

### <a name="remarks"></a>备注

成员函数返回对受控序列的最后一个元素的引用，该元素必须为非空。 当您知道它存在时，可以使用它访问最后一个元素。

### <a name="example"></a>示例

```cpp
// cliext_vector_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

// alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="vectorback_item-stlclr"></a><a name="back_item"></a>矢量：back_item（STL/CLR）

访问最后一个元素。

### <a name="syntax"></a>语法

```cpp
property value_type back_item;
```

### <a name="remarks"></a>备注

属性访问受控序列的最后一个元素，该元素必须为非空。 当您知道它存在时，可以使用它读取或写入最后一个元素。

### <a name="example"></a>示例

```cpp
// cliext_vector_back_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

// alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="vectorbegin-stlclr"></a><a name="begin"></a>矢量：开始（STL/CLR）

指定受控序列的开头。

### <a name="syntax"></a>语法

```cpp
iterator begin();
```

### <a name="remarks"></a>备注

成员函数返回一个随机访问迭代器，该迭代器指定受控序列的第一个元素，或刚刚超出空序列的末尾。 用于获取一个迭代器，该迭代器指定受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_vector_begin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);

// alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
x y c
```

## <a name="vectorcapacity-stlclr"></a><a name="capacity"></a>矢量：容量（STL/CLR）

报告为容器分配的存储大小。

### <a name="syntax"></a>语法

```cpp
size_type capacity();
```

### <a name="remarks"></a>备注

成员函数返回当前为保存受控序列而分配的存储，该值至少与[矢量：：大小 （STL/CLR）](../dotnet/vector-size-stl-clr.md)`()`一样大。 使用它来确定容器在必须为受控序列重新分配存储之前可以增长多少。

### <a name="example"></a>示例

```cpp
// cliext_vector_capacity.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorclear-stlclr"></a><a name="clear"></a>矢量：清除（STL/CLR）

删除所有元素。

### <a name="syntax"></a>语法

```cpp
void clear();
```

### <a name="remarks"></a>备注

成员函数有效地调用[向量：：擦除 （STL/CLR）](../dotnet/vector-erase-stl-clr.md) `(`[矢量：开始（STL/CLR）](../dotnet/vector-begin-stl-clr.md)`(),`[矢量：：结束 （STL/CLR）](../dotnet/vector-end-stl-clr.md)`())`。 使用它来确保受控序列为空。

### <a name="example"></a>示例

```cpp
// cliext_vector_clear.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

// add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="vectorconst_iterator-stlclr"></a><a name="const_iterator"></a>矢量：const_iterator（STL/CLR）

受控序列的常量迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>备注

类型描述未指定类型`T2`的对象，该对象可用作受控序列的恒定随机访问迭代器。

### <a name="example"></a>示例

```cpp
// cliext_vector_const_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reference-stlclr"></a><a name="const_reference"></a>矢量：const_reference（STL/CLR）

元素的常量引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>备注

类型描述对元素的常量引用。

### <a name="example"></a>示例

```cpp
// cliext_vector_const_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::vector<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>矢量：const_reverse_iterator（STL/CLR）

受控序列的常量反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>备注

类型描述未指定类型`T4`的对象，该对象可用作受控序列的恒定反向迭代器。

### <a name="example"></a>示例

```cpp
// cliext_vector_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="vectordifference_type-stlclr"></a><a name="difference_type"></a>矢量：:d）类型（STL/CLR）

两个元素之间签名距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>备注

类型描述已签名的元素计数。

### <a name="example"></a>示例

```cpp
// cliext_vector_difference_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::difference_type diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.end();
        it != c1.begin(); --it) --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="vectorempty-stlclr"></a><a name="empty"></a>矢量：空（STL/CLR）

测试元素是否存在。

### <a name="syntax"></a>语法

```cpp
bool empty();
```

### <a name="remarks"></a>备注

对于空受控序列，该成员函数返回 true。 它等效于[矢量：大小 （STL/CLR）。](../dotnet/vector-size-stl-clr.md)`() == 0` 使用它来测试矢量是否为空。

### <a name="example"></a>示例

```cpp
// cliext_vector_empty.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="vectorend-stlclr"></a><a name="end"></a>矢量：结束（STL/CLR）

指定受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
iterator end();
```

### <a name="remarks"></a>备注

成员函数返回一个随机访问迭代器，该迭代器的点位于受控序列的末尾之外。 用于获取一个迭代器，该迭代器指定受控序列的 `current` 末尾，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_vector_end.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    cliext::vector<wchar_t>::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);

// alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
a x y
```

## <a name="vectorerase-stlclr"></a><a name="erase"></a>矢量：擦除（STL/CLR）

移除指定位置处的元素。

### <a name="syntax"></a>语法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>参数

*第一*<br/>
要擦除的范围的开始。

*最后*<br/>
要擦除的范围结束。

*其中*<br/>
要擦除的元素。

### <a name="remarks"></a>备注

第一个成员函数删除由*何处*指向的受控序列的元素。 使用它删除单个元素。

第二个成员函数将移除范围 [`first`、`last`) 中的受控序列的元素。 使用它删除零个或多个连续元素。

这两个成员函数返回一个迭代器，该迭代器指定除删除的任何元素之外剩余的第一个元素，或者如果不存在此类元素[，则向量：：end （STL/CLR）。](../dotnet/vector-end-stl-clr.md) `()`

擦除元素时，元素副本的数量在擦除结束和序列近端之间的元素数中是线性的。 （在序列的任意一端执行一个或多个元素时，不会发生元素副本。

### <a name="example"></a>示例

```cpp
// cliext_vector_erase.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

// add elements and display " b c d e"
    c1.push_back(L'd');
    c1.push_back(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase all but end
    cliext::vector<wchar_t>::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="vectorfront-stlclr"></a><a name="front"></a>矢量：前（STL/CLR）

访问第一个元素。

### <a name="syntax"></a>语法

```cpp
reference front();
```

### <a name="remarks"></a>备注

成员函数返回对受控序列的第一个元素的引用，该元素必须为非空。 当您知道它存在时，可以使用它读取或写入第一个元素。

### <a name="example"></a>示例

```cpp
// cliext_vector_front.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

// alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

## <a name="vectorfront_item-stlclr"></a><a name="front_item"></a>矢量：：front_item（STL/CLR）

访问第一个元素。

### <a name="syntax"></a>语法

```cpp
property value_type front_item;
```

### <a name="remarks"></a>备注

属性访问受控序列的第一个元素，该元素必须为非空。 当您知道它存在时，可以使用它读取或写入第一个元素。

### <a name="example"></a>示例

```cpp
// cliext_vector_front_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

// alter first item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

## <a name="vectorgeneric_container-stlclr"></a><a name="generic_container"></a>矢量：generic_container（STL/CLR）

容器的泛型接口的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::
    IVector<generic_value>
    generic_container;
```

### <a name="remarks"></a>备注

类型描述此模板容器类的泛型接口。

### <a name="example"></a>示例

```cpp
// cliext_vector_generic_container.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    gc1->insert(gc1->end(), L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify original and display generic
    c1.push_back(L'e');

    System::Collections::IEnumerator^ enum1 =
        gc1->GetEnumerator();
    while (enum1->MoveNext())
        System::Console::Write("{0} ", enum1->Current);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="vectorgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>矢量：generic_iterator（STL/CLR）

用于容器的泛型接口的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>备注

该类型描述了一个泛型迭代器，该迭代器可与此模板容器类的泛型接口一起使用。

### <a name="example"></a>示例

```cpp
// cliext_vector_generic_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="vectorgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>矢量：generic_reverse_iterator（STL/CLR）

用于容器的泛型接口的反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述了一个通用反向迭代器，该迭代器可与此模板容器类的泛型接口一起使用。

### <a name="example"></a>示例

```cpp
// cliext_vector_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c c
```

## <a name="vectorgeneric_value-stlclr"></a><a name="generic_value"></a>矢量：generic_value（STL/CLR）

用于容器的泛型接口的元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>备注

类型描述类型`GValue`对象，该对象描述存储的元素值，以便与此模板容器类的泛型接口一起使用。

### <a name="example"></a>示例

```cpp
// cliext_vector_generic_value.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="vectorinsert-stlclr"></a><a name="insert"></a>矢量：插入（STL/CLR）

在指定位置添加元素。

### <a name="syntax"></a>语法

```cpp
iterator insert(iterator where, value_type val);
void insert(iterator where, size_type count, value_type val);
template<typename InIt>
    void insert(iterator where, InIt first, InIt last);
void insert(iterator where,
    System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>参数

*count*<br/>
要插入的元素数。

*第一*<br/>
要插入的范围的开始。

*最后*<br/>
要插入的范围结束。

*对*<br/>
要插入的枚举。

*瓦尔*<br/>
要插入的元素的值。

*其中*<br/>
以前在容器中插入的位置。

### <a name="remarks"></a>备注

每个成员函数在元素指向受控序列中*的位置*之前插入由其余操作数指定的序列。

第一个成员函数插入值*val*的元素，并返回指定新插入的元素的迭代器。 使用它在迭代器指定的位置之前插入单个元素。

第二个成员函数插入值*val*的*计数*元素的重复。 使用它插入零个或多个连续元素，这些元素都是相同值的副本。

如果 `InIt` 是整数类型，则第三个成员函数的行为与 `insert(where, (size_type)first, (value_type)last)` 相同。 否则，它将插入序列 *`first`。 `last` 使用它插入从其他序列复制的零个或多个连续元素。

第四个成员函数插入*右侧*指定的序列。 使用它插入枚举器描述的序列。

插入单个元素时，元素副本的数量在插入点和序列的近端之间的元素数中是线性的。 （在序列的任意一端插入一个或多个元素时，不会发生元素副本。如果是`InIt`输入迭代器，则第三个成员函数可有效地对序列中的每个元素执行单个插入。 否则，插入`N`元素时，元素副本的数量是线性的，`N`加上插入点和序列近端之间的元素数。

### <a name="example"></a>示例

```cpp
// cliext_vector_insert.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value using iterator
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a repetition of values
    cliext::vector<wchar_t> c2;
    c2.insert(c2.begin(), 2, L'y');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an iterator range
    it = c1.end();
    c2.insert(c2.end(), c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an enumeration
    c2.insert(c2.begin(),   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(begin()+1, L'x') = x
a x b c
y y
y y a x b
a x b c y y a x b
```

## <a name="vectoriterator-stlclr"></a><a name="iterator"></a>矢量：迭代器（STL/CLR）

受控序列的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>备注

类型描述未指定类型`T1`的对象，该对象可用作受控序列的随机访问迭代器。

### <a name="example"></a>示例

```cpp
// cliext_vector_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();

// alter first element and redisplay
    it = c1.begin();
    *it = L'x';
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x b c
```

## <a name="vectoroperator-stlclr"></a><a name="op_as"></a>矢量：运算符*（STL/CLR）

替换受控序列。

### <a name="syntax"></a>语法

```cpp
vector<Value>% operator=(vector<Value>% right);
```

#### <a name="parameters"></a>参数

*对*<br/>
用于复制的容器。

### <a name="remarks"></a>备注

成员运算符*将右侧*复制到对象，然后返回`*this`。 使用它将受控序列替换为*右侧*受控序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_vector_operator_as.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="vectoroperatorstlclr"></a><a name="op"></a>矢量：运算符（STL/CLR）

访问指定位置处的元素。

### <a name="syntax"></a>语法

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>参数

*Pos*<br/>
要访问的元素的位置。

### <a name="remarks"></a>备注

成员运算符返回位置*位置*的元素的引用。您可以使用它访问您知道其位置的元素。

### <a name="example"></a>示例

```cpp
// cliext_vector_operator_sub.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using subscripting
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();

// change an entry and redisplay
    c1[1] = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorpop_back-stlclr"></a><a name="pop_back"></a>矢量：:pop_back（STL/CLR）

删除最后一个元素。

### <a name="syntax"></a>语法

```cpp
void pop_back();
```

### <a name="remarks"></a>备注

成员函数删除受控序列的最后一个元素，该元素必须为非空。 使用它将矢量缩短到背面的一个元素。

### <a name="example"></a>示例

```cpp
// cliext_vector_pop_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// pop an element and redisplay
    c1.pop_back();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="vectorpush_back-stlclr"></a><a name="push_back"></a>矢量：:push_back（STL/CLR）

添加新的最后一个元素。

### <a name="syntax"></a>语法

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>备注

成员函数在受控序列的末尾插入具有`val`值的元素。 使用它将另一个元素追加到矢量中。

### <a name="example"></a>示例

```cpp
// cliext_vector_push_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorrbegin-stlclr"></a><a name="rbegin"></a>矢量：rbegin（STL/CLR）

指定反向受控序列的开头。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器，该迭代器指定受控序列的最后一个元素，或刚刚超出空序列的开头。 因此，它指定反向序列的 `beginning`。 用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_vector_rbegin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);

// alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
a y x
```

## <a name="vectorreference-stlclr"></a><a name="reference"></a>矢量：参考（STL/CLR）

元素的引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>备注

类型描述对元素的引用。

### <a name="example"></a>示例

```cpp
// cliext_vector_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

// modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;

        ref += (wchar_t)(L'A' - L'a');
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
A B C
```

## <a name="vectorrend-stlclr"></a><a name="rend"></a>矢量：rend（STL/CLR）

指定反向受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器，该迭代器的点位于受控序列的开头之外。 因此，它指定反向序列的 `end`。 用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 末尾，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_vector_rend.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);

// alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
y x c
```

## <a name="vectorreserve-stlclr"></a><a name="reserve"></a>矢量：保留（STL/CLR）

确保容器的最低增长能力。

### <a name="syntax"></a>语法

```cpp
void reserve(size_type count);
```

#### <a name="parameters"></a>参数

*count*<br/>
容器的新最小容量。

### <a name="remarks"></a>备注

成员函数确保`capacity()`从此返回至少*计数*。 使用它可确保容器在增长到指定大小之前无需重新分配受控序列的存储。

### <a name="example"></a>示例

```cpp
// cliext_vector_reserve.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorresize-stlclr"></a><a name="resize"></a>矢量：调整大小（STL/CLR）

更改元素的数量。

### <a name="syntax"></a>语法

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>参数

*new_size*<br/>
受控序列的新大小。

*瓦尔*<br/>
填充元素的值。

### <a name="remarks"></a>备注

成员函数都确保从今以后[向量：：大小（STL/CLR）](../dotnet/vector-size-stl-clr.md)`()`返回*new_size*。 如果必须延长受控序列，则第一个成员函数将值`value_type()`追加元素，而第二个成员函数则追加值为*val*的元素。 为了使受控序列变短，两个成员函数都有效地擦除最后一个元素[矢量：：大小 （STL/CLR）](../dotnet/vector-size-stl-clr.md)`() -``new_size`时间。 使用它通过修剪或填充当前受控序列来确保受控序列*的大小new_size。*

### <a name="example"></a>示例

```cpp
// cliext_vector_resize.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container and pad with default values
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());
    c1.resize(4);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// resize to empty
    c1.resize(0);
    System::Console::WriteLine("size() = {0}", c1.size());

// resize and pad
    c1.resize(5, L'x');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
0 0 0 0
size() = 0
x x x x x
```

## <a name="vectorreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>矢量：reverse_iterator（STL/CLR）

受控序列的反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_vector_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();

// alter first element and redisplay
    rit = c1.rbegin();
    *rit = L'x';
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
x b a
```

## <a name="vectorsize-stlclr"></a><a name="size"></a>矢量：大小（STL/CLR）

对元素数进行计数。

### <a name="syntax"></a>语法

```cpp
size_type size();
```

### <a name="remarks"></a>备注

成员函数将返回受控序列的长度。 使用它来确定当前受控序列中的元素数。 如果您关心的只是序列是否具有非零大小，请参阅[矢量：空 （STL/CLR）。](../dotnet/vector-empty-stl-clr.md)`()`

### <a name="example"></a>示例

```cpp
// cliext_vector_size.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

// add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="vectorsize_type-stlclr"></a><a name="size_type"></a>矢量：：size_type（STL/CLR）

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>备注

类型描述非负元素计数。

### <a name="example"></a>示例

```cpp
// cliext_vector_size_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="vectorswap-stlclr"></a><a name="swap"></a>矢量：交换（STL/CLR）

交换两个容器的内容。

### <a name="syntax"></a>语法

```cpp
void swap(vector<Value>% right);
```

#### <a name="parameters"></a>参数

*对*<br/>
要与其交换内容的容器。

### <a name="remarks"></a>备注

成员函数交换*和*之间的`*this`受控序列。 它在恒定时间内这样做，并且不会引发任何异常。 使用它作为交换两个容器内容的快速方法。

### <a name="example"></a>示例

```cpp
// cliext_vector_swap.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::vector<wchar_t> c2(5, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="vectorto_array-stlclr"></a><a name="to_array"></a>矢量：：to_array（STL/CLR）

将受控序列复制到新数组。

### <a name="syntax"></a>语法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>备注

成员函数返回包含受控序列的数组。 使用它以数组形式获取受控序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_vector_to_array.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push_back(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="vectorvalue_type-stlclr"></a><a name="value_type"></a>矢量：value_type（STL/CLR）

元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>备注

类型是模板参数*值*的同义词。

### <a name="example"></a>示例

```cpp
// cliext_vector_value_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using value_type
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::vector<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorvector-stlclr"></a><a name="vector"></a>矢量：矢量（STL/CLR）

构造容器对象。

### <a name="syntax"></a>语法

```cpp
vector();
vector(vector<Value>% right);
vector(vector<Value>^ right);
explicit vector(size_type count);
vector(size_type count, value_type val);
template<typename InIt>
    vector(InIt first, InIt last);
vector(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>参数

*count*<br/>
要插入的元素数。

*第一*<br/>
要插入的范围的开始。

*最后*<br/>
要插入的范围结束。

*对*<br/>
要插入的对象或范围。

*瓦尔*<br/>
要插入的元素的值。

### <a name="remarks"></a>备注

构造函数：

`vector();`

初始化受控序列，无元素。 使用它指定空的初始控制序列。

构造函数：

`vector(vector<Value>% right);`

使用序列 *`right.begin()`初始化受控序列 。 `right.end()` 使用它指定初始受控序列，该序列是矢量对象*右侧*控制序列的副本。

构造函数：

`vector(vector<Value>^ right);`

使用序列 *`right->begin()`初始化受控序列 。 `right->end()` 使用它指定初始受控序列，该序列是由句柄*正确的*矢量对象控制的序列的副本。

构造函数：

`explicit vector(size_type count);`

用计数元素为每个具有值`value_type()`的*计数*元素初始化受控序列。 使用它填充容器的元素都具有默认值。

构造函数：

`vector(size_type count, value_type val);`

用值*val*的*计数*元素初始化受控序列。 使用它填充容器的元素都具有相同的值。

构造函数：

`template<typename InIt>`

`vector(InIt first, InIt last);`

使用序列 *`first`初始化受控序列 。 `last` 使用它使受控序列成为另一个序列的副本。

构造函数：

`vector(System::Collections::Generic::IEnumerable<Value>^ right);`

使用枚举器*右侧*指定的序列初始化受控序列。 使用它使受控序列成为枚举器描述的另一个序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_vector_construct.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct with a repetition of default values
    cliext::vector<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// construct with a repetition of values
    cliext::vector<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    cliext::vector<wchar_t>::iterator it = c3.end();
    cliext::vector<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    cliext::vector<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying a container handle
    cliext::vector<wchar_t> c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
0 0 0
x x x x x x
x x x x x
x x x x x x
x x x x x x
x x x x x x
```

## <a name="operator-vector-stlclr"></a><a name="op_neq"></a>运算符！* （矢量） （STL/CLR）

矢量不相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator!=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左容器。

*对*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`!(left == right)`。 使用它来测试当按元素比较两个矢量时，*左的*排序是否与*右侧*相同。

### <a name="example"></a>示例

```cpp
// cliext_vector_operator_ne.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-vector-stlclr"></a><a name="op_lt"></a>运算符&lt;（矢量） （STL/CLR）

矢量小于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator<(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左容器。

*对*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

如果 对于最低位置`i``!(right[i] < left[i])`，运算符函数返回`left[i] < right[i]`true， 如果 。 否则，它返回`left->size() < right->size()`"使用它"来测试在按元素比较两个矢量之前是否*对**左*排序。

### <a name="example"></a>示例

```cpp
// cliext_vector_operator_lt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-vector-stlclr"></a><a name="op_lteq"></a>运算符&lt;= （矢量） （STL/CLR）

矢量小于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator<=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左容器。

*对*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`!(right < left)`。 使用它来测试在按元素比较两个矢量时，*是否*未*在右后右*排序。

### <a name="example"></a>示例

```cpp
// cliext_vector_operator_le.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-vector-stlclr"></a><a name="op_eq"></a>运算符* （矢量） （STL/CLR）

矢量相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator==(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左容器。

*对*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

仅当*由左右*控制的顺序长度相同*right*且每个位置`i``left[i] ==``right[i]`具有相同的长度时，运算符函数才会返回 true。 使用它来测试当按元素比较两个矢量时，*左的*排序是否与*右侧*相同。

### <a name="example"></a>示例

```cpp
// cliext_vector_operator_eq.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-vector-stlclr"></a><a name="op_gt"></a>运算符&gt;（矢量） （STL/CLR）

矢量大于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator>(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左容器。

*对*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`right``<``left`。 使用它来测试在按元素比较两个矢量时 *，左是否*按*右*顺序排列。

### <a name="example"></a>示例

```cpp
// cliext_vector_operator_gt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-vector-stlclr"></a><a name="op_gteq"></a>运算符&gt;= （矢量） （STL/CLR）

矢量大于或相等的比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator>=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>参数

*离开*<br/>
要比较的左容器。

*对*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`!(left < right)`。 使用它来测试在按元素比较两个矢量*之前是否*未对*左侧*进行排序。

### <a name="example"></a>示例

```cpp
// cliext_vector_operator_ge.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
