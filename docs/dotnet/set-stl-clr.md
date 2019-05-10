---
title: set (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::set
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::set::begin
- cliext::set::clear
- cliext::set::const_iterator
- cliext::set::const_reference
- cliext::set::const_reverse_iterator
- cliext::set::count
- cliext::set::difference_type
- cliext::set::empty
- cliext::set::end
- cliext::set::equal_range
- cliext::set::erase
- cliext::set::find
- cliext::set::generic_container
- cliext::set::generic_iterator
- cliext::set::generic_reverse_iterator
- cliext::set::generic_value
- cliext::set::insert
- cliext::set::iterator
- cliext::set::key_comp
- cliext::set::key_compare
- cliext::set::key_type
- cliext::set::lower_bound
- cliext::set::make_value
- cliext::set::operator=
- cliext::set::rbegin
- cliext::set::reference
- cliext::set::rend
- cliext::set::reverse_iterator
- cliext::set::set
- cliext::set::size
- cliext::set::size_type
- cliext::set::swap
- cliext::set::to_array
- cliext::set::upper_bound
- cliext::set::value_comp
- cliext::set::value_compare
- cliext::set::value_type
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
- operator!= (set) member [STL/CLR]
- operator< (set) member [STL/CLR]
- operator<= (set) member [STL/CLR]
- operator== (set) member [STL/CLR]
- operator> (set) member [STL/CLR]
- operator>= (set) member [STL/CLR]
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
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- set member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
ms.openlocfilehash: 612c0772504043a99f3a2ae9fa7da9c791076d6a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384642"
---
# <a name="set-stlclr"></a>set (STL/CLR)

此模板类描述一个对象，用于控制不同长度序列元素的双向访问。 使用容器`set`来管理一系列元素作为 （几乎） 平衡有序树中的节点，每个存储一个元素。

在下面的说明`GValue`等同于`GKey`，后者又是与相同*密钥*除非后一种是 ref 类型，在这种情况下它是`Key^`。

## <a name="syntax"></a>语法

```cpp
template<typename Key>
    ref class set
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>参数

*Key*<br/>
受控序列中元素的关键组件的类型。

## <a name="requirements"></a>要求

**标头：** \<cliext/设置 >

**Namespace:** cliext

## <a name="declarations"></a>声明

|类型定义|描述|
|---------------------|-----------------|
|[set::const_iterator (STL/CLR)](#const_iterator)|受控序列的常量迭代器的类型。|
|[set::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|
|[set::difference_type (STL/CLR)](#difference_type)|两个元素之间的 （可能是带符号） 距离的类型。|
|[set::generic_container (STL/CLR)](#generic_container)|泛型接口的容器的类型。|
|[set::generic_iterator (STL/CLR)](#generic_iterator)|泛型接口的容器的迭代器的类型。|
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型接口的反向迭代器的类型。|
|[set::generic_value (STL/CLR)](#generic_value)|容器的泛型接口的元素的类型。|
|[set::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|
|[set::key_compare (STL/CLR)](#key_compare)|两个键排序委托。|
|[set::key_type (STL/CLR)](#key_type)|排序键的类型。|
|[set::reference (STL/CLR)](#reference)|元素的引用的类型。|
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|受控序列的反向迭代器的类型。|
|[set::size_type (STL/CLR)](#size_type)|两个元素之间的 （非负值） 距离的类型。|
|[set::value_compare (STL/CLR)](#value_compare)|两个元素值排序委托。|
|[set::value_type (STL/CLR)](#value_type)|元素的类型。|

|成员函数|描述|
|---------------------|-----------------|
|[set::begin (STL/CLR)](#begin)|指定受控序列的开头。|
|[set::clear (STL/CLR)](#clear)|删除所有元素。|
|[set::count (STL/CLR)](#count)|对与指定的键匹配的元素进行计数。|
|[set::empty (STL/CLR)](#empty)|测试元素是否存在。|
|[set::end (STL/CLR)](#end)|指定受控序列的末尾。|
|[set::equal_range (STL/CLR)](#equal_range)|查找与指定键匹配的范围。|
|[set::erase (STL/CLR)](#erase)|移除指定位置处的元素。|
|[set::find (STL/CLR)](#find)|查找与指定键匹配的元素。|
|[set::insert (STL/CLR)](#insert)|添加元素。|
|[set::key_comp (STL/CLR)](#key_comp)|将复制两个键的排序委托。|
|[set::lower_bound (STL/CLR)](#lower_bound)|查找与指定的键匹配的范围的起始处。|
|[set::make_value (STL/CLR)](#make_value)|构造一个值对象。|
|[set::rbegin (STL/CLR)](#rbegin)|指定反向受控序列的开头。|
|[set::rend (STL/CLR)](#rend)|指定反向受控序列的末尾。|
|[set::set (STL/CLR)](#set)|构造容器对象。|
|[set::size (STL/CLR)](#size)|对元素数进行计数。|
|[set::swap (STL/CLR)](#swap)|交换两个容器的内容。|
|[set::to_array (STL/CLR)](#to_array)|将受控的序列复制到新数组。|
|[set::upper_bound (STL/CLR)](#upper_bound)|查找与指定的键匹配的范围末尾。|
|[set::value_comp (STL/CLR)](#value_comp)|将复制两个元素值的排序委托。|

|运算符|描述|
|--------------|-----------------|
|[set::operator= (STL/CLR)](#op_as)|替换受控序列。|
|[operator!= (set) (STL/CLR)](#op_neq)|确定是否`set`对象不等于另一个`set`对象。|
|[operator< (set) (STL/CLR)](#op_lt)|确定是否`set`对象是否小于另一个`set`对象。|
|[operator<= (set) (STL/CLR)](#op_lteq)|确定是否`set`对象是否小于或等于另一个`set`对象。|
|[operator== (set) (STL/CLR)](#op_eq)|确定是否`set`对象是否等于另一个`set`对象。|
|[operator> (set) (STL/CLR)](#op_gt)|确定是否`set`对象是否大于另一个`set`对象。|
|[operator>= (set) (STL/CLR)](#op_gteq)|确定是否`set`对象是否大于或等于另一个`set`对象。|

## <a name="interfaces"></a>接口

|接口|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|重复的对象。|
|<xref:System.Collections.IEnumerable>|通过元素的序列。|
|<xref:System.Collections.ICollection>|维护组元素。|
|<xref:System.Collections.Generic.IEnumerable%601>|通过类型化的元素进行排序。|
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|
|ITree\<键，值 >|维护泛型容器。|

## <a name="remarks"></a>备注

该对象分配并释放存储单独的节点作为其控制的序列。 它将元素插入到通过更改节点永远不会通过将一个节点的内容复制到另一个之间的链接保持有序 （几乎） 平衡树。 这意味着您可以插入和删除自由地不影响剩余元素的元素。

该对象通过调用类型的存储的委托对象控制的序列进行排序[set:: key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)。 在构造集; 时，可以指定存储的委托对象如果指定没有委托对象，默认值是比较`operator<(key_type, key_type)`。 通过调用成员函数来访问此存储的对象[set:: key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`。

此类委托对象必须进行严格弱排序的键的类型在施加[set:: key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)。 这意味着，任何两个密钥`X`和`Y`:

`key_comp()(X, Y)` 返回相同的布尔值导致在每次调用。

如果`key_comp()(X, Y)`为 true，则`key_comp()(Y, X)`必须为 false。

如果`key_comp()(X, Y)`为 true，然后`X`进行排序之前说过`Y`。

如果`!key_comp()(X, Y) && !key_comp()(Y, X)`为 true，然后`X`和`Y`被视为具有等效顺序。

任何元素`X`前面`Y`受控序列中`key_comp()(Y, X)`为 false。 （对于默认委托对象，密钥永远不会减小值。）与模板类不同[设置](../dotnet/set-stl-clr.md)，模板类的对象`set`不需要的所有元素的键是唯一。 （两个或多个键可以具有等效顺序。）

每个元素具有键和值。 允许查找、 插入和删除具有多个操作的元素数的对数成正比的任意元素的序列 （对数时间） 中的方式被表示序列。 此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。

一组支持双向迭代器，这意味着您可以转到给定迭代器，指定受控序列中的元素的相邻元素步骤。 特殊的头节点对应于返回的迭代器[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`。 如果存在，可以递减此迭代器，用于访问受控序列中的最后一个元素。 可以递增 set 迭代器来访问头节点，并将然后比较等于`end()`。 但不能取消引用返回的迭代器`end()`。

请注意，不能指直接给定其数字位置-需要随机访问迭代器的 set 元素。

设置迭代器将存储到其关联的集节点，后者又将存储的句柄关联的容器的句柄。 迭代器只能用于其关联的容器对象。 设置迭代器保持有效，只要其关联的集节点是与某些组相关联。 此外，有效的迭代器是现在--可以使用它来访问或更改，只要不等于此元素的值指定- `end()`。

擦除或删除元素调用析构函数为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是 ref 类的容器可确保任何元素的生存期长于容器。 但请注意，容器的句柄 does*不*销毁它的元素。

## <a name="members"></a>成员

## <a name="begin"></a>set::begin (STL/CLR)

指定受控序列的开头。

### <a name="syntax"></a>语法

```cpp
iterator begin();
```

### <a name="remarks"></a>备注

成员函数返回指定受控序列，或刚超出空序列末尾的第一个元素的双向迭代器。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改受控制的序列，但其状态的开头。

### <a name="example"></a>示例

```cpp
// cliext_set_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="clear"></a>set::clear (STL/CLR)

删除所有元素。

### <a name="syntax"></a>语法

```cpp
void clear();
```

### <a name="remarks"></a>备注

成员函数有效地调用[set:: erase (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(` [set:: begin (STL/CLR)](../dotnet/set-begin-stl-clr.md) `(),` [set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md) `())`. 用于确保受控的序列为空。

### <a name="example"></a>示例

```cpp
// cliext_set_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

// add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');

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

## <a name="const_iterator"></a>set::const_iterator (STL/CLR)

受控序列的常量迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>备注

此类型描述未指定类型的对象`T2`可充当受控序列的常量双向迭代器。

### <a name="example"></a>示例

```cpp
// cliext_set_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a>set::const_reference (STL/CLR)

元素的常量引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>备注

此类型描述的元素的常量引用。

### <a name="example"></a>示例

```cpp
// cliext_set_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a>set::const_reverse_iterator (STL/CLR)

受控序列的常量反向迭代器的类型...

### <a name="syntax"></a>语法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>备注

此类型描述未指定类型的对象`T4`可充当受控序列的常量反向迭代器。

### <a name="example"></a>示例

```cpp
// cliext_set_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="count"></a>set::count (STL/CLR)

查找与指定键匹配的元素数。

### <a name="syntax"></a>语法

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

成员函数返回具有等效顺序的受控序列中的元素数目*密钥*。 用于确定受控序列中当前与指定的键匹配的元素数。

### <a name="example"></a>示例

```cpp
// cliext_set_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
a b c
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="difference_type"></a>set::difference_type (STL/CLR)

两个元素之间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>备注

此类型描述可能是负值元素计数。

### <a name="example"></a>示例

```cpp
// cliext_set_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (Myset::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a>set::empty (STL/CLR)

测试元素是否存在。

### <a name="syntax"></a>语法

```cpp
bool empty();
```

### <a name="remarks"></a>备注

对于空受控序列，该成员函数返回 true。 它等效于[set:: size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`。 用于测试是否该集为空。

### <a name="example"></a>示例

```cpp
// cliext_set_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

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

## <a name="end"></a>set::end (STL/CLR)

指定受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
iterator end();
```

### <a name="remarks"></a>备注

成员函数返回的双向迭代器指向刚超出受控序列的末尾。 用于获取指定受控序列; 的末尾的迭代器其状态不会更改如果受控序列的长度发生更改。

### <a name="example"></a>示例

```cpp
// cliext_set_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    Myset::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
```

## <a name="equal_range"></a>set::equal_range (STL/CLR)

查找与指定键匹配的范围。

### <a name="syntax"></a>语法

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

此成员函数返回一对迭代器`cliext::pair<iterator, iterator>(` [set:: lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [set:: upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`。 用于确定受控序列中当前与指定的键匹配的元素的范围。

### <a name="example"></a>示例

```cpp
// cliext_set_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_iter Pairii;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

// display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("{0} ", *pair1.first);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
equal_range(L'x') empty = True
b
```

## <a name="erase"></a>set::erase (STL/CLR)

移除指定位置处的元素。

### <a name="syntax"></a>语法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
```

#### <a name="parameters"></a>参数

*first*<br/>
要清除范围的起始处。

*key*<br/>
若要清除的键值。

*last*<br/>
要清除范围的末尾。

*where*<br/>
要清除的元素。

### <a name="remarks"></a>备注

第一个成员函数删除由指向受控序列的元素*其中*，并返回一个迭代器，指定已移除，元素之外保留的第一个元素或[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md) `()`如果此类元素不存在。 用于删除单个元素。

第二个成员函数的范围内移除受控序列的元素 [`first`， `last`)，并返回一个迭代器，指定已删除的任何元素之外保留的第一个元素或`end()`如果没有此类元素存在... 用于删除零个或多个连续的元素。

第三个成员函数将移除其键具有等效顺序的受控任何的序列元素到*密钥*，并返回已移除的元素数的计数。 使用要删除用来计数与指定的键匹配的所有元素。

每个元素擦除需要受控序列中的元素数的对数成正比的时间。

### <a name="example"></a>示例

```cpp
// cliext_set_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

// add elements and display " b c d e"
    c1.insert(L'd');
    c1.insert(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase all but end
    Myset::iterator it = c1.end();
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

## <a name="find"></a>set::find (STL/CLR)

查找与指定键匹配的元素。

### <a name="syntax"></a>语法

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

如果受控序列中的至少一个元素具有等效排序*键*，此成员函数返回迭代器，指定其中一个元素; 否则返回[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. 用于当前与指定的键匹配的受控序列中定位的元素。

### <a name="example"></a>示例

```cpp
// cliext_set_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());
    System::Console::WriteLine("find {0} = {1}",
        L'b', *c1.find(L'b'));
    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
a b c
find A = False
find b = b
find C = False
```

## <a name="generic_container"></a>set::generic_container (STL/CLR)

泛型接口的容器的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>备注

此类型描述该类模板容器的泛型接口。

### <a name="example"></a>示例

```cpp
// cliext_set_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    gc1->insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify original and display generic
    c1.insert(L'e');
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
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

## <a name="generic_iterator"></a> set::generic_iterator (STL/CLR)

用于容器的泛型接口具有的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>备注

此类型描述可用于泛型接口为该类模板容器的泛型迭代器。

### <a name="example"></a>示例

```cpp
// cliext_set_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="generic_reverse_iterator"></a> set::generic_reverse_iterator (STL/CLR)

一个反向迭代器用于与容器的泛型接口的类型。

### <a name="syntax"></a>语法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>备注

此类型描述可用于泛型接口为该类模板容器的泛型反向迭代器。

### <a name="example"></a>示例

```cpp
// cliext_set_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_reverse_iterator gcit = gc1->rbegin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="generic_value"></a> set::generic_value (STL/CLR)

用于容器的泛型接口具有的元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>备注

此类型描述类型的对象`GValue`描述使用的存储的元素值与此模板容器类的泛型接口。

### <a name="example"></a>示例

```cpp
// cliext_set_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="insert"></a> set::insert (STL/CLR)

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
要插入范围的起始处。

*last*<br/>
要插入的范围的下限。

*right*<br/>
要插入的枚举。

*val*<br/>
要插入的密钥值。

*where*<br/>
要插入 （仅提示） 的容器中的位置。

### <a name="remarks"></a>备注

每个成员函数插入由剩余操作数指定的序列。

第一个成员函数尝试插入具有值的元素*val*，并返回一对值`X`。 如果`X.second`为 true，`X.first`指定新插入的元素; 否则为`X.first`指定具有等效的元素顺序的现有和任何新元素插入。 用于插入单个元素。

第二个成员函数将具有值的元素插入*val*，并使用*其中*作为提示 （若要提高性能），并返回一个迭代器，指定新插入的元素。 用于插入单个元素，这可能是您知道的元素相邻。

第三个成员函数将序列 [`first`， `last`)。 用于插入另一个序列中复制的零个或多个元素。

第四个成员函数将指定的序列插入*右*。 用于插入序列描述将枚举器。

每个元素插入到受控序列中需要的元素数的对数成正比的时间。 插入可发生在分期常量时间内，但是，给出一个提示，指示某个元素旁边插入点。

### <a name="example"></a>示例

```cpp
// cliext_set_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_bool Pairib;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value, unique and duplicate
    Pairib pair1 = c1.insert(L'x');
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",
        *pair1.first, pair1.second);

    pair1 = c1.insert(L'b');
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",
        *pair1.first, pair1.second);

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value with hint
    System::Console::WriteLine("insert(begin(), L'y') = {0}",
        *c1.insert(c1.begin(), L'y'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an iterator range
    Myset c2;
    Myset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an enumeration
    Myset c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(L'x') = [x True]
insert(L'b') = [b False]
a b c x
insert(begin(), L'y') = y
a b c x y
a b c x
a b c x y
```

## <a name="iterator"></a> set::iterator (STL/CLR)

受控序列的迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>备注

此类型描述未指定类型的对象`T1`可充当受控序列的双向迭代器。

### <a name="example"></a>示例

```cpp
// cliext_set_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="key_comp"></a> set::key_comp (STL/CLR)

将复制两个键的排序委托。

### <a name="syntax"></a>语法

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>备注

成员函数将返回用于受控的序列进行排序的排序委托。 用于比较两个键。

### <a name="example"></a>示例

```cpp
// cliext_set_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
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

## <a name="key_compare"></a> set::key_compare (STL/CLR)

两个键排序委托。

### <a name="syntax"></a>语法

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>备注

类型为委托，它确定其密钥的自变量的顺序的同义词。

### <a name="example"></a>示例

```cpp
// cliext_set_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
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

## <a name="key_type"></a> set::key_type (STL/CLR)

排序键的类型。

### <a name="syntax"></a>语法

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>备注

该类型是模板参数的同义词*密钥*。

### <a name="example"></a>示例

```cpp
// cliext_set_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using key_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="lower_bound"></a> set:: lower_bound (STL/CLR)

查找与指定的键匹配的范围的起始处。

### <a name="syntax"></a>语法

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

此成员函数将确定第一个元素`X`受控序列中具有相同的排序*密钥*。 如果此类元素不存在，它将返回[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; 否则它将返回一个迭代器，指定`X`。 使用要在与指定的键匹配的受控序列中当前定位的元素序列的开头。

### <a name="example"></a>示例

```cpp
// cliext_set_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    System::Console::WriteLine("*lower_bound(L'a') = {0}",
        *c1.lower_bound(L'a'));
    System::Console::WriteLine("*lower_bound(L'b') = {0}",
        *c1.lower_bound(L'b'));
    return (0);
    }
```

```Output
a b c
lower_bound(L'x')==end() = True
*lower_bound(L'a') = a
*lower_bound(L'b') = b
```

## <a name="make_value"></a> set::make_value (STL/CLR)

构造一个值对象。

### <a name="syntax"></a>语法

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
若要使用的密钥值。

### <a name="remarks"></a>备注

此成员函数返回`value_type`对象，其键是*密钥*。 您可以用它来组合使用适合与几个其他成员函数的对象。

### <a name="example"></a>示例

```cpp
// cliext_set_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(Myset::make_value(L'a'));
    c1.insert(Myset::make_value(L'b'));
    c1.insert(Myset::make_value(L'c'));

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_as"></a> set::operator= (STL/CLR)

替换受控序列。

### <a name="syntax"></a>语法

```cpp
set<Key>% operator=(set<Key>% right);
```

#### <a name="parameters"></a>参数

*right*<br/>
用于复制的容器。

### <a name="remarks"></a>备注

成员运算符副本*右*对象，然后返回`*this`。 用于替换受控的序列中的受控序列的副本*右*。

### <a name="example"></a>示例

```cpp
// cliext_set_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="rbegin"></a> set::rbegin (STL/CLR)

指定反向受控序列的开头。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器，指定受控序列，或刚超出空序列的开头的最后一个元素。 因此，它指定`beginning`反向序列。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改的相反顺序的受控的序列，但其状态开始。

### <a name="example"></a>示例

```cpp
// cliext_set_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    Myset::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
```

## <a name="reference"></a> set::reference (STL/CLR)

元素的引用的类型。

### <a name="syntax"></a>语法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>备注

此类型描述的元素的引用。

### <a name="example"></a>示例

```cpp
// cliext_set_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="rend"></a> set::rend (STL/CLR)

指定反向受控序列的末尾。

### <a name="syntax"></a>语法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>备注

成员函数返回一个反向迭代器指向刚超出开头的受控序列。 因此，它指定`end`反向序列。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改的相反顺序的受控的序列，但其状态结束。

### <a name="example"></a>示例

```cpp
// cliext_set_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
```

## <a name="reverse_iterator"></a> set::reverse_iterator (STL/CLR)

受控序列的反向迭代器的类型。

### <a name="syntax"></a>语法

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>备注

该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。

### <a name="example"></a>示例

```cpp
// cliext_set_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="set"></a> set::set (STL/CLR)

构造容器对象。

### <a name="syntax"></a>语法

```cpp
set();
explicit set(key_compare^ pred);
set(set<Key>% right);
set(set<Key>^ right);
template<typename InIter>
    setset(InIter first, InIter last);
template<typename InIter>
    set(InIter first, InIter last,
        key_compare^ pred);
set(System::Collections::Generic::IEnumerable<GValue>^ right);
set(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>参数

*first*<br/>
要插入范围的起始处。

*last*<br/>
要插入的范围的下限。

*pred*<br/>
排序谓词对受控序列。

*right*<br/>
要插入的对象或范围。

### <a name="remarks"></a>备注

构造函数：

`set();`

使用默认排序谓词初始化受控的序列不含任何元素， `key_compare()`。 用于指定一个空的初始受控的序列，使用默认排序谓词。

构造函数：

`explicit set(key_compare^ pred);`

初始化受控的序列不含任何元素，与排序谓词*pred*。 用于指定一个空的初始受控的序列，使用指定的排序谓词。

构造函数：

`set(set<Key>% right);`

初始化受控的序列与序列 [`right.begin()`， `right.end()`)，使用默认排序谓词。 用于指定副本的集对象控制的序列的初始受控的序列*右*，使用默认排序谓词。

构造函数：

`set(set<Key>^ right);`

初始化受控的序列与序列 [`right->begin()`， `right->end()`)，使用默认排序谓词。 用于指定副本的集对象控制的序列的初始受控的序列*右*，使用默认排序谓词。

构造函数：

`template<typename InIter> set(InIter first, InIter last);`

初始化受控的序列与序列 [`first`， `last`)，使用默认排序谓词。 用于使用默认排序谓词使受控的序列的另一个序列副本。

构造函数：

`template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`

初始化受控的序列与序列 [`first`， `last`)，使用排序谓词*pred*。 您可以使用它来使受控的序列的具有指定的排序谓词的另一个序列副本。

构造函数：

`set(System::Collections::Generic::IEnumerable<Key>^ right);`

初始化具有指定枚举器的序列的受控的序列*右*，使用默认排序谓词。 您可以使用它来使受控的序列描述将枚举器，使用默认排序谓词的另一个序列的副本。

构造函数：

`set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

初始化具有指定枚举器的序列的受控的序列*右*，使用排序谓词*pred*。 您可以使用它来使受控的序列的枚举器，指定排序谓词所描述的另一个序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_set_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
// construct an empty container
    Myset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an ordering rule
    Myset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    Myset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range and an ordering rule
    Myset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    Myset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration and an ordering rule
    Myset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct from a generic container
    Myset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Myset c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
a b c
size() = 0
c b a
a b c
c b a
a b c
c b a
c b a
a b c
```

## <a name="size"></a> set::size (STL/CLR)

对元素数进行计数。

### <a name="syntax"></a>语法

```cpp
size_type size();
```

### <a name="remarks"></a>备注

成员函数将返回受控序列的长度。 用于确定受控序列中当前元素的数目。 如果您关心的只是该序列是否具有非零大小，请参阅[set:: empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`。

### <a name="example"></a>示例

```cpp
// cliext_set_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

// add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');
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

## <a name="size_type"></a> set::size_type (STL/CLR)

两个元素间的带符号距离的类型。

### <a name="syntax"></a>语法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>备注

此类型描述非负元素计数。

### <a name="example"></a>示例

```cpp
// cliext_set_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::size_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="swap"></a> set::swap (STL/CLR)

交换两个容器的内容。

### <a name="syntax"></a>语法

```cpp
void swap(set<Key>% right);
```

#### <a name="parameters"></a>参数

*right*<br/>
要与其交换内容的容器。

### <a name="remarks"></a>备注

成员函数交换之间的受控的序列`this`并*右*。 它是在常量时间内，则会引发任何异常。 您将其用作一种来交换两个容器的内容的快速方法。

### <a name="example"></a>示例

```cpp
// cliext_set_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    Myset c2;
    c2.insert(L'd');
    c2.insert(L'e');
    c2.insert(L'f');
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
d e f
d e f
a b c
```

## <a name="to_array"></a> set::to_array (STL/CLR)

将受控的序列复制到新数组。

### <a name="syntax"></a>语法

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>备注

成员函数返回一个数组，包含对受控的序列。 用于获取数组形式的受控序列的副本。

### <a name="example"></a>示例

```cpp
// cliext_set_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.insert(L'd');
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

## <a name="upper_bound"></a> set::upper_bound (STL/CLR)

查找与指定的键匹配的范围末尾。

### <a name="syntax"></a>语法

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>参数

*key*<br/>
要搜索的键值。

### <a name="remarks"></a>备注

此成员函数将确定最后一个元素`X`受控序列中具有相同的排序*密钥*。 如果此类元素不存在，或者如果`X`是受控序列中的最后一个元素，它将返回[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; 否则它将返回一个迭代器，指定第一个超出元素`X`. 使用要在与指定的键匹配的受控序列中当前定位的元素序列的末尾。

### <a name="example"></a>示例

```cpp
// cliext_set_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    System::Console::WriteLine("*upper_bound(L'a') = {0}",
        *c1.upper_bound(L'a'));
    System::Console::WriteLine("*upper_bound(L'b') = {0}",
        *c1.upper_bound(L'b'));
    return (0);
    }
```

```Output
a b c
upper_bound(L'x')==end() = True
*upper_bound(L'a') = b
*upper_bound(L'b') = c
```

## <a name="value_comp"></a> set::value_comp (STL/CLR)

将复制两个元素值的排序委托。

### <a name="syntax"></a>语法

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>备注

成员函数将返回用于受控的序列进行排序的排序委托。 用于比较两个元素值。

### <a name="example"></a>示例

```cpp
// cliext_set_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_compare"></a> set::value_compare (STL/CLR)

两个元素值排序委托。

### <a name="syntax"></a>语法

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>备注

类型为委托，它确定其值参数的顺序的同义词。

### <a name="example"></a>示例

```cpp
// cliext_set_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_type"></a> set::value_type (STL/CLR)

元素的类型。

### <a name="syntax"></a>语法

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>备注

该类型是 `generic_value`的同义词。

### <a name="example"></a>示例

```cpp
// cliext_set_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using value_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_neq"></a> operator!= (set) (STL/CLR)

列出不等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key>
    bool operator!=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`!(left == right)`。 使用它来测试是否*左*未排序相同*右*当两个集都比较的元素的方式。

### <a name="example"></a>示例

```cpp
// cliext_set_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_lt"></a> operator&lt; (set) (STL/CLR)

列表小于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key>
    bool operator<(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回 true 当对于最低的位置`i`为其`!(right[i] < left[i])`它是还 true 的`left[i] < right[i]`。 否则，它将返回`left->size() < right->size()`使用它来测试是否*左*进行排序之前*右*当两个集都比较的元素的方式。

### <a name="example"></a>示例

```cpp
// cliext_set_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_lteq"></a> operator&lt;= (set) (STL/CLR)

列表小于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key>
    bool operator<=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`!(right < left)`。 使用它来测试是否*左*未排序后*右*当两个集都比较的元素的方式。

### <a name="example"></a>示例

```cpp
// cliext_set_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_eq"></a> operator== (set) (STL/CLR)

列表相等比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key>
    bool operator==(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数才返回 true，序列由控制*左*并*右*具有相同的长度和每个位置`i`， `left[i] ==` `right[i]`。 使用它来测试是否*左*进行排序相同*右*当两个集都比较的元素的方式。

### <a name="example"></a>示例

```cpp
// cliext_set_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_gt"></a> operator&gt; (set) (STL/CLR)

大于比较的列表。

### <a name="syntax"></a>语法

```cpp
template<typename Key>
    bool operator>(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数将返回`right` `<` `left`。 使用它来测试是否*左*进行排序后*右*当两个集都比较的元素的方式。

### <a name="example"></a>示例

```cpp
// cliext_set_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_gteq"></a> operator&gt;= (set) (STL/CLR)

列表大于或等于比较。

### <a name="syntax"></a>语法

```cpp
template<typename Key>
    bool operator>=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>参数

*left*<br/>
要比较的左容器。

*right*<br/>
要比较的右容器。

### <a name="remarks"></a>备注

运算符函数返回`!(left < right)`。 使用它来测试是否*左*未排序之前*右*当两个集都比较的元素的方式。

### <a name="example"></a>示例

```cpp
// cliext_set_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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