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
ms.openlocfilehash: b2d08461b4ab57ed8479549c18c35c872d0eb9f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354375"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector 类

表示可按照索引单独访问的对象的有序集合。 实现[Windows：基础：集合：：I 可观察Vector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_)以帮助进行 XAML[数据绑定](/windows/uwp/data-binding/data-binding-in-depth)。

## <a name="syntax"></a>语法

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>参数

*T*<br/>
向量对象中包含的元素的类型。

*E*<br/>
指定二进制谓词，用于使用*类型 T*的值测试相等性。默认值为`std::equal_to<T>`。

### <a name="remarks"></a>备注

允许的类型是：

1. 整数

1. 接口类*

1. 公共 ref 类

1. value struct

1. 公共枚举类

**Vector**类是[Windows：：基础：集合：：iVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)接口C++具体实现。

如果尝试在公共返回值或参数中使用**Vector**类型，则引发编译器错误 C3986。 通过将参数或返回值的类型更改为 [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)可修复该错误。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[矢量：矢量](#ctor)|初始化 Vector 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Vector::Append](#append)|在当前向量中的最后一项后插入指定项。|
|[矢量：清除](#clear)|删除当前向量中的所有元素。|
|[矢量：第一](#first)|返回指定该向量中第一个元素的迭代器。|
|[矢量：getAt](#getat)|检索由指定索引标识的当前向量的元素。|
|[矢量：获取许多](#getmany)|从指定索引处开始，检索当前向量中的项目序列。|
|[矢量：获取视图](#getview)|返回向量的只读视图，即 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)。|
|[矢量：索引](#indexof)|在当前向量中搜索指定项，如果找到，则返回该项的索引。|
|[Vector::InsertAt](#insertat)|在指定索引标识的元素处将指定项插入到当前矢量中。|
|[Vector::ReplaceAll](#replaceall)|删除当前向量中的元素，然后插入来自指定数组的元素。|
|[Vector::RemoveAt](#removeat)|从当前向量删除指定索引标识的元素。|
|[Vector::RemoveAtEnd](#removeatend)|删除当前矢量末尾的元素。|
|[Vector::SetAt](#setat)|将指定值分配给当前向量中指定索引标识的元素。|
|[矢量：大小](#size)|返回当前向量对象中的元素数目。|

### <a name="events"></a>事件

|||
|-|-|
|名称|说明|
|事件[窗口：：基础：集合：：：矢量更改事件\<处理程序 T>= 矢量更改](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|当向量更改时发生。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Vector`

### <a name="requirements"></a>要求

**标题：** 集合.h

**命名空间：** Platform::Collections

## <a name="vectorappend-method"></a><a name="append"></a>矢量：：追加方法

在当前向量中的最后一项后插入指定项。

### <a name="syntax"></a>语法

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>参数

*index*<br/>
要插入到向量中的项。 *项*的类型由*T*类型名称定义。

## <a name="vectorclear-method"></a><a name="clear"></a>矢量：清除方法

删除当前向量中的所有元素。

### <a name="syntax"></a>语法

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a>矢量：第一种方法

返回指向该向量中第一个元素的迭代器。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>返回值

指向该向量中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存 First（） 返回的迭代器的一个方便方法是将返回值分配给使用**自动**类型扣减关键字声明的变量。 例如，`auto x = myVector->First();` 。 此迭代器知道该集合的长度。

When you need a pair of iterators to pass to an STL function, use the free functions [Windows::Foundation::Collections::begin](../cppcx/begin-function.md) and [Windows::Foundation::Collections::end](../cppcx/end-function.md)

## <a name="vectorgetat-method"></a><a name="getat"></a>矢量：GetAt 方法

检索由指定索引标识的当前向量的元素。

### <a name="syntax"></a>语法

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

### <a name="return-value"></a>返回值

*索引*参数指定的元素。 元素类型由*T*类型名称定义。

## <a name="vectorgetmany-method"></a><a name="getmany"></a>矢量：获取多种方法

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

dest**<br/>
调用方分配的项数组，从*startIndex*指定的元素开始，到 Vector 中的最后一个元素结束。

### <a name="return-value"></a>返回值

已检索的项的数量。

### <a name="remarks"></a>备注

此函数并非旨在由客户端代码直接使用。 它在[to_vector函数](../cppcx/to-vector-function.md)中内部使用，以便有效地转换平台：：矢量内量到 std：：vector 实例。

## <a name="vectorgetview-method"></a><a name="getview"></a>矢量：获取视图方法

返回向量的只读视图，即 IVectorView。

### <a name="syntax"></a>语法

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>返回值

一个 IVectorView 对象。

## <a name="vectorindexof-method"></a><a name="indexof"></a>矢量：方法索引

在当前向量中搜索指定项，如果找到，则返回该项的索引。

### <a name="syntax"></a>语法

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>参数

*value*<br/>
要查找的项。

*index*<br/>
如果找到参数*值*，则项的零基索引;否则，0。

如果项是 Vector 的第一个元素，或者未找到该项，*则索引*参数为 0。 如果返回值为**true，** 则找到项，它是第一个元素;否则，未找到该项目。

### <a name="return-value"></a>返回值

如果找到指定的项，为 true;如果找到指定的项，则**为 true。** 否则，**假**。

### <a name="remarks"></a>备注

IndexOf 使用 std::find_if 查找该项目。 因此，自定义元素类型应该重载 == 和 != 运算符以支持 find_if 所需的相等性比较。

## <a name="vectorinsertat-method"></a><a name="insertat"></a>矢量：插入方法

在指定索引标识的元素处将指定项插入到当前矢量中。

### <a name="syntax"></a>语法

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

*item*<br/>
要在*索引*指定的元素处插入到矢量中的项。 *项*的类型由*T*类型名称定义。

## <a name="vectorremoveat-method"></a><a name="removeat"></a>矢量：删除方法

从当前向量删除指定索引标识的元素。

### <a name="syntax"></a>语法

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a>矢量：：删除 Atend 方法

删除当前矢量末尾的元素。

### <a name="syntax"></a>语法

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a>矢量：：替换所有方法

删除当前向量中的元素，然后插入来自指定数组的元素。

### <a name="syntax"></a>语法

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>参数

*阿尔尔*<br/>
其类型由*T*类型名称定义的对象的数组。

## <a name="vectorsetat-method"></a><a name="setat"></a>矢量：setat 方法

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

## <a name="vectorsize-method"></a><a name="size"></a>矢量：大小方法

返回当前向量对象中的元素数目。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

当前 Vector 中的元素数目。

## <a name="vectorvector-constructor"></a><a name="ctor"></a>矢量：矢量构造函数

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
用于初始化矢量的[std：：数组](../standard-library/array-class-stl.md)。

*阿尔尔*<br/>
[平台：](../cppcx/platform-array-class.md)将用于初始化矢量的数组。

*Init*<br/>
用于初始化当前向量的对象集合的类型。

*I l*<br/>
用于初始化矢量的*T*型对象的[std：：initializer_list。](../standard-library/initializer-list-class.md)

*N*<br/>
用于初始化当前向量的对象集合中的元素数。

*大小*<br/>
向量中元素的数目。

*value*<br/>
用于初始化当前向量中每个元素的值。

*v*<br/>
用于初始化当前矢量的 l[值和 r 值](../cpp/lvalues-and-rvalues-visual-cpp.md)到[std：：矢量](../standard-library/vector-class.md)。

*Ptr*<br/>
指向用于初始化当前向量的 `std::vector` 的指针。

*第一*<br/>
用于初始化当前向量的对象序列中的第一个元素。 *第一*种是通过*完美的转发*传递的。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*最后*<br/>
用于初始化当前向量的对象序列中的最后一个元素。 *最后*一种是通过*完美的转发*传递的。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另请参阅

[集合 (C++/CX)](collections-c-cx.md)<br/>
[平台命名空间](platform-namespace-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
