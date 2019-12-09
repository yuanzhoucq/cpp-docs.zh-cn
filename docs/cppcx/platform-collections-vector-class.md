---
title: Platform::Collections::Vector 类
ms.date: 12/04/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
ms.openlocfilehash: b7774c2cdab7b9abcb3ebac1453779055eacf897
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857887"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector 类

表示可按照索引单独访问的对象的有序集合。 实现[Windows：： Foundation：：集合：： IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_)以帮助 XAML[数据绑定](/windows/uwp/data-binding/data-binding-in-depth)。

## <a name="syntax"></a>语法

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>参数

*T*<br/>
向量对象中包含的元素的类型。

*E*<br/>
指定一个二元谓词，用于测试与类型*T*的值的相等性。默认值为 `std::equal_to<T>`。

### <a name="remarks"></a>备注

允许的类型包括：

1. 整数

1. 接口类 ^

1. 公共 ref 类^

1. 值结构

1. 公共枚举类

**Vector**类是C++ [Windows：： Foundation：：集合：： IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)接口的具体实现。

如果尝试在公共返回值或参数中使用**Vector**类型，则会引发编译器错误 C3986。 通过将参数或返回值的类型更改为 [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)可修复该错误。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[Vector::Vector](#ctor)|初始化 Vector 类的新实例。|

### <a name="public-methods"></a>公共方法

|Name|描述|
|----------|-----------------|
|[Vector::Append](#append)|在当前向量中的最后一项后插入指定项。|
|[Vector::Clear](#clear)|删除当前向量中的所有元素。|
|[Vector::First](#first)|返回指定该向量中第一个元素的迭代器。|
|[Vector::GetAt](#getat)|检索由指定索引标识的当前向量的元素。|
|[Vector::GetMany](#getmany)|从指定索引处开始，检索当前向量中的项目序列。|
|[Vector::GetView](#getview)|返回向量的只读视图，即 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)。|
|[Vector::IndexOf](#indexof)|在当前向量中搜索指定项，如果找到，则返回该项的索引。|
|[Vector::InsertAt](#insertat)|将指定的项插入到由指定索引标识的元素的当前向量中。|
|[Vector::ReplaceAll](#replaceall)|删除当前向量中的元素，然后插入来自指定数组的元素。|
|[Vector::RemoveAt](#removeat)|从当前向量删除指定索引标识的元素。|
|[Vector::RemoveAtEnd](#removeatend)|删除当前矢量末尾的元素。|
|[Vector::SetAt](#setat)|将指定值分配给当前向量中指定索引标识的元素。|
|[Vector::Size](#size)|返回当前向量对象中的元素数目。|

### <a name="events"></a>Events

|||
|-|-|
|Name|描述|
|事件[Windows：： Foundation：： Collection：： VectorChangedEventHandler\<t > ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|当向量更改时发生。|

## <a name="inheritance-hierarchy"></a>繼承階層

`Vector`

### <a name="requirements"></a>需求

**标头：** collection.h

**命名空间：** Platform::Collections

## <a name="append"></a>Vector：： Append 方法

在当前向量中的最后一项后插入指定项。

### <a name="syntax"></a>语法

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>参数

*index*<br/>
要插入到向量中的项。 *项*的类型由*T*类型名称定义。

## <a name="clear"></a>Vector：： Clear 方法

删除当前向量中的所有元素。

### <a name="syntax"></a>语法

```cpp
virtual void Clear();
```

## <a name="first"></a>Vector：： First 方法

返回指向该向量中第一个元素的迭代器。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>返回值

指向该向量中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存第一个（）返回的迭代器的一种简便方法是将返回值分配给用**auto**类型推导关键字声明的变量。 例如 `auto x = myVector->First();`。 此迭代器知道该集合的长度。

如果需要将一对迭代器传递到 STL 函数，请使用 free 函数[Windows：： foundation：：集合：： begin](../cppcx/begin-function.md)和[Windows：： Foundation：：集合：： end](../cppcx/end-function.md)

## <a name="getat"></a>Vector：： GetAt 方法

检索由指定索引标识的当前向量的元素。

### <a name="syntax"></a>语法

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

### <a name="return-value"></a>返回值

由*index*参数指定的元素。 元素类型由*T*类型名称定义。

## <a name="getmany"></a>Vector：： GetMany 方法

检索当前向量中的项序列，从指定的索引开始，并将它们复制到调用方分配的数组中。

### <a name="syntax"></a>语法

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>参数

*startIndex*<br/>
要检索的项开头从零开始的索引。

*dest*<br/>
调用方分配的项的数组，这些项以*startIndex*指定的元素开始，并在向量中的最后一个元素结束。

### <a name="return-value"></a>返回值

已检索的项的数量。

### <a name="remarks"></a>备注

此函数并非旨在由客户端代码直接使用。 它用于在[To_vector 函数](../cppcx/to-vector-function.md)内部使用，以启用 Platform：： vector 实例所在到 std：： vector 实例的有效转换。

## <a name="getview"></a>Vector：： GetView 方法

返回向量的只读视图，即 IVectorView。

### <a name="syntax"></a>语法

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>返回值

一个 IVectorView 对象。

## <a name="indexof"></a>Vector：： IndexOf 方法

在当前向量中搜索指定项，如果找到，则返回该项的索引。

### <a name="syntax"></a>语法

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>参数

*value*<br/>
要查找的项。

*index*<br/>
如果找到参数*值*，则为该项的从零开始的索引;否则为0。

如果项是向量的第一个元素或未找到该项，则*索引*参数为0。 如果返回值为**true**，则表示已找到该项并且它是第一个元素;否则，找不到该项。

### <a name="return-value"></a>返回值

如果找到指定的项，则为**true** ;否则**为 false**。

### <a name="remarks"></a>备注

IndexOf 使用 std::find_if 查找该项目。 因此，自定义元素类型应该重载 == 和 != 运算符以支持 find_if 所需的相等性比较。

##  <a name="insertat"></a>Vector：： InsertAt 方法

将指定的项插入到由指定索引标识的元素的当前向量中。

### <a name="syntax"></a>语法

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

*item*<br/>
要插入到 Vector 中由*index*指定的元素的项。 *项*的类型由*T*类型名称定义。

## <a name="removeat"></a>Vector：： RemoveAt 方法

从当前向量删除指定索引标识的元素。

### <a name="syntax"></a>语法

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

## <a name="removeatend"></a>Vector：： RemoveAtEnd 方法

删除当前矢量末尾的元素。

### <a name="syntax"></a>语法

```cpp
virtual void RemoveAtEnd();
```

## <a name="replaceall"></a>Vector：： ReplaceAll 方法

删除当前向量中的元素，然后插入来自指定数组的元素。

### <a name="syntax"></a>语法

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>参数

*arr*<br/>
对象的数组，其类型由*T*类型名称定义。

## <a name="setat"></a>Vector：： SetAt 方法

将指定值分配给当前向量中指定索引标识的元素。

### <a name="syntax"></a>语法

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

*item*<br/>
要分配给指定元素的值。 *项*的类型由*T*类型名称定义。

## <a name="size"></a>Vector：： Size 方法

返回当前向量对象中的元素数目。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

当前 Vector 中的元素数目。

## <a name="ctor"></a>Vector：： Vector 构造函数

初始化 Vector 类的新实例。

### <a name="syntax"></a>语法

```cpp
Vector();

explicit Vector(unsigned int size);
Vector( unsigned int size, T value);
template <typename U> explicit Vector( const ::std::vector<U>& v);
template <typename U> explicit Vector( std::vector<U>&& v);

Vector( const T * ptr, unsigned int size);
template <size_t N> explicit Vector(const T(&arr)[N]);
template <size_t N> explicit Vector(const std::array<T, N>& a);
explicit Vector(const Array<T>^ arr);

template <typename InIt> Vector(InIt first, InIt last);
Vector(std::initializer_list<T> il);
```

### <a name="parameters"></a>参数

*a*<br/>
将用于初始化向量的[std：： array](../standard-library/array-class-stl.md) 。

*arr*<br/>
将用于初始化向量的[Platform：： Array](../cppcx/platform-array-class.md) 。

*InIt*<br/>
用于初始化当前向量的对象集合的类型。

*il*<br/>
将用于初始化向量的类型为*T*的对象的[std：： initializer_list](../standard-library/initializer-list-class.md) 。

*N*<br/>
用于初始化当前向量的对象集合中的元素数。

*size*<br/>
向量中元素的数目。

*value*<br/>
用于初始化当前向量中每个元素的值。

*v*<br/>
[左值和右](../cpp/lvalues-and-rvalues-visual-cpp.md)到用于初始化当前向量的[std：： vector](../standard-library/vector-class.md) 。

*ptr*<br/>
指向用于初始化当前向量的 `std::vector` 的指针。

*first*<br/>
用于初始化当前向量的对象序列中的第一个元素。 *第一*种类型是通过*完美转发*传递的。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*last*<br/>
用于初始化当前向量的对象序列中的最后一个元素。 *最后一*种方法是通过*完美转发*传递的。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另请参阅

[集合 (C++/CX)](collections-c-cx.md)<br/>
[平台命名空间](platform-namespace-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
