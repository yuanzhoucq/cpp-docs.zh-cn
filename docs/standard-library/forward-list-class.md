---
title: forward_list 类
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::forward_list
- forward_list/std::forward_list::allocator_type
- forward_list/std::forward_list::const_iterator
- forward_list/std::forward_list::const_pointer
- forward_list/std::forward_list::const_reference
- forward_list/std::forward_list::difference_type
- forward_list/std::forward_list::iterator
- forward_list/std::forward_list::pointer
- forward_list/std::forward_list::reference
- forward_list/std::forward_list::size_type
- forward_list/std::forward_list::value_type
- forward_list/std::forward_list::assign
- forward_list/std::forward_list::before_begin
- forward_list/std::forward_list::begin
- forward_list/std::forward_list::cbefore_begin
- forward_list/std::forward_list::cbegin
- forward_list/std::forward_list::cend
- forward_list/std::forward_list::clear
- forward_list/std::forward_list::emplace_after
- forward_list/std::forward_list::emplace_front
- forward_list/std::forward_list::empty
- forward_list/std::forward_list::end
- forward_list/std::forward_list::erase_after
- forward_list/std::forward_list::front
- forward_list/std::forward_list::get_allocator
- forward_list/std::forward_list::insert_after
- forward_list/std::forward_list::max_size
- forward_list/std::forward_list::merge
- forward_list/std::forward_list::pop_front
- forward_list/std::forward_list::push_front
- forward_list/std::forward_list::remove
- forward_list/std::forward_list::remove_if
- forward_list/std::forward_list::resize
- forward_list/std::forward_list::reverse
- forward_list/std::forward_list::sort
- forward_list/std::forward_list::splice_after
- forward_list/std::forward_list::swap
- forward_list/std::forward_list::unique
helpviewer_keywords:
- std::forward_list
- std::forward_list::allocator_type
- std::forward_list::const_iterator
- std::forward_list::const_pointer
- std::forward_list::const_reference
- std::forward_list::difference_type
- std::forward_list::iterator
- std::forward_list::pointer
- std::forward_list::reference
- std::forward_list::size_type
- std::forward_list::value_type
- std::forward_list::assign
- std::forward_list::before_begin
- std::forward_list::begin
- std::forward_list::cbefore_begin
- std::forward_list::cbegin
- std::forward_list::cend
- std::forward_list::clear
- std::forward_list::emplace_after
- std::forward_list::emplace_front
- std::forward_list::empty
- std::forward_list::end
- std::forward_list::erase_after
- std::forward_list::front
- std::forward_list::get_allocator
- std::forward_list::insert_after
- std::forward_list::max_size
- std::forward_list::merge
- std::forward_list::pop_front
- std::forward_list::push_front
- std::forward_list::remove
- std::forward_list::remove_if
- std::forward_list::resize
- std::forward_list::reverse
- std::forward_list::sort
- std::forward_list::splice_after
- std::forward_list::swap
- std::forward_list::unique
ms.openlocfilehash: e13242aa41cc99cdd01a6f16b607ef568195d659
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890839"
---
# <a name="forward_list-class"></a>forward_list 类

描述用于控制变长元素序列的对象。 序列存储为节点的单向链接列表，其中每个节点都包含 `Type` 类型的成员。

## <a name="syntax"></a>语法

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>参数

类型 * \
要存储在 forward_list 中的元素数据类型。

*分配*器\
存储的分配器对象，用于封装有关 forward_list 的内存分配和解除分配的详细信息。 此参数可选。 默认值为分配器 <`Type`>。

## <a name="remarks"></a>备注

`forward_list` 对象通过基于[分配器类](../standard-library/allocator-class.md)*的存储*对象（通常称为 `std::allocator)`）为其控制的序列分配并释放存储。 有关详细信息，请参阅[分配器](../standard-library/allocators.md)。 分配器对象必须与 `allocator`类型的对象具有相同的外部接口。

> [!NOTE]
> 分配容器对象时，不会复制存储的分配器对象。

通过 `forward_list` 擦除迭代器、指针和引用所控制序列的元素时，这些迭代器、指针和引用可能失效。 通过 `forward_list` 对受控序列执行插入和接合操作不会使迭代器失效。

调用 [forward_list::insert_after](#insert_after)（它是可调用构造函数 `Type(const  T&)` 的唯一成员函数）时，可能会添加受控序列。 `forward_list` 也可能调用移动构造函数。 如果此类表达式引发异常，则容器对象不插入任何新元素，并重新引发该异常。 因此，当发生此类异常时，类型 `forward_list` 的对象将处于已知状态。

## <a name="members"></a>Members

### <a name="constructors"></a>构造函数

|||
|-|-|
|[forward_list](#forward_list)|构造 `forward_list` 类型的对象。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[allocator_type](#allocator_type)|一种类型，用于表示转发列表对象的分配器类。|
|[const_iterator](#const_iterator)|一种类型，用于为转发列表提供常量迭代器。|
|[const_pointer](#const_pointer)|一种类型，它提供指向转发列表中**const**元素的指针。|
|[const_reference](#const_reference)|一种类型，用于提供对转发列表中元素的常量引用。|
|[difference_type](#difference_type)|一种有符号整数类型，可用于表示转发列表中某个范围类迭代器所指向元素之间的元素数目。|
|[迭代器](#iterator)|一种类型，用于为转发列表提供迭代器。|
|[指针](#pointer)|一种类型，用于提供指向转发列表中元素的指针。|
|[reference](#reference)|一种类型，用于提供对转发列表中元素的引用。|
|[size_type](#size_type)|一种类型，用于表示两个元素之间的无符号距离。|
|[value_type](#value_type)|一种类型，用于表示转发列表中存储的元素的类型。|

### <a name="functions"></a>函数

|||
|-|-|
|[assign](#assign)|清除转发列表中的元素，并将一组新的元素复制到目标转发列表。|
|[before_begin](#before_begin)|返回寻址转发列表中第一个元素之前的位置的迭代器。|
|[begin](#begin)|返回寻址转发列表中第一个元素的迭代器。|
|[cbefore_begin](#cbefore_begin)|返回寻址转发列表中第一个元素之前的位置的常量迭代器。|
|[cbegin](#cbegin)|返回寻址转发列表中第一个元素的常量迭代器。|
|[cend](#cend)|返回寻址转发列表中最后一个元素之后的位置的常量迭代器。|
|[clear](#clear)|清除转发列表中的所有元素。|
|[emplace_after](#emplace_after)|在指定位置之后移动构造新元素。|
|[emplace_front](#emplace_front)|在列表的起始位置添加一个就地构造的元素。|
|[empty](#empty)|测试转发列表是否为空。|
|[end](#end)|返回寻址转发列表中最后一个元素之后的位置的迭代器。|
|[erase_after](#erase_after)|删除转发列表中指定位置之后的元素。|
|[front](#front)|返回对转发列表中第一个元素的引用。|
|[get_allocator](#get_allocator)|返回用于构造转发列表的分配器对象的一个副本。|
|[insert_after](#insert_after)|在转发列表中的指定位置之后添加元素。|
|[max_size](#max_size)|返回转发列表的最大长度。|
|[merge](#merge)|将元素从参数列表中删除，将它们插入目标转发列表，将新的组合元素集以升序或其他指定顺序排序。|
|[pop_front](#pop_front)|删除转发列表起始处的一个元素。|
|[push_front](#push_front)|在转发列表起始处添加一个元素。|
|[remove](#remove)|清除转发列表中与指定值匹配的元素。|
|[remove_if](#remove_if)|将满足指定谓词的元素从转发列表中清除。|
|[resize](#resize)|为转发列表指定新的大小。|
|[reverse](#reverse)|颠倒转发列表中元素的顺序。|
|[sort](#sort)|按升序或按谓词指定的顺序排列元素。|
|[splice_after](#splice_after)|重新联结节点间的链接。|
|[swap](#swap)|交换两个转发列表的元素。|
|[unique](#unique)|删除通过了指定测试的相邻元素。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator=](#op_eq)|将转发列表的元素替换为另一个转发列表的副本。|

## <a name="allocator_type"></a>allocator_type

一种类型，用于表示转发列表对象的分配器类。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>备注

`allocator_type` 是模板参数 Allocator 的同义词。

## <a name="assign"></a>将

清除转发列表中的元素，并将一组新的元素复制到目标转发列表。

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign(
    initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>参数

*第一个*\
替换范围的起始处。

*最后*\
替换范围的结束处。

*计数*\
要分配的元素数。

*val*\
要分配每个元素的值。

*类型*\
值的类型。

*IList*\
要复制的 initializer_list。

### <a name="remarks"></a>备注

如果 forward_list 是整数类型，则第一个成员函数的行为与 `assign((size_type)First, (Type)Last)` 相同。 否则，第一个成员函数将 `*this` 控制的序列替换为序列 [ `First, Last)`，该序列不能与初始控制序列重叠。

第二个成员函数将 `*this` 控制的序列替换为值 `Count` 的重复 `Val` 元素。

第三个成员函数将 initializer_list 的元素复制到 forward_list 中。

## <a name="before_begin"></a>before_begin

返回寻址转发列表中第一个元素之前的位置的迭代器。

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>返回值

恰好指向序列的第一个元素之前位置（或恰好在空序列末尾的位置之前）的正向迭代器。

### <a name="remarks"></a>备注

## <a name="begin"></a>准备

返回寻址转发列表中第一个元素的迭代器。

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>返回值

指向序列第一个元素（或刚超出空序列末尾的位置）的正向迭代器。

### <a name="remarks"></a>备注

## <a name="cbefore_begin"></a>cbefore_begin

返回寻址转发列表中第一个元素之前的位置的常量迭代器。

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>返回值

恰好指向序列的第一个元素之前位置（或恰好在空序列末尾的位置之前）的正向迭代器。

### <a name="remarks"></a>备注

## <a name="cbegin"></a>cbegin

返回一个**常量**迭代器，该迭代器用于寻址范围内的第一个元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

**常量**向前访问迭代器，指向范围的第一个元素，或刚超出空范围末尾（对于空范围，`cbegin() == cend()`）的位置。

### <a name="remarks"></a>备注

由于使用 `cbegin` 的返回值，因此不能修改范围中的元素。

可以使用此成员函数替代 `begin()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，请考虑 `Container` 为支持 `begin()` 和 `cbegin()`的任何类型的可修改（非常**量**）容器。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

返回一个**常量**迭代器，该迭代器用于寻址范围内最后一个元素之外的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

指向恰好超出范围末尾位置的向前访问迭代器。

### <a name="remarks"></a>备注

`cend` 用于测试迭代器是否超过了其范围的末尾。

可以使用此成员函数替代 `end()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，请考虑 `Container` 为支持 `end()` 和 `cend()`的任何类型的可修改（非常**量**）容器。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

不应对 `cend` 返回的值取消引用。

## <a name="clear"></a>清除

清除转发列表中的所有元素。

```cpp
void clear();
```

### <a name="remarks"></a>备注

此成员函数调用 `erase_after(before_begin(), end()).`

## <a name="const_iterator"></a>const_iterator

一种类型，用于为转发列表提供常量迭代器。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>备注

`const_iterator` 描述为可用作受控序列的常量向前迭代器的对象。 在此处描述为实现定义的类型的同义词。

## <a name="const_pointer"></a>const_pointer

一种类型，它提供指向转发列表中**const**元素的指针。

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>备注

## <a name="const_reference"></a>const_reference

一种类型，用于提供对转发列表中元素的常量引用。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>备注

## <a name="difference_type"></a>difference_type

一种有符号整数类型，可用于表示转发列表中某个范围类迭代器所指向元素之间的元素数目。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>备注

`difference_type` 描述一个对象，可以表示受控序列中任意两个元素的地址之间的差异。

## <a name="emplace_after"></a>emplace_after

在指定位置之后移动构造新元素。

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>参数

*Where*\
目标转发列表中构造新元素的位置。

*val*\
构造函数参数。

### <a name="return-value"></a>返回值

指定新插入元素的迭代器。

### <a name="remarks"></a>备注

此成员函数插入一个元素，其中包含构造函数参数*val* ，紧跟在受控序列中*位置*指向的元素之后。 否则，其行为与 [forward_list :: insert_after](#insert_after) 相同。

## <a name="emplace_front"></a>emplace_front

在列表的起始位置添加一个就地构造的元素。

```cpp
template <class Type>
    void emplace_front(Type&& val);
```

### <a name="parameters"></a>参数

*val*\
添加到转发列表开头的元素。

### <a name="remarks"></a>备注

此成员函数在受控序列末尾插入具有构造函数参数 `_ val` 的元素。

如果引发了异常，该容器将保持不变，并重新引发该异常。

## <a name="empty"></a>空白处

测试转发列表是否为空。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

如果转发列表为空，**则为 true** ;否则**为 false**。

## <a name="end"></a>端面

返回寻址转发列表中最后一个元素之后的位置的迭代器。

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>返回值

指向刚超出序列末尾位置的正向迭代器。

## <a name="erase_after"></a>erase_after

删除转发列表中指定位置之后的元素。

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>参数

*Where*\
目标转发列表中擦除元素的位置。

*第一个*\
要擦除范围的起始处。

*最后*\
要擦除范围的结尾处。

### <a name="return-value"></a>返回值

一个迭代器，它指定已删除的任何元素之外保留的第一个元素或 [forward_list::end](#end)（若此类元素不存在）。

### <a name="remarks"></a>备注

第一个成员函数删除受控序列*中*紧靠后的元素。

第二个成员函数将删除 `( first,  last)` 范围中受控序列的元素（不包括任一终点）。

擦除 `N` 元素会导致调用 `N` 析构函数。 发生[重新分配](../standard-library/forward-list-class.md)，因此迭代器和引用对已清除元素无效。

成员函数从不引发异常。

## <a name="forward_list"></a>forward_list

构造 `forward_list` 类型的对象。

```cpp
forward_list();
explicit forward_list(const Allocator& Al);
explicit forward_list(size_type Count);
forward_list(size_type Count, const Type& Val);
forward_list(size_type Count, const Type& Val, const Allocator& Al);
forward_list(const forward_list& Right);
forward_list(const forward_list& Right, const Allocator& Al);
forward_list(forward_list&& Right);
forward_list(forward_list&& Right, const Allocator& Al);
forward_list(initializer_list<Type> IList, const Alloc& Al);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>参数

*Al*\
要用于此对象的分配器类。

*计数*\
所构造列表中元素的数目。

*Val*\
构造的列表中的元素值。

*Right*\
所构造列表要作为其副本的列表。

*第一个*\
要复制的范围元素中的第一个元素的位置。

*最后*\
要复制的元素范围以外的第一个元素的位置。

*IList*\
要复制的 initializer_list。

### <a name="remarks"></a>备注

所有构造函数都存储[分配器](../standard-library/allocator-class.md)并初始化受控序列。 分配器对象*是参数（* 如果存在）。 对于复制构造函数，则为 ` right.get_allocator()`。 否则为 `Allocator()`。

前两个构造函数指定一个空的初始受控序列。

第三个构造函数指定 `Type()`值的*计数*元素的重复。

第四个和第五个构造函数指定值*Val*的*计数*元素的重复。

第六个构造函数指定由*Right*控制的序列副本。 如果 `InputIterator` 是整数类型，则接下来的两个构造函数指定 `(size_type)First` 元素的重复元素，元素的值为 `(Type)Last`。 否则，接下来两个构造函数指定序列 `[First, Last)`。

第九个和第十个构造函数与第六个构造函数相同，但它具有 [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 引用。

最后一个构造函数指定具有类 `initializer_list<Type>` 的对象的初始受控序列。

## <a name="front"></a>主

返回对转发列表中第一个元素的引用。

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>返回值

对受控序列的第一个元素的引用，必须为非空。

## <a name="get_allocator"></a>get_allocator

返回用于构造转发列表的分配器对象的一个副本。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

存储的 [allocator](../standard-library/allocator-class.md) 对象。

## <a name="insert_after"></a>insert_after

在转发列表中的指定位置之后添加元素。

```cpp
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>
    void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>参数

*Where*\
目标转发列表中插入第一个元素的位置。

*计数*\
要插入的元素数。

*第一个*\
插入范围的起始处。

*最后*\
插入范围的结束处。

*Val*\
添加到转发列表的元素。

*IList*\
要插入的 initializer_list。

### <a name="return-value"></a>返回值

一个迭代器，指定新插入的元素（仅限第一个和最后一个成员函数）。

### <a name="remarks"></a>备注

每个成员函数在由控制的序列中的*位置*指向的元素之后插入，这是由剩余操作数指定的序列。

第一个成员函数插入具有值*Val*的元素，并返回指定新插入的元素的迭代器。

第二个成员函数插入值*Val*的*计数*元素的重复。

如果 `InputIterator` 是整数类型，则第三个成员函数的行为与 `insert(it, (size_type)First, (Type)Last)` 相同。 否则，它插入序列 `[First, Last)`，该序列不能与初始受控序列重叠。

第四个成员函数插入由类 `initializer_list<Type>` 的对象指定的序列。

最后一个成员函数与第一个成员函数相同，但前者具有 [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 引用。

插入 `N` 元素会导致调用 `N` 构造函数。 发生[重新分配](../standard-library/forward-list-class.md)，但没有迭代器或引用变为无效。

如果在一个或多个元素插入过程中引发异常，则容器将保持不变并重新引发异常。

## <a name="iterator"></a>器

一种类型，用于为转发列表提供迭代器。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>备注

`iterator` 描述为可用作受控序列的前向迭代器的对象。 在此处描述为实现定义的类型的同义词。

## <a name="max_size"></a>max_size

返回转发列表的最大长度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>返回值

该对象可控制的最长序列的长度。

### <a name="remarks"></a>备注

## <a name="merge"></a>merge

将两个排序序列合并为一个以线性时间排序的序列。 将元素从参数列表中删除，并将它们插入此 `forward_list`。 调用 `merge` 之前，这两个列表应该按相同的比较函数对象排序。 合并的列表将按该比较函数对象进行排序。

```cpp
void merge(forward_list& right);
template <class Predicate>
    void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>参数

*right*\
要从其开始合并的转发列表。

*comp*\
用于对元素进行排序的比较函数对象。

### <a name="remarks"></a>备注

`forward_list::merge` 从 `forward_list` `right`中删除元素，并将其插入到此 `forward_list`中。 这两个序列必须由相同的谓词进行排序，如下所述。 合并的序列也可按该比较函数对象进行排序。

对于在 `Pi` 和 `Pj` 位置指定元素的迭代器 `i` 和 `j`，第一个成员函数每当 `!(*Pj < *Pi)` 时采用顺序 `i < j`。 （元素按 `ascending` 顺序排序。）当 `i < j`时，第二个成员函数将强制实施订单 `! comp(*Pj, *Pi)`。

原始受控序列中没有元素对在所生成的受控序列中反向。 如果所生成的受控序列中的一对元素经比较相等 (`!(*Pi < *Pj) && !(*Pj < *Pi)`)，则来自原始受控序列的元素在来自由 `right` 控制的序列的元素之前显示。

仅当 `comp` 引发异常时才会发生异常。 在这种情况下，受控序列以未指定的顺序保留，并重新引发异常。

## <a name="op_eq"></a>operator =

将转发列表的元素替换为另一个转发列表的副本。

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>参数

*right*\
要复制到转发列表的转发列表。

*IList*\
一个用括号括起来的初始化表达式列表，其行为类似于类型 `Type` 的元素的序列。

### <a name="remarks"></a>备注

第一个成员运算符将受控序列替换为由*right*控制的序列副本。

第二个成员操作符从类 `initializer_list<Type>` 的对象替换受控序列。

第三个成员运算符与第一个成员运算符相同，但前者具有 [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 引用。

## <a name="pointer"></a>变为

一种类型，用于提供指向转发列表中元素的指针。

```cpp
typedef typename Allocator::pointer pointer;
```

## <a name="pop_front"></a>pop_front

删除转发列表起始处的一个元素。

```cpp
void pop_front();
```

### <a name="remarks"></a>备注

转发列表的第一个元素必须为非空。

成员函数从不引发异常。

## <a name="push_front"></a>push_front

在转发列表起始处添加一个元素。

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>参数

*val*\
添加到转发列表开头的元素。

### <a name="remarks"></a>备注

如果引发了异常，该容器将保持不变，并重新引发该异常。

## <a name="reference"></a>对

一种类型，用于提供对转发列表中元素的引用。

```cpp
typedef typename Allocator::reference reference;
```

## <a name="remove"></a>取消

清除转发列表中与指定值匹配的元素。

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>参数

*val*\
一个值，如果某个元素包含该值，则会导致从列表中删除该元素。

### <a name="remarks"></a>备注

成员函数从受控序列删除由迭代器 `P` 指定的所有元素，其中 `*P ==  val`。

成员函数从不引发异常。

## <a name="remove_if"></a>remove_if

将满足指定谓词的元素从转发列表中清除。

```cpp
template <class Predicate>
    void remove_if(Predicate pred);
```

### <a name="parameters"></a>参数

*pred*\
一元谓词，如果元素满足该谓词，则该谓词会导致此元素从列表删除。

### <a name="remarks"></a>备注

成员函数从受控序列删除由迭代器 `P` 指定的所有元素，其中 ` pred(*P)` 为 true。

仅当*pred*引发异常时才会发生异常。 在这种情况下，受控序列以未指定的状态保留，并重新引发异常。

## <a name="resize"></a>调节

为转发列表指定新的大小。

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>参数

*_Newsize*\
调整大小后的转发列表中的元素数。

*val*\
要用于填充的值。

### <a name="remarks"></a>备注

成员函数同时确保列表之后中的元素数 *_Newsize*。 如果它必须使受控序列更长，则第一个成员函数将追加值为 `Type()`的元素，而第二个成员函数则追加值为*val*的元素。 若要使受控序列更短，两个成员函数可有效地调用 `erase_after(begin() + _Newsize - 1, end())`。

## <a name="reverse"></a>反向

颠倒转发列表中元素的顺序。

```cpp
void reverse();
```

## <a name="size_type"></a>size_type

一种类型，用于表示两个元素之间的无符号距离。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>备注

无符号的整数类型描述可表示任何受控序列长度的对象。

## <a name="sort"></a>进行

按升序或按谓词指定的顺序排列元素。

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>参数

*pred*\
排序谓词。

### <a name="remarks"></a>备注

两个成员函数通过谓词对受控序列中的元素排序，如下所述。

对于在 `Pi` 和 `Pj` 位置指定元素的迭代器 `i` 和 `j`，第一个成员函数每当 `!(*Pj < *Pi)` 时采用顺序 `i < j`。 （元素按 `ascending` 顺序排序。）`i < j`时，成员模板函数会施加订单 `! pred(*Pj, *Pi)`。 原始受控序列中没有排序的元素对在所生成的受控序列中反向。 （排序是稳定的。）

仅当*pred*引发异常时才会发生异常。 在这种情况下，受控序列以未指定的顺序保留，并重新引发异常。

## <a name="splice_after"></a>splice_after

从源 forward_list 中删除元素并将其插入到目标 forward_list 中。

```cpp
// insert the entire source forward_list
void splice_after(const_iterator Where, forward_list& Source);
void splice_after(const_iterator Where, forward_list&& Source);

// insert one element of the source forward_list
void splice_after(const_iterator Where, forward_list& Source, const_iterator Iter);
void splice_after(const_iterator Where, forward_list&& Source, const_iterator Iter);

// insert a range of elements from the source forward_list
void splice_after(
    const_iterator Where,
    forward_list& Source,
    const_iterator First,
    const_iterator Last);

void splice_after(
    const_iterator Where,
    forward_list&& Source,
    const_iterator First,
    const_iterator Last);
```

### <a name="parameters"></a>参数

*Where*\
目标 forward_list 中要在其后面进行插入的位置。

*源*\
要插入目标 forward_list 中的源 forward_list。

*Iter*\
要从源 forward_list 中进行插入的元素。

*第一个*\
要从源 forward_list 中进行插入的范围中的第一个元素。

*最后*\
要从源 forward_list 中进行插入的范围之外的第一个位置。

### <a name="remarks"></a>备注

第一对成员函数将由*源*控制的序列插入到由*Where*指向的受控序列中的元素之后。 它还将从*源*中删除所有元素。 （`&Source` 不得等于**此**。）

第二对成员函数删除由*源*控制的序列中的*Iter*之后的元素，并将其插入到由*Where*指向的受控序列中的元素之后。 （如果 `Where == Iter || Where == ++Iter`，则不会发生更改。）

第三对成员函数（范围接合）将由*源*控制的序列中的 `(First, Last)` 所指定的子范围插入到由*Where*控制的序列中的元素之后。 它还会删除由*源*控制的序列中的原始子范围。 （如果 `&Source == this`，范围 `(First, Last)` 一定不能包含*指向的元素。）*

如果范围接合插入 `N` 个元素和 `&Source != this`，则类 [iterator](#iterator) 的对象会递增 `N` 次。

任何迭代器、指针或指定接合的元素的引用都不会变得无效。

### <a name="example"></a>示例

```cpp
// forward_list_splice_after.cpp
// compile with: /EHsc /W4
#include <forward_list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    forward_list<int> c1{ 10, 11 };
    forward_list<int> c2{ 20, 21, 22 };
    forward_list<int> c3{ 30, 31 };
    forward_list<int> c4{ 40, 41, 42, 43 };

    forward_list<int>::iterator where_iter;
    forward_list<int>::iterator first_iter;
    forward_list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice_after(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice_after(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    c2.splice_after(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = (10) (11)c2 = (20) (21) (22)c3 = (30) (31)c4 = (40) (41) (42) (43)After splicing c1 into c2:c1 =c2 = (20) (21) (10) (11) (22)After splicing the first element of c3 into c2:c3 = (30)c2 = (20) (21) (31) (10) (11) (22)After splicing a range of c4 into c2:c4 = (40) (41)c2 = (20) (21) (42) (43) (31) (10) (11) (22)
```

## <a name="swap"></a>购

交换两个转发列表的元素。

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>参数

*right*\
提供要交换的元素的转发列表。

### <a name="remarks"></a>备注

成员函数在 `*this` 和*右*之间交换受控序列。 如果 `get_allocator() ==  right.get_allocator()`，它在固定时间内执行此操作，它不引发任何异常，不使任何引用、指针或指定两个受控序列中的元素的迭代器失效。 否则，它所执行的元素分配和构造函数调用数量会与两个受控序列中的元素数量成正比。

## <a name="unique"></a>针对

删除来自每个连续的相等元素组的第一个元素之外的所有元素。

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>参数

*comp*\
用于比较连续元素的二元谓词。

### <a name="remarks"></a>备注

保留每个唯一元素的第一个元素，并删除其余元素。 元素必须进行排序，以使具有相等值的元素在列表中相邻。

第一个成员函数从受控序列删除经比较等于其前一个元素的每个元素。 对于在 `Pi` 和 `Pj` 位置指定元素的迭代器 `i` 和 `j`，第二个成员函数删除其中 `i + 1 == j &&  comp(*Pi, *Pj)` 的每个元素。

对于长度为 `N` (> 0) 的受控序列，计算谓词 ` comp(*Pi, *Pj)``N - 1` 次。

仅当 `comp` 引发异常时才会发生异常。 在这种情况下，受控序列以未指定的状态保留，并重新引发异常。

## <a name="value_type"></a>value_type

一种类型，用于表示转发列表中存储的元素的类型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 `Type`的同义词。
