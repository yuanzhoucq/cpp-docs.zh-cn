---
title: list (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
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
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
ms.openlocfilehash: 1c05aff71b16c3edf1348466df325caacb027554
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225626"
---
# <a name="list-stlclr"></a>list (STL/CLR)

此模板类描述了一个对象，该对象控制具有双向访问权限的不同长度的元素序列。 可以使用容器将 `list` 一系列元素作为双向链接节点列表进行管理，每个节点存储一个元素。

在下面的说明中，与 `GValue` *值*相同，除非后者为 ref 类型，在这种情况下，它是 `Value^` 。

## <a name="syntax"></a>语法

```cpp
template<typename Value>
    ref class list
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        Microsoft::VisualC::StlClr::IList<GValue>
    { ..... };
```

### <a name="parameters"></a>参数

*值*<br/>
受控序列中的元素的类型。

## <a name="requirements"></a>要求

**标头：**\<cliext/list>

**命名空间：** cliext

## <a name="declarations"></a>声明

|类型定义|说明|
|---------------------|-----------------|
|[list::const_iterator (STL/CLR)](#const_iterator)|受控序列的常量迭代器的类型。|
|[list::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|
|[list::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|
|[list::generic_container (STL/CLR)](#generic_container)|容器的泛型接口的类型。|
|[list::generic_iterator (STL/CLR)](#generic_iterator)|容器的泛型接口的迭代器的类型。|
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型接口的反向迭代器的类型。|
|[list::generic_value (STL/CLR)](#generic_value)|容器的泛型接口的元素类型。|
|[list::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|
|[list::reference (STL/CLR)](#reference)|元素的引用的类型。|
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|受控序列的反向迭代器的类型。|
|[list::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|
|[list::value_type (STL/CLR)](#value_type)|元素的类型。|

|成员函数|说明|
|---------------------|-----------------|
|[list::assign (STL/CLR)](#assign)|替换所有元素。|
|[list::back (STL/CLR)](#back)|访问最后一个元素。|
|[list::begin (STL/CLR)](#begin)|指定受控序列的开头。|
|[list::clear (STL/CLR)](#clear)|删除所有元素。|
|[list::empty (STL/CLR)](#empty)|测试元素是否存在。|
|[list::end (STL/CLR)](#end)|指定受控序列的末尾。|
|[list::erase (STL/CLR)](#erase)|移除指定位置处的元素。|
|[list::front (STL/CLR)](#front)|访问第一个元素。|
|[list::insert (STL/CLR)](#insert)|在指定位置添加元素。|
|[list::list (STL/CLR)](#list)|构造容器对象。|
|[list::merge (STL/CLR)](#merge)|合并两个有序受控序列。|
|[list::pop_back (STL/CLR)](#pop_back)|删除最后一个元素。|
|[list::pop_front (STL/CLR)](#pop_front)|删除第一个元素。|
|[list::push_back (STL/CLR)](#push_back)|添加新的最后一个元素。|
|[list::push_front (STL/CLR)](#push_front)|添加新的第一个元素。|
|[list::rbegin (STL/CLR)](#rbegin)|指定反向受控序列的开头。|
|[list::remove (STL/CLR)](#remove)|删除具有指定值的元素。|
|[list::remove_if (STL/CLR)](#remove_if)|移除通过指定测试的元素。|
|[list::rend (STL/CLR)](#rend)|指定反向受控序列的末尾。|
|[list::resize (STL/CLR)](#resize)|更改元素的数量。|
|[list::reverse (STL/CLR)](#reverse)|反转受控序列。|
|[list::size (STL/CLR)](#size)|对元素数进行计数。|
|[list::sort (STL/CLR)](#sort)|对受控序列进行排序。|
|[list::splice (STL/CLR)](#splice)|重新联结节点间的链接。|
|[list::swap (STL/CLR)](#swap)|交换两个容器的内容。|
|[list::to_array (STL/CLR)](#to_array)|将受控序列复制到新数组。|
|[list::unique (STL/CLR)](#unique)|删除通过了指定测试的相邻元素。|

|属性|说明|
|--------------|-----------------|
|[list::back_item (STL/CLR)](#back_item)|访问最后一个元素。|
|[list::front_item (STL/CLR)](#front_item)|访问第一个元素。|

|操作员|说明|
|--------------|-----------------|
|[list::operator= (STL/CLR)](#op_as)|替换受控序列。|
|[operator！ = （list）（STL/CLR）](#op_neq)|确定对象是否 `list` 不等于另一个 `list` 对象。|
|[operator< （list）（STL/CLR）](#op_lt)|确定 `list` 对象是否小于另一个 `list` 对象。|
|[operator<= （list）（STL/CLR）](#op_lteq)|确定 `list` 对象是否小于或等于另一个 `list` 对象。|
|[operator = = （list）（STL/CLR）](#op_eq)|确定 `list` 对象是否等于另一个 `list` 对象。|
|[operator> （list）（STL/CLR）](#op_gt)|确定 `list` 对象是否大于另一个 `list` 对象。|
|[operator>= (list) (STL/CLR)](#op_gteq)|确定 `list` 对象是否大于或等于另一个 `list` 对象。|

## <a name="interfaces"></a>接口

|接口|说明|
|---------------|-----------------|
|<xref:System.ICloneable>|复制对象。|
|<xref:System.Collections.IEnumerable>|通过元素进行排序。|
|<xref:System.Collections.ICollection>|维护元素组。|
|<xref:System.Collections.Generic.IEnumerable%601>|通过类型化元素进行排序。|
|<xref:System.Collections.Generic.ICollection%601>|维护类型化元素组。|
|IList\<Value>|维护泛型容器。|

## <a name="remarks"></a>备注

对象为其控制的序列分配并释放存储，并将其控制为双向链接列表中的单个节点。 它通过更改节点之间的链接来重新排列元素，而不是将一个节点的内容复制到另一个节点。 这意味着，无需干扰剩余元素，即可随意插入和移除元素。 因此，列表非常适合用于模板类[队列（stl/clr）](../dotnet/queue-stl-clr.md)或模板类[堆栈（stl/clr）](../dotnet/stack-stl-clr.md)的基础容器。

`list`对象支持双向迭代器，这意味着，如果迭代器指定了受控序列中的元素，则可以单步执行相邻元素。 特殊头节点对应于[list：： end （STL/CLR）](../dotnet/list-end-stl-clr.md)返回的迭代器 `()` 。 可以递减此迭代器以到达受控序列中的最后一个元素（如果存在）。 您可以递增列表迭代器以到达头节点，然后将其与相等 `end()` 。 但不能取消引用返回的迭代器 `end()` 。

请注意，不能直接引用列表元素，因为它的数字位置需要随机访问迭代器。 因此，列表*不能*用作模板类[priority_queue （STL/CLR）](../dotnet/priority-queue-stl-clr.md)的基础容器。

列表迭代器将句柄存储到其关联的列表节点，后者又将句柄存储到其关联的容器。 只能将迭代器与其关联的容器对象一起使用。 只要列表迭代器的关联列表节点与某个列表相关联，它就会保持有效。 而且，有效的迭代器是 dereferencable 的，您可以使用它来访问或更改它指定的元素值，但前提是它不等于 `end()` 。

清除或删除元素会调用析构函数以获取其存储的值。 销毁容器将清除所有元素。 因此，其元素类型为 ref 类的容器可确保没有元素长于容器。 但请注意，句柄的容器*不*会销毁其元素。

## <a name="members"></a>成员

## <a name="listassign-stlclr"></a><a name="assign"></a>list：： assign （STL/CLR）

替换所有元素。

### <a name="syntax"></a>语法

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>参数

*计数*<br/>
要插入的元素数。

*first*<br/>
要插入的范围的开头。

*last*<br/>
要插入的范围的末尾。

*然后*<br/>
要插入的枚举。

*初始值*<br/>
要插入的元素的值。

### <a name="remarks"></a>备注

第一个成员函数会将受控序列替换为值*val*的*计数*元素的重复。 使用它可以将具有相同值的元素填充到容器中。

如果 `InIt` 是整数类型，则第二个成员函数的行为与相同 `assign((size_type)first, (value_type)last)` 。 否则，它会将受控序列替换为序列 [ `first` ， `last` ）。 用于使受控序列成为副本的另一个序列。

第三个成员函数将受控序列替换*为枚举器*指定的序列。 用于使受控序列成为枚举器所描述的序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_list_assign.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::list<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an iterator range
    cliext::list<wchar_t>::iterator it = c1.end();
    c2.assign(c1.begin(), --it);
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

## <a name="listback-stlclr"></a><a name="back"></a>list：： back （STL/CLR）

访问最后一个元素。

### <a name="syntax"></a>语法

```cpp
reference back();
```

### <a name="remarks"></a>备注

成员函数返回对受控序列的最后一个元素的引用，该元素必须为非空。 当您知道最后一个元素存在时，可以使用它来访问最后一个元素。

### <a name="example"></a>示例

```cpp
// cliext_list_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listback_item-stlclr"></a><a name="back_item"></a>list：： back_item （STL/CLR）

访问最后一个元素。

### <a name="syntax"></a>语法

```cpp
property value_type back_item;
```

### <a name="remarks"></a>备注

属性访问受控序列的最后一个元素，该元素必须为非空。 当您知道最后一个元素存在时，可以使用它读取或写入该元素。

### <a name="example"></a>示例

```cpp
// cliext_list_back_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listbegin-stlclr"></a><a name="begin"></a>list：： begin （STL/CLR）

指定受控序列的开头。

### <a name="syntax"></a>语法

```cpp
iterator begin();
```

### <a name="remarks"></a>备注

此成员函数返回一个随机访问迭代器，该迭代器指定受控序列的第一个元素，或刚超出空序列的末尾。 用于获取一个迭代器，该迭代器指定受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_list_begin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::iterator it = c1.begin();
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

## <a name="listclear-stlclr"></a><a name="clear"></a>list：： clear （STL/CLR）

删除所有元素。

### <a name="syntax"></a>语法

```cpp
void clear();
```

### <a name="remarks"></a>备注

成员函数有效地调用[list：： erase （stl/clr）](../dotnet/list-erase-stl-clr.md) `(` [list：： begin （stl/clr）](../dotnet/list-begin-stl-clr.md) `(),` [list：： end （stl/clr）](../dotnet/list-end-stl-clr.md) `())` 。 用于确保受控序列为空。

### <a name="example"></a>示例

```cpp
// cliext_list_clear.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listconst_iterator-stlclr"></a><a name="const_iterator"></a>list：： const_iterator （STL/CLR）

受控序列的常量迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>备注

该类型描述 `T2` 可用作受控序列的常量随机访问迭代器的未指定类型的对象。

### <a name="example"></a>示例

```cpp
// cliext_list_const_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listconst_reference-stlclr"></a><a name="const_reference"></a>list：： const_reference （STL/CLR）

元素的常量引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>备注

类型描述对元素的常量引用。

### <a name="example"></a>示例

```cpp
// cliext_list_const_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::list<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>list：： const_reverse_iterator （STL/CLR）

受控序列的常量反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述 `T4` 可用作受控序列的常量反向迭代器的未指定类型的对象。

### <a name="example"></a>示例

```cpp
// cliext_list_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="listdifference_type-stlclr"></a><a name="difference_type"></a>list：:d ifference_type （STL/CLR）

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>备注

类型描述有符号的元素计数。

### <a name="example"></a>示例

```cpp
// cliext_list_difference_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::difference_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.end();
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

## <a name="listempty-stlclr"></a><a name="empty"></a>list：： empty （STL/CLR）

测试元素是否存在。

### <a name="syntax"></a>语法

```cpp
bool empty();
```

### <a name="remarks"></a>备注

对于空受控序列，该成员函数返回 true。 它等效于[list：： size （STL/CLR）](../dotnet/list-size-stl-clr.md) `() == 0` 。 用于测试列表是否为空。

### <a name="example"></a>示例

```cpp
// cliext_list_empty.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listend-stlclr"></a><a name="end"></a>list：： end （STL/CLR）

指定受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
iterator end();
```

### <a name="remarks"></a>备注

成员函数返回一个随机访问迭代器，它指向刚超出受控序列末尾的位置。 用于获取一个迭代器，该迭代器指定受控序列的末尾;如果受控序列的长度发生更改，则其状态不会更改。

### <a name="example"></a>示例

```cpp
// cliext_list_end.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::list<wchar_t>::iterator it = c1.end();
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

## <a name="listerase-stlclr"></a><a name="erase"></a>list：： erase （STL/CLR）

移除指定位置处的元素。

### <a name="syntax"></a>语法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>参数

*first*<br/>
要清除的范围的开头。

*last*<br/>
要清除的范围的结束。

*where*<br/>
要清除的元素。

### <a name="remarks"></a>备注

第一个成员函数删除由*where*指向的受控序列的元素。 使用它可以删除单个元素。

第二个成员函数将移除范围 [`first`、`last`) 中的受控序列的元素。 使用它可以删除零个或多个连续元素。

这两个成员函数都返回一个迭代器，该迭代器指定在删除的任何元素之外保留的第一个元素; 如果此类元素不存在，则为[list：： end （STL/CLR）](../dotnet/list-end-stl-clr.md) `()` 。

擦除元素时，元素副本的数目在擦除结束和序列的最近结束之间的元素数中是线性的。 （在序列的任一端删除一个或多个元素时，不会发生元素复制。）

### <a name="example"></a>示例

```cpp
// cliext_list_erase.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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
    cliext::list<wchar_t>::iterator it = c1.end();
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

## <a name="listfront-stlclr"></a><a name="front"></a>list：： front （STL/CLR）

访问第一个元素。

### <a name="syntax"></a>语法

```cpp
reference front();
```

### <a name="remarks"></a>备注

成员函数返回对受控序列中第一个元素的引用，该元素必须为非空。 你可以使用它来读取或写入第一个元素（如果你知道存在该元素）。

### <a name="example"></a>示例

```cpp
// cliext_list_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listfront_item-stlclr"></a><a name="front_item"></a>list：： front_item （STL/CLR）

访问第一个元素。

### <a name="syntax"></a>语法

```cpp
property value_type front_item;
```

### <a name="remarks"></a>备注

属性访问受控序列中的第一个元素，该元素必须为非空。 你可以使用它来读取或写入第一个元素（如果你知道存在该元素）。

### <a name="example"></a>示例

```cpp
// cliext_list_front_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listgeneric_container-stlclr"></a><a name="generic_container"></a>list：： generic_container （STL/CLR）

容器的泛型接口的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::
    IList<generic_value>
    generic_container;
```

### <a name="remarks"></a>备注

类型描述此模板容器类的泛型接口。

### <a name="example"></a>示例

```cpp
// cliext_list_generic_container.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="listgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>list：： generic_iterator （STL/CLR）

与容器的泛型接口一起使用的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可与此模板容器类的泛型接口一起使用的泛型迭代器。

### <a name="example"></a>示例

```cpp
// cliext_list_generic_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
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

## <a name="listgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>list：： generic_reverse_iterator （STL/CLR）

用于容器的泛型接口的反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可与此模板容器类的泛型接口一起使用的一般反向迭代器。

### <a name="example"></a>示例

```cpp
// cliext_list_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
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

## <a name="listgeneric_value-stlclr"></a><a name="generic_value"></a>list：： generic_value （STL/CLR）

用于容器的泛型接口的元素类型。

### <a name="syntax"></a>语法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>备注

类型描述了一个类型为的对象 `GValue` ，该对象描述用于此模板容器类的泛型接口的存储元素值。

### <a name="example"></a>示例

```cpp
// cliext_list_generic_value.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
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

## <a name="listinsert-stlclr"></a><a name="insert"></a>list：： insert （STL/CLR）

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

*计数*<br/>
要插入的元素数。

*first*<br/>
要插入的范围的开头。

*last*<br/>
要插入的范围的末尾。

*然后*<br/>
要插入的枚举。

*初始值*<br/>
要插入的元素的值。

*where*<br/>
要插入到的容器中的位置。

### <a name="remarks"></a>备注

每个成员函数在由控制的序列中的*位置*指向的元素之前，插入由剩余操作数指定的序列。

第一个成员函数插入具有值*val*的元素，并返回指定新插入的元素的迭代器。 用于在迭代器指定的位置之前插入单个元素。

第二个成员函数插入值*val*的*计数*元素的重复。 使用它可以插入零个或多个连续元素，这些元素是同一值的所有副本。

如果 `InIt` 是整数类型，则第三个成员函数的行为与 `insert(where, (size_type)first, (value_type)last)` 相同。 否则，将插入序列 [ `first` ， `last` ）。 使用它可以插入从另一个序列复制的零个或多个连续元素。

第四个成员函数插入由*权限*指定的序列。 使用它可以插入枚举器描述的序列。

在插入单个元素时，元素副本的数目在插入点与序列的最近结束之间的元素数中是线性的。 （在序列的任一端插入一个或多个元素时，不会发生元素复制。）如果 `InIt` 是输入迭代器，则第三个成员函数将为序列中的每个元素有效地执行单个插入。 否则，在插入 `N` 元素时，元素副本的数量为线性， `N` 并加上插入点与序列的最近结束之间的元素数。

### <a name="example"></a>示例

```cpp
// cliext_list_insert.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::list<wchar_t> c2;
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

    // insert a single value using index
    it = c2.begin();
    ++it, ++it, ++it;
    c2.insert(it, L'z');
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

## <a name="listiterator-stlclr"></a><a name="iterator"></a>list：： iterator （STL/CLR）

受控序列的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>备注

该类型描述 `T1` 可用作受控序列的随机访问迭代器的未指定类型的对象。

### <a name="example"></a>示例

```cpp
// cliext_list_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
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

## <a name="listlist-stlclr"></a><a name="list"></a>list：： list （STL/CLR）

构造容器对象。

### <a name="syntax"></a>语法

```cpp
list();
list(list<Value>% right);
list(list<Value>^ right);
explicit list(size_type count);
list(size_type count, value_type val);
template<typename InIt>
    list(InIt first, InIt last);
list(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>参数

*计数*<br/>
要插入的元素数。

*first*<br/>
要插入的范围的开头。

*last*<br/>
要插入的范围的末尾。

*然后*<br/>
要插入的对象或范围。

*初始值*<br/>
要插入的元素的值。

### <a name="remarks"></a>备注

构造函数：

`list();`

初始化没有元素的受控序列。 用于指定空的初始受控序列。

构造函数：

`list(list<Value>% right);`

用序列 [，）初始化受控序列 `right.begin()` `right.end()` 。 用于指定初始受控序列，该序列是由 list 对象*权限*控制的序列的副本。

构造函数：

`list(list<Value>^ right);`

用序列 [，）初始化受控序列 `right->begin()` `right->end()` 。 用于指定初始受控序列，该序列是由其句柄为*right*的列表对象控制的序列副本。

构造函数：

`explicit list(size_type count);`

用*count*元素每个值初始化受控序列 `value_type()` 。 使用它可以使用具有默认值的元素填充容器。

构造函数：

`list(size_type count, value_type val);`

用每*个值为值的**计数*元素初始化受控序列。 使用它可以将具有相同值的元素填充到容器中。

构造函数：

`template<typename InIt>`

`list(InIt first, InIt last);`

用序列 [，）初始化受控序列 `first` `last` 。 用于使受控序列成为另一个序列的副本。

构造函数：

`list(System::Collections::Generic::IEnumerable<Value>^ right);`

使用枚举器*权限*指定的序列初始化受控序列。 用于使受控序列成为枚举器所描述的另一序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_list_construct.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::list<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::list<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::list<wchar_t>::iterator it = c3.end();
    cliext::list<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::list<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::list<wchar_t> c8(%c3);
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

## <a name="listmerge-stlclr"></a><a name="merge"></a>list：： merge （STL/CLR）

合并两个有序受控序列。

### <a name="syntax"></a>语法

```cpp
void merge(list<Value>% right);
template<typename Pred2>
    void merge(list<Value>% right, Pred2 pred);
```

#### <a name="parameters"></a>参数

*pred*<br/>
元素对的比较器。

*然后*<br/>
要合并的容器。

### <a name="remarks"></a>备注

第一个成员函数从*右*控制的序列中移除所有元素，并将其插入到受控序列中。 这两个序列必须以前按顺序排序 `operator<` --元素在您通过任一顺序进行的进度中都不能减少。 结果序列也按排序 `operator<` 。 您可以使用此成员函数将值增加的两个序列合并为一个也增加值的序列。

第二个成员函数的行为与第一个相同，不同之处在于 `pred`  --  `pred(X, Y)` 对于 `X` 序列中跟随元素的任何元素，序列按排序方式必须为 false `Y` 。 用于合并由指定的谓词函数或委托排序的两个序列。

这两个函数执行稳定合并-在生成的受控序列中，任何一个原始受控序列中的元素都不会反转。 此外，如果生成的受控序列中的一对元素 `X` 和 `Y` 具有等效的排序---- `!(X < Y) && !(X < Y)` 来自原始受控序列的元素出现在由*right*控制的序列中的元素之前。

### <a name="example"></a>示例

```cpp
// cliext_list_merge.cpp
// compile with: /clr
#include <cliext/list>

typedef cliext::list<wchar_t> Mylist;
int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'c');
    c1.push_back(L'e');

    // display initial contents " a c e"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    cliext::list<wchar_t> c2;
    c2.push_back(L'b');
    c2.push_back(L'd');
    c2.push_back(L'f');

    // display initial contents " b d f"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // merge and display
    cliext::list<wchar_t> c3(c1);
    c3.merge(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());

    // sort descending, merge descending, and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.merge(c1, cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    return (0);
    }
```

```Output
a c e
b d f
a b c d e f
c2.size() = 0
e c a
f e d c b a
f e e d c c b a a
c1.size() = 0
```

## <a name="listoperator-stlclr"></a><a name="op_as"></a>list：： operator = （STL/CLR）

替换受控序列。

### <a name="syntax"></a>语法

```
list<Value>% operator=(list<Value>% right);
```

#### <a name="parameters"></a>参数

*然后*<br/>
用于复制的容器。

### <a name="remarks"></a>备注

成员运算符*直接*复制到对象，然后返回 **`*this`** 。 用于将受控序列替换为*右侧*受控序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_list_operator_as.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="listpop_back-stlclr"></a><a name="pop_back"></a>list：:p op_back （STL/CLR）

删除最后一个元素。

### <a name="syntax"></a>语法

```cpp
void pop_back();
```

### <a name="remarks"></a>备注

成员函数删除受控序列中的最后一个元素，该元素必须为非空。 使用它可以将列表中的一个元素向后缩短一个元素。

### <a name="example"></a>示例

```cpp
// cliext_list_pop_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listpop_front-stlclr"></a><a name="pop_front"></a>list：:p op_front （STL/CLR）

删除第一个元素。

### <a name="syntax"></a>语法

```cpp
void pop_front();
```

### <a name="remarks"></a>备注

成员函数删除受控序列中的第一个元素，该元素必须为非空。 使用它可以将列表中的一个元素按前一个元素缩短。

### <a name="example"></a>示例

```cpp
// cliext_list_pop_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listpush_back-stlclr"></a><a name="push_back"></a>list：:p ush_back （STL/CLR）

添加新的最后一个元素。

### <a name="syntax"></a>语法

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>备注

此成员函数在 `val` 受控序列的末尾插入一个具有值的元素。 使用它可以向列表中追加另一个元素。

### <a name="example"></a>示例

```cpp
// cliext_list_push_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listpush_front-stlclr"></a><a name="push_front"></a>list：:p ush_front （STL/CLR）

添加新的第一个元素。

### <a name="syntax"></a>语法

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>备注

此成员函数在受控序列的开头插入一个具有值的元素 `val` 。 您可以使用它将另一个元素预置到列表。

### <a name="example"></a>示例

```cpp
// cliext_list_push_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listrbegin-stlclr"></a><a name="rbegin"></a>list：： rbegin （STL/CLR）

指定反向受控序列的开头。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器，该迭代器指定受控序列的最后一个元素，或刚超出空序列的开头。 因此，它指定反向序列的 `beginning`。 用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_list_rbegin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="listreference-stlclr"></a><a name="reference"></a>list：： reference （STL/CLR）

元素的引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>备注

类型描述对元素的引用。

### <a name="example"></a>示例

```cpp
// cliext_list_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;

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

## <a name="listremove-stlclr"></a><a name="remove"></a>list：： remove （STL/CLR）

删除具有指定值的元素。

### <a name="syntax"></a>语法

```cpp
void remove(value_type val);
```

#### <a name="parameters"></a>参数

*初始值*<br/>
要移除的元素的值。

### <a name="remarks"></a>备注

成员函数删除受控序列中的元素 `((System::Object^)val)->Equals((System::Object^)x)` （如果有）。 使用此方法可以清除具有指定值的任意元素。

### <a name="example"></a>示例

```cpp
// cliext_list_remove.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove(L'A');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove(L'b');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c
```

## <a name="listremove_if-stlclr"></a><a name="remove_if"></a>list：： remove_if （STL/CLR）

移除通过指定测试的元素。

### <a name="syntax"></a>语法

```cpp
template<typename Pred1>
    void remove_if(Pred1 pred);
```

#### <a name="parameters"></a>参数

*pred*<br/>
测试要删除的元素。

### <a name="remarks"></a>备注

成员函数从受控序列（清除）中删除为 true 的每个元素 `X` `pred(X)` 。 使用它可以删除满足您指定为函数或委托的条件的所有元素。

### <a name="example"></a>示例

```cpp
// cliext_list_remove_if.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b b b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(
        cliext::equal_to<wchar_t>(), L'd'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(
        cliext::not_equal_to<wchar_t>(), L'b'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b b b c
a b b b c
b b b
```

## <a name="listrend-stlclr"></a><a name="rend"></a>list：： rend （STL/CLR）

指定反向受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器，该迭代器指向刚刚超出受控序列的开头。 因此，它指定反向序列的 `end`。 用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 末尾，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_list_rend.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="listresize-stlclr"></a><a name="resize"></a>list：： resize （STL/CLR）

更改元素的数量。

### <a name="syntax"></a>语法

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>参数

*new_size*<br/>
受控序列的新大小。

*初始值*<br/>
填充元素的值。

### <a name="remarks"></a>备注

成员函数确保[list：： size （STL/CLR）](../dotnet/list-size-stl-clr.md) `()` 之后返回*new_size*。 如果它必须使受控序列更长，则第一个成员函数将追加值为的元素 `value_type()` ，而第二个成员函数则追加值为*val*的元素。 为了使受控序列更短，两个成员函数实际上会清除最后一个元素[列表：： size （STL/CLR）](../dotnet/list-size-stl-clr.md) `() -` `new_size` 次。 使用它可以通过修整或填充当前受控序列来确保受控序列*new_size*大小。

### <a name="example"></a>示例

```cpp
// cliext_list_resize.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container and pad with default values
    cliext::list<wchar_t> c1;
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

## <a name="listreverse-stlclr"></a><a name="reverse"></a>list：： reverse （STL/CLR）

反转受控序列。

### <a name="syntax"></a>语法

```cpp
void reverse();
```

### <a name="remarks"></a>备注

成员函数将反转受控序列中所有元素的顺序。 可以使用它来反映元素列表。

### <a name="example"></a>示例

```cpp
// cliext_list_reverse.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // reverse and redisplay
    c1.reverse();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
```

## <a name="listreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>list：： reverse_iterator （STL/CLR）

受控序列的反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_list_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="listsize-stlclr"></a><a name="size"></a>list：： size （STL/CLR）

对元素数进行计数。

### <a name="syntax"></a>语法

```cpp
size_type size();
```

### <a name="remarks"></a>备注

成员函数将返回受控序列的长度。 用于确定受控序列中当前的元素数。 如果你只关心序列的大小是否为非零，请参阅[list：： empty （STL/CLR）](../dotnet/list-empty-stl-clr.md) `()` 。

### <a name="example"></a>示例

```cpp
// cliext_list_size.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listsize_type-stlclr"></a><a name="size_type"></a>list：： size_type （STL/CLR）

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>备注

该类型描述了一个非负元素计数。

### <a name="example"></a>示例

```cpp
// cliext_list_size_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::size_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="listsort-stlclr"></a><a name="sort"></a>list：： sort （STL/CLR）

对受控序列进行排序。

### <a name="syntax"></a>语法

```cpp
void sort();
template<typename Pred2>
    void sort(Pred2 pred);
```

#### <a name="parameters"></a>参数

*pred*<br/>
元素对的比较器。

### <a name="remarks"></a>备注

第一个成员函数重新排列受控序列中的元素，以便在按顺序进行排序时，它们按 `operator<` --元素排序不会减少。 您可以使用此成员函数按递增顺序对序列进行排序。

第二个成员函数的行为与第一个相同，不同之处在于 `pred`  --  `pred(X, Y)` 对于 `X` 结果序列中后面跟有元素的任何元素，序列按排序方式为 false `Y` 。 它用于按谓词函数或委托指定的顺序对序列进行排序。

这两个函数执行稳定排序--在生成的受控序列中，不会反转原始受控序列中的元素对。

### <a name="example"></a>示例

```cpp
// cliext_list_sort.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort descending and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort ascending and redisplay
    c1.sort();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
a b c
```

## <a name="listsplice-stlclr"></a><a name="splice"></a>list：：接合（STL/CLR）

Restitch 节点之间的链接。

### <a name="syntax"></a>语法

```cpp
void splice(iterator where, list<Value>% right);
void splice(iterator where, list<Value>% right,
    iterator first);
void splice(iterator where, list<Value>% right,
    iterator first, iterator last);
```

#### <a name="parameters"></a>参数

*first*<br/>
要拼接的范围的开头。

*last*<br/>
要拼接的范围的结束。

*然后*<br/>
要从中拼接的容器。

*where*<br/>
要在其中接合的容器中的位置。

### <a name="remarks"></a>备注

第一个成员函数将由*右*控制的序列插入到所指向的受控序列中的元素*之前。* 它还会删除*右侧*的所有元素。 （ `%right` 不得等于 **`this`** 。）使用它可以将所有列表拼接到另一个列表。

第二个成员函数删除由*right*控制的序列中的*第一个*元素，并将其插入到所指向的受控序列中的元素*之前。* （如果 `where` `==``first` `||` `where``== ++first`，则不会发生更改。）它用于将一个列表中的单个元素接合到另一个列表。

第三个成员函数将由 [，）指定的子范围 `first` `last` 从*右端*所控制的序列中的元素之前的*位置*插入到所指向的位置。 它还将从*权限*控制的序列中删除原始子范围。 （如果 `right == this` 范围 [ `first` ， `last` ）不能包含由*where*指向的元素。）使用它可以将零个或多个元素的子序列从一个列表接合到另一个列表。

### <a name="example"></a>示例

```cpp
// cliext_list_splice.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // splice to a new list
    cliext::list<wchar_t> c2;
    c2.splice(c2.begin(), c1);
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return one element
    c1.splice(c1.end(), c2, c2.begin());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return remaining elements
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());
    return (0);
    }
```

```Output
a b c
c1.size() = 0
a b c
a
b c
b c a
c2.size() = 0
```

## <a name="listswap-stlclr"></a><a name="swap"></a>list：： swap （STL/CLR）

交换两个容器的内容。

### <a name="syntax"></a>语法

```cpp
void swap(list<Value>% right);
```

#### <a name="parameters"></a>参数

*然后*<br/>
要与其交换内容的容器。

### <a name="remarks"></a>备注

成员函数交换和右之间的受控 **`*this`** 序列*right*。 它在固定时间内执行此操作，并且不会引发异常。 使用该方法可以快速交换两个容器的内容。

### <a name="example"></a>示例

```cpp
// cliext_list_swap.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::list<wchar_t> c2(5, L'x');
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

## <a name="listto_array-stlclr"></a><a name="to_array"></a>list：： to_array （STL/CLR）

将受控序列复制到新数组。

### <a name="syntax"></a>语法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>备注

此成员函数返回包含受控序列的数组。 可以使用它以数组形式获取受控序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_list_to_array.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="listunique-stlclr"></a><a name="unique"></a>list：： unique （STL/CLR）

删除通过了指定测试的相邻元素。

### <a name="syntax"></a>语法

```cpp
void unique();
template<typename Pred2>
    void unique(Pred2 pred);
```

#### <a name="parameters"></a>参数

*pred*<br/>
元素对的比较器。

### <a name="remarks"></a>备注

第一个成员函数从受控序列（清除）中删除每个与前一个元素相等的元素，如果元素在 `X` 元素之前，则 `Y` `X == Y` 成员函数将删除 `Y` 。 使用它可以删除比较相等的相邻元素的每个子序列的所有副本。 请注意，如果对受控序列进行排序（例如通过调用[list：： sort （STL/CLR））](../dotnet/list-sort-stl-clr.md) `()` ，则成员函数仅保留具有唯一值的元素。 （由此而得名）。

第二个成员函数的行为与第一个相同，不同之处在于，它会删除元素后面的每个元素 `Y` `X` `pred(X, Y)` 。 使用它可以删除满足指定谓词函数或委托的相邻元素的所有子序列的所有副本。 请注意，如果按顺序对受控序列进行排序（例如通过调用 `sort(pred)` ），则成员函数将只保留对任何其他元素不具有等效排序的元素。

### <a name="example"></a>示例

```cpp
// cliext_list_unique.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique
    cliext::list<wchar_t> c2(c1);
    c2.unique();
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique(not_equal_to)
    c2 = c1;
    c2.unique(cliext::not_equal_to<wchar_t>());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a a b c
a b c
a a
```

## <a name="listvalue_type-stlclr"></a><a name="value_type"></a>list：： value_type （STL/CLR）

元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>备注

该类型是模板参数*值*的同义词。

### <a name="example"></a>示例

```cpp
// cliext_list_value_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::list<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-list-stlclr"></a><a name="op_neq"></a>operator！ = （list）（STL/CLR）

列表不相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator!=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `!(left == right)` 。 使用此方法可以测试在按元素比较两个*列表时，是否按原样对**左侧*进行排序。

### <a name="example"></a>示例

```cpp
// cliext_list_operator_ne.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="operatorlt-list-stlclr"></a><a name="op_lt"></a>operator &lt; （list）（STL/CLR）

列表小于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator<(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

如果为，则运算符函数返回 true，适用于的最低位置 `i` `!(right[i] < left[i])` `left[i] < right[i]` 。 否则，它会返回， `left->size() < right->size()` 以便在按元素比较两个列表*right*时，使用它来测试是否对*左侧*排序。

### <a name="example"></a>示例

```cpp
// cliext_list_operator_lt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="operatorlt-list-stlclr"></a><a name="op_lteq"></a>operator &lt; = （list）（STL/CLR）

列表小于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator<=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `!(right < left)` 。 用于测试在按元素对两个列表进行比较*时，是否向**左*排序。

### <a name="example"></a>示例

```cpp
// cliext_list_operator_le.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="operator-list-stlclr"></a><a name="op_eq"></a>operator = = （list）（STL/CLR）

列出相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator==(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

仅当由*左*和*右*控制的序列具有相同的长度，并且对于每个位置，operator 函数才返回 true `i` `left[i] ==` `right[i]` 。 使用此方法可以测试在按元素比较两个列表*时，* 是否向*左*排序。

### <a name="example"></a>示例

```cpp
// cliext_list_operator_eq.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="operatorgt-list-stlclr"></a><a name="op_gt"></a>operator &gt; （list）（STL/CLR）

列表大于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator>(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `right` `<` `left` 。 用于测试在按元素比较两个*列表时，是否向**左*排序。

### <a name="example"></a>示例

```cpp
// cliext_list_operator_gt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="operatorgt-list-stlclr"></a><a name="op_gteq"></a>operator &gt; = （list）（STL/CLR）

列出大于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Value>
    bool operator>=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `!(left` `<` `right)` 。 用于测试在按元素比较两个*列表时，是否向**左*排序。

### <a name="example"></a>示例

```cpp
// cliext_list_operator_ge.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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
