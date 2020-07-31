---
title: map (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::map
- cliext::map::begin
- cliext::map::clear
- cliext::map::const_iterator
- cliext::map::const_reference
- cliext::map::const_reverse_iterator
- cliext::map::count
- cliext::map::difference_type
- cliext::map::empty
- cliext::map::end
- cliext::map::equal_range
- cliext::map::erase
- cliext::map::find
- cliext::map::generic_container
- cliext::map::generic_iterator
- cliext::map::generic_reverse_iterator
- cliext::map::generic_value
- cliext::map::insert
- cliext::map::iterator
- cliext::map::key_comp
- cliext::map::key_compare
- cliext::map::key_type
- cliext::map::lower_bound
- cliext::map::make_value
- cliext::map::map
- cliext::map::mapped_type
- cliext::map::operator=
- cliext::map::operator
- cliext::map::rbegin
- cliext::map::reference
- cliext::map::rend
- cliext::map::reverse_iterator
- cliext::map::size
- cliext::map::size_type
- cliext::map::swap
- cliext::map::to_array
- cliext::map::upper_bound
- cliext::map::value_comp
- cliext::map::value_compare
- cliext::map::value_type
- cliext::operator!= (map)
- cliext::operator< (map)
- cliext::operator<= (map)
- cliext::operator== (map)
- cliext::operator> (map)
- cliext::operator>= (map)
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
- operator!= (map) member [STL/CLR]
- operator< (map) member [STL/CLR]
- operator<= (map) member [STL/CLR]
- operator== (map) member [STL/CLR]
- operator> (map) member [STL/CLR]
- operator>= (map) member [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
ms.openlocfilehash: cd06942d3795dda9e6c6aaa8794957018fa96ace
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216370"
---
# <a name="map-stlclr"></a>map (STL/CLR)

此模板类描述了一个对象，该对象控制具有双向访问权限的不同长度的元素序列。 使用容器可以将 `map` 一系列元素作为（几乎）均衡的节点的排序树来管理，每个节点存储一个元素。 元素包含一个键，用于对序列进行排序，并包含一个映射值，此值将随之进行。

在下面的说明中，与 `GValue` 相同：

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

其中：

`GKey`与*Key*相同，除非后者为 ref 类型，在这种情况下，它是`Key^`

`GMapped`与*映射*相同，除非后者为 ref 类型，在这种情况下，它是`Mapped^`

## <a name="syntax"></a>语法

```cpp
template<typename Key,
    typename Mapped>
    ref class map
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        System::Collections::Generic::IDictionary<Gkey, GMapped>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>参数

*Key*<br/>
受控序列中元素的键组件的类型。

*Mapped*<br/>
受控序列中元素的附加组件的类型。

## <a name="requirements"></a>要求

**标头：**\<cliext/map>

**命名空间：** cliext

## <a name="declarations"></a>声明

|类型定义|描述|
|---------------------|-----------------|
|[map::const_iterator (STL/CLR)](#const_iterator)|受控序列的常量迭代器的类型。|
|[map::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|
|[map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|
|[map::difference_type (STL/CLR)](#difference_type)|两个元素之间的（可能有符号）距离的类型。|
|[map::generic_container (STL/CLR)](#generic_container)|容器的泛型接口的类型。|
|[map::generic_iterator (STL/CLR)](#generic_iterator)|容器的泛型接口的迭代器的类型。|
|[map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型接口的反向迭代器的类型。|
|[map::generic_value (STL/CLR)](#generic_value)|容器的泛型接口的元素类型。|
|[map::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|
|[map::key_compare (STL/CLR)](#key_compare)|两个键的排序委托。|
|[map::key_type (STL/CLR)](#key_type)|排序键的类型。|
|[map::mapped_type (STL/CLR)](#mapped_type)|与每个键关联的映射值的类型。|
|[map::reference (STL/CLR)](#reference)|元素的引用的类型。|
|[map::reverse_iterator (STL/CLR)](#reverse_iterator)|受控序列的反向迭代器的类型。|
|[map::size_type (STL/CLR)](#size_type)|两个元素之间的（非负）距离的类型。|
|[map::value_compare (STL/CLR)](#value_compare)|两个元素值的排序委托。|
|[map::value_type (STL/CLR)](#value_type)|元素的类型。|

|成员函数|描述|
|---------------------|-----------------|
|[map::begin (STL/CLR)](#begin)|指定受控序列的开头。|
|[map::clear (STL/CLR)](#clear)|删除所有元素。|
|[map::count (STL/CLR)](#count)|对与指定的键匹配的元素进行计数。|
|[map::empty (STL/CLR)](#empty)|测试元素是否存在。|
|[map::end (STL/CLR)](#end)|指定受控序列的末尾。|
|[map::equal_range (STL/CLR)](#equal_range)|查找与指定键匹配的范围。|
|[map::erase (STL/CLR)](#erase)|移除指定位置处的元素。|
|[map::find (STL/CLR)](#find)|查找与指定键匹配的元素。|
|[map::insert (STL/CLR)](#insert)|添加元素。|
|[map::key_comp (STL/CLR)](#key_comp)|复制两个键的排序委托。|
|[map::lower_bound (STL/CLR)](#lower_bound)|查找与指定键匹配的范围的开头。|
|[map::make_value (STL/CLR)](#make_value)|构造一个值对象。|
|[map::map (STL/CLR)](#map)|构造容器对象。|
|[map::rbegin (STL/CLR)](#rbegin)|指定反向受控序列的开头。|
|[map::rend (STL/CLR)](#rend)|指定反向受控序列的末尾。|
|[map::size (STL/CLR)](#size)|对元素数进行计数。|
|[map::swap (STL/CLR)](#swap)|交换两个容器的内容。|
|[map::to_array (STL/CLR)](#to_array)|将受控序列复制到新数组。|
|[map::upper_bound (STL/CLR)](#upper_bound)|查找与指定键匹配的范围的末尾。|
|[map::value_comp (STL/CLR)](#value_comp)|复制两个元素值的排序委托。|

|操作员|描述|
|--------------|-----------------|
|[map::operator= (STL/CLR)](#op_as)|替换受控序列。|
|[map::operator(STL/CLR)](#op)|将键映射到其关联的映射值。|
|[operator！ = （map）（STL/CLR）](#op_neq)|确定对象是否 `map` 不等于另一个 `map` 对象。|
|[运算符< （map）（STL/CLR）](#op_lt)|确定 `map` 对象是否小于另一个 `map` 对象。|
|[operator<= (map) (STL/CLR)](#op_lteq)|确定 `map` 对象是否小于或等于另一个 `map` 对象。|
|[operator = = （map）（STL/CLR）](#op_eq)|确定 `map` 对象是否等于另一个 `map` 对象。|
|[运算符> （map）（STL/CLR）](#op_gt)|确定 `map` 对象是否大于另一个 `map` 对象。|
|[运算符>= （map）（STL/CLR）](#op_gteq)|确定 `map` 对象是否大于或等于另一个 `map` 对象。|

## <a name="interfaces"></a>接口

|接口|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|复制对象。|
|<xref:System.Collections.IEnumerable>|通过元素进行排序。|
|<xref:System.Collections.ICollection>|维护元素组。|
|<xref:System.Collections.Generic.IEnumerable%601>|通过类型化元素进行排序。|
|<xref:System.Collections.Generic.ICollection%601>|维护类型化元素组。|
|<xref:System.Collections.Generic.IDictionary%602>|维护 {key，value} 对组。|
|ITree<项，值>|维护泛型容器。|

## <a name="remarks"></a>备注

对象为其控制的序列分配并释放存储，以作为单个节点。 它通过更改节点之间的链接，将元素插入到（几乎）平衡树中，而不是将一个节点的内容复制到另一个节点。 这意味着，无需干扰剩余元素，即可随意插入和移除元素。

对象通过调用类型为[map：： key_compare （STL/CLR）](../dotnet/map-key-compare-stl-clr.md)的存储委托对象，对它控制的序列进行排序。 构造映射时，可以指定存储的委托对象;如果指定 "无委托对象"，则默认值为 "比较" `operator<(key_type, key_type)` 。 可以通过调用成员函数[map：： key_comp （STL/CLR）](../dotnet/map-key-comp-stl-clr.md)访问此存储的对象 `()` 。

此类委托对象必须对[映射：： key_type （STL/CLR）](../dotnet/map-key-type-stl-clr.md)类型的键施加严格弱排序。 这意味着，对于任意两个密钥 `X` 和 `Y` ：

`key_comp()(X, Y)`针对每个调用返回相同的布尔值结果。

如果 `key_comp()(X, Y)` 为 true，则 `key_comp()(Y, X)` 必须为 false。

如果 `key_comp()(X, Y)` 为 true，则 `X` 称之前为排序 `Y` 。

如果 `!key_comp()(X, Y) && !key_comp()(Y, X)` 为 true，则 `X` `Y` 认为和具有等效的排序。

对于位于 `X` `Y` 受控序列中的任何元素， `key_comp()(Y, X)` 为 false。 （对于默认的委托对象，键从不减小值。）与模板类[映射](../dotnet/map-stl-clr.md)不同，模板类的对象 `map` 不需要所有元素的键都是唯一的。 （两个或两个以上的键可以具有等效的顺序。）

每个元素都包含一个单独的键和一个映射值。 序列以允许查找、插入和移除任意元素的方式表示，这些操作与序列中的元素数的对数成正比（对数时间）。 此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。

映射支持双向迭代器，这意味着，如果迭代器指定了受控序列中的元素，则可以单步执行相邻元素。 特殊头节点对应于[map：： end （STL/CLR）](../dotnet/map-end-stl-clr.md)返回的迭代器 `()` 。 可以递减此迭代器以到达受控序列中的最后一个元素（如果存在）。 您可以递增地图迭代器以到达头节点，然后将其与相等 `end()` 。 但不能取消引用返回的迭代器 `end()` 。

请注意，不能直接引用映射元素，因为它的数字位置需要随机访问迭代器。

地图迭代器将句柄存储到其关联的映射节点，后者又将句柄存储到其关联的容器。 只能将迭代器与其关联的容器对象一起使用。 只要映射迭代器的关联映射节点与某个映射相关联，它就会保持有效。 而且，有效的迭代器是 dereferencable 的，您可以使用它来访问或更改它指定的元素值，但前提是它不等于 `end()` 。

清除或删除元素会调用析构函数以获取其存储的值。 销毁容器将清除所有元素。 因此，其元素类型为 ref 类的容器可确保没有元素长于容器。 但请注意，句柄的容器*不*会销毁其元素。

## <a name="members"></a>成员

## <a name="mapbegin-stlclr"></a><a name="begin"></a>map：： begin （STL/CLR）

指定受控序列的开头。

### <a name="syntax"></a>语法

```cpp
iterator begin();
```

### <a name="remarks"></a>备注

成员函数返回一个双向迭代器，该迭代器指定受控序列的第一个元素，或刚超出空序列的末尾。 用于获取一个迭代器，该迭代器指定受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_map_begin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Mymap::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*++begin() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*begin() = [a 1]
*++begin() = [b 2]
```

## <a name="mapclear-stlclr"></a><a name="clear"></a>map：： clear （STL/CLR）

删除所有元素。

### <a name="syntax"></a>语法

```cpp
void clear();
```

### <a name="remarks"></a>备注

成员函数有效地调用[map：： erase （stl/clr）](../dotnet/map-erase-stl-clr.md) `(` [map：： begin （stl/clr）](../dotnet/map-begin-stl-clr.md) `(),` [map：： end （stl/clr）](../dotnet/map-end-stl-clr.md) `())` 。 用于确保受控序列为空。

### <a name="example"></a>示例

```cpp
// cliext_map_clear.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0
[a 1] [b 2]
size() = 0
```

## <a name="mapconst_iterator-stlclr"></a><a name="const_iterator"></a>map：： const_iterator （STL/CLR）

受控序列的常量迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>备注

该类型描述 `T2` 可用作受控序列的常量双向迭代器的未指定类型的对象。

### <a name="example"></a>示例

```cpp
// cliext_map_const_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapconst_reference-stlclr"></a><a name="const_reference"></a>map：： const_reference （STL/CLR）

元素的常量引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>备注

类型描述对元素的常量引用。

### <a name="example"></a>示例

```cpp
// cliext_map_const_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymap::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>map：： const_reverse_iterator （STL/CLR）

受控序列的常量反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述 `T4` 可用作受控序列的常量反向迭代器的未指定类型的对象。

### <a name="example"></a>示例

```cpp
// cliext_map_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="mapcount-stlclr"></a><a name="count"></a>map：： count （STL/CLR）

查找与指定键匹配的元素数。

### <a name="syntax"></a>语法

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

该成员函数将返回受控序列中与*键*具有等效排序的元素的数目。 用于确定受控序列中当前与指定键匹配的元素数。

### <a name="example"></a>示例

```cpp
// cliext_map_count.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="mapdifference_type-stlclr"></a><a name="difference_type"></a>map：:d ifference_type （STL/CLR）

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>备注

该类型描述了可能的负元素计数。

### <a name="example"></a>示例

```cpp
// cliext_map_difference_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymap::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
begin()-end() = -3
```

## <a name="mapempty-stlclr"></a><a name="empty"></a>map：： empty （STL/CLR）

测试元素是否存在。

### <a name="syntax"></a>语法

```cpp
bool empty();
```

### <a name="remarks"></a>备注

对于空受控序列，该成员函数返回 true。 它等效于[map：： size （STL/CLR）](../dotnet/map-size-stl-clr.md) `() == 0` 。 用于测试映射是否为空。

### <a name="example"></a>示例

```cpp
// cliext_map_empty.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="mapend-stlclr"></a><a name="end"></a>map：： end （STL/CLR）

指定受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
iterator end();
```

### <a name="remarks"></a>备注

成员函数返回一个双向迭代器，它指向刚超出受控序列末尾的位置。 用于获取一个迭代器，该迭代器指定受控序列的末尾;如果受控序列的长度发生更改，则其状态不会更改。

### <a name="example"></a>示例

```cpp
// cliext_map_end.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Mymap::iterator it = c1.end();
    --it;
    --it;
    System::Console::WriteLine("*-- --end() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*--end() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

## <a name="mapequal_range-stlclr"></a><a name="equal_range"></a>map：： equal_range （STL/CLR）

查找与指定键匹配的范围。

### <a name="syntax"></a>语法

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

此成员函数返回一对迭代器 `cliext::pair<iterator, iterator>(` [map：： lower_bound （stl/clr）](../dotnet/map-lower-bound-stl-clr.md) `(key),` [map：： upper_bound （stl/clr）](../dotnet/map-upper-bound-stl-clr.md) `(key))` 。 用于确定受控序列中当前与指定键匹配的元素范围。

### <a name="example"></a>示例

```cpp
// cliext_map_equal_range.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_iter Pairii;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("[{0} {1}] ",
            pair1.first->first, pair1.first->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
equal_range(L'x') empty = True
[b 2]
```

## <a name="maperase-stlclr"></a><a name="erase"></a>map：： erase （STL/CLR）

移除指定位置处的元素。

### <a name="syntax"></a>语法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
```

#### <a name="parameters"></a>参数

*first*<br/>
要清除的范围的开头。

*key*<br/>
要清除的键值。

*last*<br/>
要清除的范围的结束。

*where*<br/>
要清除的元素。

### <a name="remarks"></a>备注

第一个成员函数删除由*where*指向的受控序列的元素，并返回一个迭代器，该迭代器指定在删除的元素之外保留的第一个元素; 如果此类元素不存在，则为[map：： end （STL/CLR）](../dotnet/map-end-stl-clr.md) `()` 。 使用它可以删除单个元素。

第二个成员函数删除范围 [，）中的受控序列的元素， `first` `last` 并返回一个迭代器，该迭代器指定删除的任何元素之外保留的第一个元素; `end()` 如果此类元素不存在，则为。 使用它可以删除零个或多个连续元素。

第三个成员函数删除受控序列中其键与*键*具有等效顺序的任何元素，并返回所移除的元素数的计数。 使用它可删除与指定键匹配的所有元素并对其进行计数。

每个元素擦除与受控序列中的元素数的对数成正比。

### <a name="example"></a>示例

```cpp
// cliext_map_erase.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    cliext::map<wchar_t, int> c1;
    c1.insert(cliext::map<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::map<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::map<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase all but end
    it = c1.end();
    it = c1.erase(c1.begin(), --it);
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",
        it->first, it->second);
    System::Console::WriteLine("size() = {0}", c1.size());

    // erase end
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
erase(begin()) = [b 2]
[b 2] [c 3] [d 4] [e 5]
erase(begin(), end()-1) = [e 5]
size() = 1
erase(L'x') = 0
erase(L'e') = 1
```

## <a name="mapfind-stlclr"></a><a name="find"></a>map：： find （STL/CLR）

查找与指定键匹配的元素。

### <a name="syntax"></a>语法

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

如果受控序列中的至少一个元素具有与*键*等效的排序，则成员函数将返回一个指定这些元素之一的迭代器;否则，它将返回[map：： end （STL/CLR）](../dotnet/map-end-stl-clr.md) `()` 。 用于查找当前位于受控序列中的元素，该元素与指定的键匹配。

### <a name="example"></a>示例

```cpp
// cliext_map_find.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Mymap::iterator it = c1.find(L'b');
    System::Console::WriteLine("find {0} = [{1} {2}]",
        L'b', it->first, it->second);

    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
find A = False
find b = [b 2]
find C = False
```

## <a name="mapgeneric_container-stlclr"></a><a name="generic_container"></a>map：： generic_container （STL/CLR）

容器的泛型接口的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>备注

类型描述此模板容器类的泛型接口。

### <a name="example"></a>示例

```cpp
// cliext_map_generic_container.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Mymap::make_value(L'e', 5));
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3] [d 4] [e 5]
```

## <a name="mapgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>map：： generic_iterator （STL/CLR）

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
// cliext_map_generic_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
    System::Console::Write("[{0} {1}] ", gcval->first, gcval->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="mapgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>map：： generic_reverse_iterator （STL/CLR）

用于容器的泛型接口的反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可与此模板容器类的泛型接口一起使用的一般反向迭代器。

### <a name="example"></a>示例

```cpp
// cliext_map_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_reverse_iterator gcit = gc1->rbegin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="mapgeneric_value-stlclr"></a><a name="generic_value"></a>map：： generic_value （STL/CLR）

用于容器的泛型接口的元素类型。

### <a name="syntax"></a>语法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>备注

类型描述了一个类型为的对象 `GValue` ，该对象描述用于此模板容器类的泛型接口的存储元素值。

### <a name="example"></a>示例

```cpp
// cliext_map_generic_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="mapinsert-stlclr"></a><a name="insert"></a>map：： insert （STL/CLR）

添加元素。

### <a name="syntax"></a>语法

```cpp
cliext::pair<iterator, bool> insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>参数

*first*<br/>
要插入的范围的开头。

*last*<br/>
要插入的范围的末尾。

*然后*<br/>
要插入的枚举。

*初始值*<br/>
要插入的项值。

*where*<br/>
容器中要插入的位置（仅提示）。

### <a name="remarks"></a>备注

每个成员函数都插入由剩余操作数指定的序列。

第一个成员函数将使用值*val*来插入元素，并返回一对值 `X` 。 如果 `X.second` 为 true，则 `X.first` 指定新插入的元素; 否则 `X.first` 指定一个具有等效排序的元素，并且不插入新元素。 用于插入单个元素。

第二个成员函数插入具有值*val*的元素，并使用*where*作为提示（以提高性能），并返回指定新插入的元素的迭代器。 使用它可以插入一个元素，该元素可能与你知道的元素相邻。

第三个成员函数插入序列 [ `first` ， `last` ）。 用于插入从另一个序列复制的零个或多个元素。

第四个成员函数插入由*权限*指定的序列。 使用它可以插入枚举器描述的序列。

每个元素插入时间与受控序列中的元素数的对数成正比。 但是，如果指定一个在插入点附近指定元素的提示，则可能会在分期常量时间内进行插入。

### <a name="example"></a>示例

```cpp
// cliext_map_insert.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_bool Pairib;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
// insert a single value, success and failure
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    pair1 = c1.insert(Mymap::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    Mymap::iterator it =
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Mymap c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Mymap c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Mymap::value_type>^)%c1);
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [[x 24] True]
insert([L'b' 2]) = [[b 2] False]
[a 1] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [c 3] [x 24]
[a 1] [b 2] [c 3] [x 24] [y 25]
```

## <a name="mapiterator-stlclr"></a><a name="iterator"></a>map：： iterator （STL/CLR）

受控序列的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>备注

该类型描述 `T1` 可用作受控序列的双向迭代器的未指定类型的对象。

### <a name="example"></a>示例

```cpp
// cliext_map_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapkey_comp-stlclr"></a><a name="key_comp"></a>map：： key_comp （STL/CLR）

复制两个键的排序委托。

### <a name="syntax"></a>语法

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>备注

此成员函数返回用于对受控序列进行排序的排序委托。 用于对两个键进行比较。

### <a name="example"></a>示例

```cpp
// cliext_map_key_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="mapkey_compare-stlclr"></a><a name="key_compare"></a>map：： key_compare （STL/CLR）

两个键的排序委托。

### <a name="syntax"></a>语法

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>备注

类型是委托的同义词，它确定其密钥参数的顺序。

### <a name="example"></a>示例

```cpp
// cliext_map_key_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="mapkey_type-stlclr"></a><a name="key_type"></a>map：： key_type （STL/CLR）

排序键的类型。

### <a name="syntax"></a>语法

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>备注

该类型是模板参数*键*的同义词。

### <a name="example"></a>示例

```cpp
// cliext_map_key_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymap::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="maplower_bound-stlclr"></a><a name="lower_bound"></a>map：： lower_bound （STL/CLR）

查找与指定键匹配的范围的开头。

### <a name="syntax"></a>语法

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

成员函数确定 `X` 受控序列中对*key*具有等效顺序的第一个元素。 如果此类元素不存在，它将返回[map：： end （STL/CLR）](../dotnet/map-end-stl-clr.md) `()` ; 否则，它将返回指定的迭代器 `X` 。 用于查找当前在受控序列中与指定键匹配的一系列元素的开头。

### <a name="example"></a>示例

```cpp
// cliext_map_lower_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Mymap::iterator it = c1.lower_bound(L'a');
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.lower_bound(L'b');
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
lower_bound(L'x')==end() = True
*lower_bound(L'a') = [a 1]
*lower_bound(L'b') = [b 2]
```

## <a name="mapmake_value-stlclr"></a><a name="make_value"></a>map：： make_value （STL/CLR）

构造一个值对象。

### <a name="syntax"></a>语法

```cpp
static value_type make_value(key_type key, mapped_type mapped);
```

#### <a name="parameters"></a>参数

*key*<br/>
要使用的密钥值。

*贴*<br/>
要搜索的映射值。

### <a name="remarks"></a>备注

成员函数返回一个 `value_type` 对象，其键为*key* ，并*映射*其映射值。 使用它来编写适用于多个其他成员函数的对象。

### <a name="example"></a>示例

```cpp
// cliext_map_make_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapmap-stlclr"></a><a name="map"></a>map：： map （STL/CLR）

构造容器对象。

### <a name="syntax"></a>语法

```cpp
map();
explicit map(key_compare^ pred);
map(map<Key, Mapped>% right);
map(map<Key, Mapped>^ right);
template<typename InIter>
    mapmap(InIter first, InIter last);
template<typename InIter>
    map(InIter first, InIter last,
        key_compare^ pred);
map(System::Collections::Generic::IEnumerable<GValue>^ right);
map(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>参数

*first*<br/>
要插入的范围的开头。

*last*<br/>
要插入的范围的末尾。

*pred*<br/>
受控序列的排序谓词。

*然后*<br/>
要插入的对象或范围。

### <a name="remarks"></a>备注

构造函数：

`map();`

用默认的排序谓词初始化没有元素的受控序列 `key_compare()` 。 使用它可以指定一个空的初始受控序列，并使用默认的排序谓词。

构造函数：

`explicit map(key_compare^ pred);`

用排序谓词*pred*初始化不包含元素的受控序列。 使用此方法可以指定一个具有指定排序谓词的空的初始受控序列。

构造函数：

`map(map<Key, Mapped>% right);`

用序列 [，）初始化受控序列 `right.begin()` `right.end()` ，并带有默认的排序谓词。 使用此方法可以指定初始受控序列，该序列是由 map 对象*权限*控制的序列的副本，具有默认的排序谓词。

构造函数：

`map(map<Key, Mapped>^ right);`

用序列 [，）初始化受控序列 `right->begin()` `right->end()` ，并带有默认的排序谓词。 使用此方法可以指定初始受控序列，该序列是由 map 对象*权限*控制的序列的副本，具有默认的排序谓词。

构造函数：

`template<typename InIter> map(InIter first, InIter last);`

用序列 [，）初始化受控序列 `first` `last` ，并带有默认的排序谓词。 使用它可以通过默认排序谓词使受控序列成为另一个序列的副本。

构造函数：

`template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`

用序列 [，）初始化受控序列 `first` `last` ，其排序谓词为*pred*。 使用此方法可以通过指定的排序谓词使受控序列成为另一个序列的副本。

构造函数：

`map(System::Collections::Generic::IEnumerable<Key>^ right);`

使用默认排序谓词，*用枚举器*指定的序列初始化受控序列。 使用此方法可以通过默认的排序谓词，使受控序列成为枚举器描述的另一个序列的副本。

构造函数：

`map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

使用排序谓词*pred*，*通过枚举器*指定的序列初始化受控序列。 它用于使受控序列成为使用指定排序谓词的枚举器所描述的另一序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_map_construct.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
// construct an empty container
    Mymap c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymap c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymap c3(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymap c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymap c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3);
    for each (Mymap::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymap c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying another container
    Mymap c7(c4);
    for each (Mymap::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mymap c8(%c3);
    for each (Mymap::value_type elem in c8)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
```

## <a name="mapmapped_type-stlclr"></a><a name="mapped_type"></a>map：： mapped_type （STL/CLR）

与每个键关联的映射值的类型。

### <a name="syntax"></a>语法

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>备注

类型是*映射*的模板参数的同义词。

### <a name="example"></a>示例

```cpp
// cliext_map_mapped_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Mymap::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="mapoperator-stlclr"></a><a name="op_as"></a>map：： operator = （STL/CLR）

替换受控序列。

### <a name="syntax"></a>语法

```cpp
map<Key, Mapped>% operator=(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>参数

*然后*<br/>
用于复制的容器。

### <a name="remarks"></a>备注

成员运算符*直接*复制到对象，然后返回 **`*this`** 。 用于将受控序列替换为*右侧*受控序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_map_operator_as.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2 = c1;
    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="mapoperatorstlclr"></a><a name="op"></a>map：： operator （STL/CLR）

将键映射到其关联的映射值。

### <a name="syntax"></a>语法

```cpp
mapped_type operator[](key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

成员函数致力于查找具有等效*排序的元素。* 如果找到一个，则返回关联的映射值;否则，它将插入 `value_type(key, mapped_type())` 并返回关联的（默认）映射值。 使用它可以查找给定了其关联键的映射值，或者，如果未找到键，则可确保该项存在。

### <a name="example"></a>示例

```cpp
// cliext_map_operator_sub.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("c1[{0}] = {1}",
        L'A', c1[L'A']);
    System::Console::WriteLine("c1[{0}] = {1}",
        L'b', c1[L'b']);

    // redisplay altered contents
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // alter mapped values and redisplay
    c1[L'A'] = 10;
    c1[L'c'] = 13;
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
c1[A] = 0
c1[b] = 2
[A 0] [a 1] [b 2] [c 3]
[A 10] [a 1] [b 2] [c 13]
```

## <a name="maprbegin-stlclr"></a><a name="rbegin"></a>map：： rbegin （STL/CLR）

指定反向受控序列的开头。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器，该迭代器指定受控序列的最后一个元素，或刚超出空序列的开头。 因此，它指定反向序列的 `beginning`。 用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_map_rbegin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*rbegin() = [c 3]
*++rbegin() = [b 2]
```

## <a name="mapreference-stlclr"></a><a name="reference"></a>map：： reference （STL/CLR）

元素的引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>备注

类型描述对元素的引用。

### <a name="example"></a>示例

```cpp
// cliext_map_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymap::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="maprend-stlclr"></a><a name="rend"></a>map：： rend （STL/CLR）

指定反向受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器，该迭代器指向刚刚超出受控序列的开头。 因此，它指定反向序列的 `end`。 用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 末尾，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。

### <a name="example"></a>示例

```cpp
// cliext_map_rend.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rend();
    --rit;
    --rit;
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*--rend() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --rend() = [b 2]
*--rend() = [a 1]
```

## <a name="mapreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>map：： reverse_iterator （STL/CLR）

受控序列的反向迭代器的类型。

### <a name="syntax"></a>语法

```
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_map_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="mapsize-stlclr"></a><a name="size"></a>map：： size （STL/CLR）

对元素数进行计数。

### <a name="syntax"></a>语法

```cpp
size_type size();
```

### <a name="remarks"></a>备注

成员函数将返回受控序列的长度。 用于确定受控序列中当前的元素数。 如果你只关心序列的大小是否为非零，请参阅[map：： empty （STL/CLR）](../dotnet/map-empty-stl-clr.md) `()` 。

### <a name="example"></a>示例

```cpp
// cliext_map_size.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Mymap::make_value(L'd', 4));
    c1.insert(Mymap::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="mapsize_type-stlclr"></a><a name="size_type"></a>map：： size_type （STL/CLR）

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>备注

该类型描述了一个非负元素计数。

### <a name="example"></a>示例

```cpp
// cliext_map_size_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::size_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="mapswap-stlclr"></a><a name="swap"></a>map：： swap （STL/CLR）

交换两个容器的内容。

### <a name="syntax"></a>语法

```cpp
void swap(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>参数

*然后*<br/>
要与其交换内容的容器。

### <a name="remarks"></a>备注

成员函数交换和右之间的受控 **`this`** 序列*right*。 它在固定时间内执行此操作，并且不会引发异常。 使用该方法可以快速交换两个容器的内容。

### <a name="example"></a>示例

```cpp
// cliext_map_swap.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymap c2;
    c2.insert(Mymap::make_value(L'd', 4));
    c2.insert(Mymap::make_value(L'e', 5));
    c2.insert(Mymap::make_value(L'f', 6));
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[d 4] [e 5] [f 6]
[d 4] [e 5] [f 6]
[a 1] [b 2] [c 3]
```

## <a name="mapto_array-stlclr"></a><a name="to_array"></a>map：： to_array （STL/CLR）

将受控序列复制到新数组。

### <a name="syntax"></a>语法

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>备注

此成员函数返回包含受控序列的数组。 可以使用它以数组形式获取受控序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_map_to_array.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Mymap::value_type>^ a1 = c1.to_array();

    c1.insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Mymap::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="mapupper_bound-stlclr"></a><a name="upper_bound"></a>map：： upper_bound （STL/CLR）

查找与指定键匹配的范围的末尾。

### <a name="syntax"></a>语法

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

成员函数确定 `X` 受控序列中对*key*具有等效排序的最后一个元素。 如果此类元素不存在，或者如果 `X` 是受控序列中的最后一个元素，则它将返回[map：： END （STL/CLR）](../dotnet/map-end-stl-clr.md) `()` ; 否则，它将返回指定第一个元素的迭代器 `X` 。 使用它可以查找受控序列中当前与指定键匹配的元素序列的末尾。

### <a name="example"></a>示例

```cpp
// cliext_map_upper_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Mymap::iterator it = c1.upper_bound(L'a');
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.upper_bound(L'b');
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
upper_bound(L'x')==end() = True
*upper_bound(L'a') = [b 2]
*upper_bound(L'b') = [c 3]
```

## <a name="mapvalue_comp-stlclr"></a><a name="value_comp"></a>map：： value_comp （STL/CLR）

复制两个元素值的排序委托。

### <a name="syntax"></a>语法

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>备注

此成员函数返回用于对受控序列进行排序的排序委托。 用于比较两个元素值。

### <a name="example"></a>示例

```cpp
// cliext_map_value_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="mapvalue_compare-stlclr"></a><a name="value_compare"></a>map：： value_compare （STL/CLR）

两个元素值的排序委托。

### <a name="syntax"></a>语法

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>备注

类型是委托的同义词，用于确定其值参数的顺序。

### <a name="example"></a>示例

```cpp
// cliext_map_value_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="mapvalue_type-stlclr"></a><a name="value_type"></a>map：： value_type （STL/CLR）

元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>备注

该类型是 `generic_value` 的同义词。

### <a name="example"></a>示例

```cpp
// cliext_map_value_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymap::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="operator-map-stlclr"></a><a name="op_neq"></a>operator！ = （map）（STL/CLR）

列表不相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key,
    typename Mapped>
    bool operator!=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `!(left == right)` 。 使用此方法可以测试在按元素对两个映射进行*比较时，是否按原样对**左侧*进行排序。

### <a name="example"></a>示例

```cpp
// cliext_map_operator_ne.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-map-stlclr"></a><a name="op_lt"></a>运算符 &lt; （map）（STL/CLR）

列表小于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key,
    typename Mapped>
    bool operator<(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

如果为，则运算符函数返回 true，适用于的最低位置 `i` `!(right[i] < left[i])` `left[i] < right[i]` 。 否则，它会返回 `left->size() < right->size()` 用于测试在按元素对两个映射*right*进行比较的情况下，是否向*左*排序。

### <a name="example"></a>示例

```cpp
// cliext_map_operator_lt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-map-stlclr"></a><a name="op_lteq"></a>operator &lt; = （map）（STL/CLR）

列表小于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key,
    typename Mapped>
    bool operator<=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `!(right < left)` 。 使用此方法可以测试是否在按元素对两个映射进行*比较时向**左*排序。

### <a name="example"></a>示例

```cpp
// cliext_map_operator_le.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-map-stlclr"></a><a name="op_eq"></a>operator = = （map）（STL/CLR）

列出相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key,
    typename Mapped>
    bool operator==(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

仅当由*左*和*右*控制的序列具有相同的长度，并且对于每个位置，operator 函数才返回 true `i` `left[i] ==` `right[i]` 。 使用此方法可以*测试在按*元素对两个映射进行比较时，是否*向左*排序。

### <a name="example"></a>示例

```cpp
// cliext_map_operator_eq.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-map-stlclr"></a><a name="op_gt"></a>运算符 &gt; （map）（STL/CLR）

列表大于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key,
    typename Mapped>
    bool operator>(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `right` `<` `left` 。 使用此方法可以*测试是否在*按元素对两个映射进行比较时向*右*排序。

### <a name="example"></a>示例

```cpp
// cliext_map_operator_gt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-map-stlclr"></a><a name="op_gteq"></a>operator &gt; = （map）（STL/CLR）

列出大于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key,
    typename Mapped>
    bool operator>=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>参数

*左中*<br/>
要比较的左容器。

*然后*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

Operator 函数返回 `!(left` `<` `right)` 。 用于测试在按元素对两个映射进行比较*时，是否向**左*排序。

### <a name="example"></a>示例

```cpp
// cliext_map_operator_ge.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
