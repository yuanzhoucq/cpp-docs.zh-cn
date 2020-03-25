---
title: deque (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::deque
- cliext::deque::assign
- cliext::deque::at
- cliext::deque::back
- cliext::deque::back_item
- cliext::deque::begin
- cliext::deque::clear
- cliext::deque::const_iterator
- cliext::deque::const_reference
- cliext::deque::const_reverse_iterator
- cliext::deque::deque
- cliext::deque::difference_type
- cliext::deque::empty
- cliext::deque::end
- cliext::deque::erase
- cliext::deque::front
- cliext::deque::front_item
- cliext::deque::generic_container
- cliext::deque::generic_iterator
- cliext::deque::generic_reverse_iterator
- cliext::deque::generic_value
- cliext::deque::insert
- cliext::deque::iterator
- cliext::deque::operator!=
- cliext::deque::operator[]
- cliext::deque::pop_back
- cliext::deque::pop_front
- cliext::deque::push_back
- cliext::deque::push_front
- cliext::deque::rbegin
- cliext::deque::reference
- cliext::deque::rend
- cliext::deque::resize
- cliext::deque::reverse_iterator
- cliext::deque::size
- cliext::deque::size_type
- cliext::deque::swap
- cliext::deque::to_array
- cliext::deque::value_type
- cliext::deque::operator<
- cliext::deque::operator<=
- cliext::deque::operator=
- cliext::deque::operator==
- cliext::deque::operator>
- cliext::deque::operator>=
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- deque member [STL/CLR]
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
- operator!= member [STL/CLR]
- operator member [] [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
ms.openlocfilehash: 74fb98d99e0aba94c40dce9ad1bcd6af83394231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208762"
---
# <a name="deque-stlclr"></a>deque (STL/CLR)

此模板类描述一个对象，该对象控制具有随机访问权限的、长度可变的元素序列。 可以使用容器 `deque` 来管理类似于连续存储块的一系列元素，但这两个元素可以在一端增长或收缩，而无需复制任何剩余元素。 因此，它可以有效地实现 `double-ended queue`。 （因此，名称为。）

在下面的说明中，`GValue` 与 `Value` 相同，除非后者为 ref 类型，在这种情况下，它是 `Value^`的。

## <a name="syntax"></a>语法

```cpp
template<typename Value>
    ref class deque
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IDeque<GValue>
    { ..... };
```

### <a name="parameters"></a>parameters

*GValue*<br/>
受控序列中的元素的泛型类型。

*值*<br/>
受控序列中的元素的类型。

## <a name="requirements"></a>要求

**标头：** \<cliext/deque >

**命名空间：** cliext

## <a name="declarations"></a>声明

|类型定义|说明|
|---------------------|-----------------|
|[deque::const_iterator (STL/CLR)](#const_iterator)|受控序列的常量迭代器的类型。|
|[deque::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|
|[deque::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|
|[deque::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|
|[deque::generic_container (STL/CLR)](#generic_container)|容器的泛型接口的类型。|
|[deque::generic_iterator (STL/CLR)](#generic_iterator)|容器的泛型接口的迭代器的类型。|
|[deque::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型接口的反向迭代器的类型。|
|[deque::generic_value (STL/CLR)](#generic_value)|容器的泛型接口的元素类型。|
|[deque::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|
|[deque::reference (STL/CLR)](#reference)|元素的引用的类型。|
|[deque::reverse_iterator (STL/CLR)](#reverse_iterator)|受控序列的反向迭代器的类型。|
|[deque::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|
|[deque::value_type (STL/CLR)](#value_type)|元素的类型。|

|成员函数|说明|
|---------------------|-----------------|
|[deque::assign (STL/CLR)](#assign)|替换所有元素。|
|[deque::at (STL/CLR)](#at)|访问指定位置处的元素。|
|[deque::back (STL/CLR)](#back)|访问最后一个元素。|
|[deque::begin (STL/CLR)](#begin)|指定受控序列的开头。|
|[deque::clear (STL/CLR)](#clear)|删除所有元素。|
|[deque::deque (STL/CLR)](#deque)|构造容器对象。|
|[deque::empty (STL/CLR)](#empty)|测试元素是否存在。|
|[deque::end (STL/CLR)](#end)|指定受控序列的末尾。|
|[deque::erase (STL/CLR)](#erase)|移除指定位置处的元素。|
|[deque::front (STL/CLR)](#front)|访问第一个元素。|
|[deque::insert (STL/CLR)](#insert)|在指定位置添加元素。|
|[deque::pop_back (STL/CLR)](#pop_back)|删除最后一个元素。|
|[deque::pop_front (STL/CLR)](#pop_front)|删除第一个元素。|
|[deque::push_back (STL/CLR)](#push_back)|添加新的最后一个元素。|
|[deque::push_front (STL/CLR)](#push_front)|添加新的第一个元素。|
|[deque::rbegin (STL/CLR)](#rbegin)|指定反向受控序列的开头。|
|[deque::rend (STL/CLR)](#rend)|指定反向受控序列的末尾。|
|[deque::resize (STL/CLR)](#resize)|更改元素的数量。|
|[deque::size (STL/CLR)](#size)|对元素数进行计数。|
|[deque::swap (STL/CLR)](#swap)|交换两个容器的内容。|
|[deque::to_array (STL/CLR)](#to_array)|将受控序列复制到新数组。|

|properties|说明|
|--------------|-----------------|
|[deque::back_item (STL/CLR)](#back_item)|访问最后一个元素。|
|[deque::front_item (STL/CLR)](#front_item)|访问第一个元素。|

|操作员|说明|
|--------------|-----------------|
|[deque::operator!= (STL/CLR)](#op_neq)|确定两个 `deque` 对象是否不相等。|
|[deque::operator(STL/CLR)](#operator)|访问指定位置处的元素。|
|[operator< (deque) (STL/CLR)](#op_lt)|确定 `deque` 对象是否小于另一个 `deque` 对象。|
|[operator<= (deque) (STL/CLR)](#op_lteq)|确定 `deque` 对象是否小于或等于另一个 `deque` 对象。|
|[operator= (deque) (STL/CLR)](#op_as)|替换受控序列。|
|[operator== (deque) (STL/CLR)](#op_eq)|确定 `deque` 对象是否等于另一个 `deque` 对象。|
|[operator> (deque) (STL/CLR)](#op_gt)|确定 `deque` 对象是否大于另一个 `deque` 对象。|
|[operator>= (deque) (STL/CLR)](#op_gteq)|确定 `deque` 对象是否大于或等于另一个 `deque` 对象。|

## <a name="interfaces"></a>界面

|接口|说明|
|---------------|-----------------|
|<xref:System.ICloneable>|复制对象。|
|<xref:System.Collections.IEnumerable>|通过元素进行排序。|
|<xref:System.Collections.ICollection>|维护元素组。|
|<xref:System.Collections.Generic.IEnumerable%601>|通过类型化元素进行排序。|
|<xref:System.Collections.Generic.ICollection%601>|维护类型化元素组。|
|<xref:System.Collections.Generic.IList%601>|维护类型化元素的有序组。|
|IDeque < 值\>|维护泛型容器。|

## <a name="remarks"></a>备注

对象为其控制的序列分配并释放存储，并通过存储的句柄数组指定 `Value` 元素块。 阵列按需增长。 增长发生的方式是：预先计算或追加新元素的成本是固定时间，并且不会干扰剩余的元素。 你还可以在常量时间结束时删除元素，而不会干扰剩余元素。 因此，deque 非常适合用于模板类[队列（stl/clr）](../dotnet/queue-stl-clr.md)或模板类[堆栈（stl/clr）](../dotnet/stack-stl-clr.md)的基础容器。

`deque` 对象支持随机访问迭代器，这意味着，可以直接引用元素的数值位置，从零开始，为最后一个（后端）元素计算[deque：： size （STL/CLR）](#size)`() - 1`。 这也意味着 deque 非常适合用于模板类[priority_queue （STL/CLR）](../dotnet/priority-queue-stl-clr.md)的基础容器。

Deque 迭代器将句柄存储到其关联的 deque 对象，以及它指定的元素的偏移量。 只能将迭代器与其关联的容器对象一起使用。 Deque 元素的偏移*不*一定与其位置相同。 插入的第一个元素的偏移量为零，下一个追加的元素的偏移量为1，但下一个预置元素的偏移量为-1。

在任一端插入或删除元素时，*不*会更改存储在任何有效偏移上的元素的值。 但是，插入或删除内部元素*可以*更改在给定偏移量下存储的元素值，因此由迭代器指定的值也可以更改。 （容器可能需要复制元素以在插入前创建孔洞，或在擦除后填充孔。）尽管如此，只要 deque 迭代器的偏差指定了有效的元素，它就会保持有效。 而且，有效的迭代器仍 dereferencable，可以使用它来访问或更改它指定的元素值，只要其偏差不等于 `end()`返回的迭代器的偏移量。

清除或删除元素会调用析构函数以获取其存储的值。 销毁容器将清除所有元素。 因此，其元素类型为 ref 类的容器可确保没有元素长于容器。 但请注意，句柄的容器*不*会销毁其元素。

## <a name="members"></a>成员

## <a name="dequeassign-stlclr"></a><a name="assign"></a>deque：： assign （STL/CLR）

替换所有元素。

### <a name="syntax"></a>语法

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>parameters

*计数*<br/>
要插入的元素数。

*first*<br/>
要插入的范围的开头。

*last*<br/>
要插入的范围的末尾。

right<br/>
要插入的枚举。

*val*<br/>
要插入的元素的值。

### <a name="remarks"></a>备注

第一个成员函数会将受控序列替换为值*val*的*计数*元素的重复。 使用它可以将具有相同值的元素填充到容器中。

如果 `InIt` 是整数类型，则第二个成员函数的行为与 `assign((size_type)first, (value_type)last)`相同。 否则，它会将受控序列替换为序列 [`first`，`last`）。 用于使受控序列成为副本的另一个序列。

第三个成员函数将受控序列替换*为枚举器*指定的序列。 用于使受控序列成为枚举器所描述的序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_deque_assign.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::deque<wchar_t> c2;
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

## <a name="dequeat-stlclr"></a><a name="at"></a>deque：： at （STL/CLR）

访问指定位置处的元素。

### <a name="syntax"></a>语法

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>parameters

pos<br/>
要访问的元素的位置。

### <a name="remarks"></a>备注

成员函数返回*对位置位置*的受控序列的元素的引用。使用它可读取或写入您知道的位置的元素。

### <a name="example"></a>示例

```cpp
// cliext_deque_at.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeback-stlclr"></a><a name="back"></a>deque：： back （STL/CLR）

访问最后一个元素。

### <a name="syntax"></a>语法

```cpp
reference back();
```

### <a name="remarks"></a>备注

成员函数返回对受控序列的最后一个元素的引用，该元素必须为非空。 当您知道最后一个元素存在时，可以使用它来访问最后一个元素。

### <a name="example"></a>示例

```cpp
// cliext_deque_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeback_item-stlclr"></a><a name="back_item"></a>deque：： back_item （STL/CLR）

访问最后一个元素。

### <a name="syntax"></a>语法

```cpp
property value_type back_item;
```

### <a name="remarks"></a>备注

属性访问受控序列的最后一个元素，该元素必须为非空。 当您知道最后一个元素存在时，可以使用它读取或写入该元素。

### <a name="example"></a>示例

```cpp
// cliext_deque_back_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequebegin-stlclr"></a><a name="begin"></a>deque：： begin （STL/CLR）

指定受控序列的开头。

### <a name="syntax"></a>语法

```cpp
iterator begin();
```

### <a name="remarks"></a>备注

此成员函数返回一个随机访问迭代器，该迭代器指定受控序列的第一个元素，或刚超出空序列的末尾。 用于获取一个迭代器，该迭代器指定受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_deque_begin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::iterator it = c1.begin();
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

## <a name="dequeclear-stlclr"></a><a name="clear"></a>deque：： clear （STL/CLR）

删除所有元素。

### <a name="syntax"></a>语法

```cpp
void clear();
```

### <a name="remarks"></a>备注

成员函数有效地调用[deque：： erase （stl/clr）](#erase)`(` [deque：： begin](#begin) （stl/clr）`(),` [DEQUE：： end （stl](#end) /clr）`())`。 用于确保受控序列为空。

### <a name="example"></a>示例

```cpp
// cliext_deque_clear.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeconst_iterator-stlclr"></a><a name="const_iterator"></a>deque：： const_iterator （STL/CLR）

受控序列的常量迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>备注

该类型描述可用作受控序列的常量随机访问迭代器的未指定类型 `T2` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_deque_const_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="dequeconst_reference-stlclr"></a><a name="const_reference"></a>deque：： const_reference （STL/CLR）

元素的常量引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>备注

类型描述对元素的常量引用。

### <a name="example"></a>示例

```cpp
// cliext_deque_const_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::deque<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="dequeconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>deque：： const_reverse_iterator （STL/CLR）

受控序列的常量反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述可用作受控序列的常量反向迭代器的未指定类型 `T4` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_deque_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::deque<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="dequedeque-stlclr"></a><a name="deque"></a>deque：:d eque （STL/CLR）

构造容器对象。

### <a name="syntax"></a>语法

```cpp
deque();
deque(deque<Value>% right);
deque(deque<Value>^ right);
explicit deque(size_type count);
deque(size_type count, value_type val);
template<typename InIt>
    deque(InIt first, InIt last);
deque(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>parameters

*计数*<br/>
要插入的元素数。

*first*<br/>
要插入的范围的开头。

*last*<br/>
要插入的范围的末尾。

right<br/>
要插入的对象或范围。

*val*<br/>
要插入的元素的值。

### <a name="remarks"></a>备注

构造函数：

`deque();`

初始化没有元素的受控序列。 用于指定空的初始受控序列。

构造函数：

`deque(deque<Value>% right);`

用序列 [`right.begin()`，`right.end()`）初始化受控序列。 用于指定初始受控序列，该序列是由 deque 对象*权限*控制的序列的副本。 有关迭代器的详细信息，请参阅[deque：： begin （stl/clr）](#begin)和[deque：： end （stl/clr）](#end)。

构造函数：

`deque(deque<Value>^ right);`

用序列 [`right->begin()`，`right->end()`）初始化受控序列。 用于指定初始受控序列，该序列是由 deque 对象（其句柄是*正确*的）所控制的序列的副本。

构造函数：

`explicit deque(size_type count);`

初始化受控序列 *，其中每个元素都*具有值 `value_type()`。 使用它可以使用具有默认值的元素填充容器。

构造函数：

`deque(size_type count, value_type val);`

用每*个值为值的* *计数*元素初始化受控序列。 使用它可以将具有相同值的元素填充到容器中。

构造函数：

`template<typename InIt>`

`deque(InIt first, InIt last);`

用序列 [`first`，`last`）初始化受控序列。 用于使受控序列成为另一个序列的副本。

构造函数：

`deque(System::Collections::Generic::IEnumerable<Value>^ right);`

使用枚举器*权限*指定的序列初始化受控序列。 用于使受控序列成为枚举器所描述的另一序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_deque_construct.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container
    cliext::deque<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::deque<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::deque<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::deque<wchar_t>::iterator it = c3.end();
    cliext::deque<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::deque<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::deque<wchar_t> c8(%c3);
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

## <a name="dequedifference_type-stlclr"></a><a name="difference_type"></a>deque：:d ifference_type （STL/CLR）

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>备注

类型描述有符号的元素计数。

### <a name="example"></a>示例

```cpp
// cliext_deque_difference_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::difference_type diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequeempty-stlclr"></a><a name="empty"></a>deque：： empty （STL/CLR）

测试元素是否存在。

### <a name="syntax"></a>语法

```cpp
bool empty();
```

### <a name="remarks"></a>备注

对于空受控序列，该成员函数返回 true。 它等效于[deque：： size （STL/CLR）](#size)`() == 0`。 用于测试 deque 是否为空。

### <a name="example"></a>示例

```cpp
// cliext_deque_empty.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeend-stlclr"></a><a name="end"></a>deque：： end （STL/CLR）

指定受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
iterator end();
```

### <a name="remarks"></a>备注

成员函数返回一个随机访问迭代器，它指向刚超出受控序列末尾的位置。 用于获取一个迭代器，该迭代器指定受控序列的 `current` 末尾，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_deque_end.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequeerase-stlclr"></a><a name="erase"></a>deque：： erase （STL/CLR）

移除指定位置处的元素。

### <a name="syntax"></a>语法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>parameters

*first*<br/>
要清除的范围的开头。

*last*<br/>
要清除的范围的结束。

*where*<br/>
要清除的元素。

### <a name="remarks"></a>备注

第一个成员函数删除由*where*指向的受控序列的元素。 使用它可以删除单个元素。

第二个成员函数将移除范围 [`first`、`last`) 中的受控序列的元素。 使用它可以删除零个或多个连续元素。

这两个成员函数都返回一个迭代器，该迭代器指定在删除的任何元素之外保留的第一个元素; 如果不存在此类元素，则为[deque：： end （STL/CLR）](#end)`()`

擦除元素时，元素副本的数目在擦除结束和序列的最近结束之间的元素数中是线性的。 （在序列的任一端删除一个或多个元素时，不会发生元素复制。）

### <a name="example"></a>示例

```cpp
// cliext_deque_erase.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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
    cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequefront-stlclr"></a><a name="front"></a>deque：： front （STL/CLR）

访问第一个元素。

### <a name="syntax"></a>语法

```cpp
reference front();
```

### <a name="remarks"></a>备注

成员函数返回对受控序列中第一个元素的引用，该元素必须为非空。 你可以使用它来读取或写入第一个元素（如果你知道存在该元素）。

### <a name="example"></a>示例

```cpp
// cliext_deque_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequefront_item-stlclr"></a><a name="front_item"></a>deque：： front_item （STL/CLR）

访问第一个元素。

### <a name="syntax"></a>语法

```cpp
property value_type front_item;
```

### <a name="remarks"></a>备注

属性访问受控序列中的第一个元素，该元素必须为非空。 你可以使用它来读取或写入第一个元素（如果你知道存在该元素）。

### <a name="example"></a>示例

```cpp
// cliext_deque_front_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequegeneric_container-stlclr"></a><a name="generic_container"></a>deque：： generic_container （STL/CLR）

容器的泛型接口的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::
    IDeque<generic_value>
    generic_container;
```

### <a name="remarks"></a>备注

类型描述此模板容器类的泛型接口。

### <a name="example"></a>示例

```cpp
// cliext_deque_generic_container.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="dequegeneric_iterator-stlclr"></a><a name="generic_iterator"></a>deque：： generic_iterator （STL/CLR）

与容器的泛型接口一起使用的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value> generic_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可与此模板容器类的泛型接口一起使用的泛型迭代器。

### <a name="example"></a>示例

```cpp
// cliext_deque_generic_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="dequegeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>deque：： generic_reverse_iterator （STL/CLR）

用于容器的泛型接口的反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可与此模板容器类的泛型接口一起使用的一般反向迭代器。

### <a name="example"></a>示例

```cpp
// cliext_deque_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="dequegeneric_value-stlclr"></a><a name="generic_value"></a>deque：： generic_value （STL/CLR）

用于容器的泛型接口的元素类型。

### <a name="syntax"></a>语法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>备注

该类型描述了一个 `GValue` 类型的对象，该对象描述用于此模板容器类的泛型接口的存储元素值。

### <a name="example"></a>示例

```cpp
// cliext_deque_generic_value.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="dequeinsert-stlclr"></a><a name="insert"></a>deque：： insert （STL/CLR）

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

#### <a name="parameters"></a>parameters

*计数*<br/>
要插入的元素数。

*first*<br/>
要插入的范围的开头。

*last*<br/>
要插入的范围的末尾。

right<br/>
要插入的枚举。

*val*<br/>
要插入的元素的值。

*where*<br/>
要插入到的容器中的位置。

### <a name="remarks"></a>备注

每个成员函数在由控制的序列中的*位置*指向的元素之前，插入由剩余操作数指定的序列。

第一个成员函数插入具有值*val*的元素，并返回指定新插入的元素的迭代器。 用于在迭代器指定的位置之前插入单个元素。

第二个成员函数插入值*val*的*计数*元素的重复。 使用它可以插入零个或多个连续元素，这些元素是同一值的所有副本。

如果 `InIt` 是整数类型，则第三个成员函数的行为与 `insert(where, (size_type)first, (value_type)last)` 相同。 否则，将插入序列 [`first`，`last`）。 使用它可以插入从另一个序列复制的零个或多个连续元素。

第四个成员函数插入由*权限*指定的序列。 使用它可以插入枚举器描述的序列。

在插入单个元素时，元素副本的数目在插入点与序列的最近结束之间的元素数中是线性的。 （在序列的任一端插入一个或多个元素时，不会发生元素复制。）如果 `InIt` 是输入迭代器，则第三个成员函数将为序列中的每个元素有效地执行单个插入。 否则，在插入 `N` 元素时，元素副本的数目在 `N` 加上插入点与序列的最近结束之间的元素数为线性。

### <a name="example"></a>示例

```cpp
// cliext_deque_insert.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::deque<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::deque<wchar_t> c2;
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

## <a name="dequeiterator-stlclr"></a><a name="iterator"></a>deque：： iterator （STL/CLR）

受控序列的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>备注

该类型描述可用作受控序列的随机访问迭代器的未指定类型 `T1` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_deque_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
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

## <a name="dequeoperator-stlclr"></a><a name="op_neq"></a>deque：： operator！ = （STL/CLR）

Deque 不等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator!=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>parameters

*left*<br/>
要比较的左容器。

right<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `!(left == right)`。 使用此方法可以测试在按元素对两个 deque 进行*比较时，是否按原样对* *左侧*进行排序。

### <a name="example"></a>示例

```cpp
// cliext_deque_operator_ne.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="dequeoperatorstlclr"></a><a name="operator"></a>deque：： operator （STL/CLR）

访问指定位置处的元素。

### <a name="syntax"></a>语法

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>parameters

pos<br/>
要访问的元素的位置。

### <a name="remarks"></a>备注

成员运算符返回 referene*位置处的元素。* 使用它可以访问您知道的位置的元素。

### <a name="example"></a>示例

```cpp
// cliext_deque_operator_sub.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepop_back-stlclr"></a><a name="pop_back"></a>deque：:p op_back （STL/CLR）

删除最后一个元素。

### <a name="syntax"></a>语法

```cpp
void pop_back();
```

### <a name="remarks"></a>备注

成员函数删除受控序列中的最后一个元素，该元素必须为非空。 您可以使用它来缩短后面一个元素的 deque。

### <a name="example"></a>示例

```cpp
// cliext_deque_pop_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepop_front-stlclr"></a><a name="pop_front"></a>deque：:p op_front （STL/CLR）

删除第一个元素。

### <a name="syntax"></a>语法

```cpp
void pop_front();
```

### <a name="remarks"></a>备注

成员函数删除受控序列中的第一个元素，该元素必须为非空。 使用它可以缩短前一个元素的 deque。

### <a name="example"></a>示例

```cpp
// cliext_deque_pop_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_front();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
b c
```

## <a name="dequepush_back-stlclr"></a><a name="push_back"></a>deque：:p ush_back （STL/CLR）

添加新的最后一个元素。

### <a name="syntax"></a>语法

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>备注

此成员函数在受控序列的末尾插入一个具有值 `val` 的元素。 使用它可以向 deque 中追加另一个元素。

### <a name="example"></a>示例

```cpp
// cliext_deque_push_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepush_front-stlclr"></a><a name="push_front"></a>deque：:p ush_front （STL/CLR）

添加新的第一个元素。

### <a name="syntax"></a>语法

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>备注

此成员函数在受控序列的开头插入一个具有值 `val` 的元素。 使用此方法可以将另一个元素预置到 deque。

### <a name="example"></a>示例

```cpp
// cliext_deque_push_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_front(L'a');
    c1.push_front(L'b');
    c1.push_front(L'c');

    // display contents " c b a"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="dequerbegin-stlclr"></a><a name="rbegin"></a>deque：： rbegin （STL/CLR）

指定反向受控序列的开头。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器，该迭代器指定受控序列的最后一个元素，或刚超出空序列的开头。 因此，它指定反向序列的 `beginning`。 用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_deque_rbegin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="dequereference-stlclr"></a><a name="reference"></a>deque：： reference （STL/CLR）

元素的引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>备注

类型描述对元素的引用。

### <a name="example"></a>示例

```cpp
// cliext_deque_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;

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

## <a name="dequerend-stlclr"></a><a name="rend"></a>deque：： rend （STL/CLR）

指定反向受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器，该迭代器指向刚刚超出受控序列的开头。 因此，它指定反向序列的 `end`。 用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 末尾，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_deque_rend.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="dequeresize-stlclr"></a><a name="resize"></a>deque：： resize （STL/CLR）

更改元素的数量。

### <a name="syntax"></a>语法

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>parameters

*new_size*<br/>
受控序列的新大小。

*val*<br/>
填充元素的值。

### <a name="remarks"></a>备注

成员函数确保[deque：： size （STL/CLR）](#size)`()` 之后返回*new_size*。 如果它必须使受控序列更长，则第一个成员函数将追加值为 `value_type()`的元素，而第二个成员函数则追加值为*val*的元素。 为了使受控序列更短，两个成员函数将有效地清除最后一个元素[deque：： size （STL/CLR）](#size)`() -` `new_size` 时间。 使用它可以通过修整或填充当前受控序列来确保受控序列*new_size*大小。

### <a name="example"></a>示例

```cpp
// cliext_deque_resize.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container and pad with default values
    cliext::deque<wchar_t> c1;
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

## <a name="dequereverse_iterator-stlclr"></a><a name="reverse_iterator"></a>deque：： reverse_iterator （STL/CLR）

受控序列的反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_deque_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="dequesize-stlclr"></a><a name="size"></a>deque：： size （STL/CLR）

对元素数进行计数。

### <a name="syntax"></a>语法

```cpp
size_type size();
```

### <a name="remarks"></a>备注

成员函数将返回受控序列的长度。 用于确定受控序列中当前的元素数。 如果你只关心序列的大小是否为非零，请参阅[deque：： empty （STL/CLR）](#empty)`()`。

### <a name="example"></a>示例

```cpp
// cliext_deque_size.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequesize_type-stlclr"></a><a name="size_type"></a>deque：： size_type （STL/CLR）

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>备注

该类型描述了一个非负元素计数。

### <a name="example"></a>示例

```cpp
// cliext_deque_size_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="dequeswap-stlclr"></a><a name="swap"></a>deque：： swap （STL/CLR）

交换两个容器的内容。

### <a name="syntax"></a>语法

```cpp
void swap(deque<Value>% right);
```

#### <a name="parameters"></a>parameters

right<br/>
要与其交换内容的容器。

### <a name="remarks"></a>备注

成员函数在 `*this` 和*右*之间交换受控序列。 它在固定时间内执行此操作，并且不会引发异常。 使用该方法可以快速交换两个容器的内容。

### <a name="example"></a>示例

```cpp
// cliext_deque_swap.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> c2(5, L'x');
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

## <a name="dequeto_array-stlclr"></a><a name="to_array"></a>deque：： to_array （STL/CLR）

将受控序列复制到新数组。

### <a name="syntax"></a>语法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>备注

此成员函数返回包含受控序列的数组。 可以使用它以数组形式获取受控序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_deque_to_array.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequevalue_type-stlclr"></a><a name="value_type"></a>deque：： value_type （STL/CLR）

元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>备注

该类型是模板参数*值*的同义词。

### <a name="example"></a>示例

```cpp
// cliext_deque_value_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::deque<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operatorlt-deque-stlclr"></a><a name="op_lt"></a>operator&lt; （deque）（STL/CLR）

Deque 小于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator<(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>parameters

*left*<br/>
要比较的左容器。

right<br/>
要比较的右容器。

### <a name="remarks"></a>备注

如果为，则运算符函数将返回 true，以便为其 `!(right[i] < left[i])` `i` 也为 `left[i] < right[i]`。 否则，它将返回 `left->size() < right->size()` 你使用它来测试在按元素对两个 deque 进行*比较时，* 是否向*左*排序。

### <a name="example"></a>示例

```cpp
// cliext_deque_operator_lt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operatorlt-deque-stlclr"></a><a name="op_lteq"></a>operator&lt;= （deque）（STL/CLR）

Deque 小于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator<=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>parameters

*left*<br/>
要比较的左容器。

right<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `!(right < left)`。 使用此方法可以测试是否在按元素对两个 deque 进行比较时*向* *左*排序。

### <a name="example"></a>示例

```cpp
// cliext_deque_operator_le.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operator-deque-stlclr"></a><a name="op_as"></a>operator = （deque）（STL/CLR）

替换受控序列。

### <a name="syntax"></a>语法

```cpp
deque<Value>% operator=(deque<Value>% right);
```

#### <a name="parameters"></a>parameters

right<br/>
用于复制的容器。

### <a name="remarks"></a>备注

成员运算符*直接*复制到对象，然后返回 `*this`。 用于将受控序列替换为*右侧*受控序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_deque_operator_as.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operator-deque-stlclr"></a><a name="op_eq"></a>operator = = （deque）（STL/CLR）

Deque 相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator==(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>parameters

*left*<br/>
要比较的左容器。

right<br/>
要比较的右容器。

### <a name="remarks"></a>备注

仅当由*左*和*右*控制的序列具有相同的长度，并且每个位置 `i``left[i] ==` `right[i]`时，operator 函数才返回 true。 使用此方法可以*测试在按*元素对两个 deque 进行比较时，是否*向左*排序。

### <a name="example"></a>示例

```cpp
// cliext_deque_operator_eq.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operatorgt-deque-stlclr"></a><a name="op_gt"></a>operator&gt; （deque）（STL/CLR）

Deque 大于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator>(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>parameters

*left*<br/>
要比较的左容器。

right<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `right` `<` `left`。 使用此方法可以测试是否在按元素对两个 deque 进行*比较时向* *左*排序。

### <a name="example"></a>示例

```cpp
// cliext_deque_operator_gt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operatorgt-deque-stlclr"></a><a name="op_gteq"></a>operator&gt;= （deque）（STL/CLR）

Deque 大于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator>=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>parameters

*left*<br/>
要比较的左容器。

right<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `!(left` `<` `right)`。 用于测试在按元素对两个 deque 进行比较*时，是否向* *左*排序。

### <a name="example"></a>示例

```cpp
// cliext_deque_operator_ge.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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
