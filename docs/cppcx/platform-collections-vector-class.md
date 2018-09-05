---
title: 类 |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aeaed487db1063efd14dddbca28480a169b13522
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761106"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector 类

表示可按照索引单独访问的对象的有序集合。

## <a name="syntax"></a>语法

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>参数

*T*  
向量对象中包含的元素的类型。

*E*  
指定测试相等性类型的值的二进制谓词*T*。默认值为 `std::equal_to<T>`。

### <a name="remarks"></a>备注

允许的类型包括：

1. 整数

1. 接口类 ^

1. 公共 ref 类

1. value struct

1. 公共枚举类

**向量**类是 c + + 具体实现[Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)接口。

如果尝试使用**向量**在公共返回值或参数，编译器将引发的错误 C3986 中的类型。 可以修复此错误，通过更改参数或返回值类型设置为[Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[Vector::Vector](#ctor)|初始化 Vector 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Vector::Append](#append)|在当前向量中的最后一项后插入指定项。|
|[Vector::Clear](#clear)|删除当前向量中的所有元素。|
|[Vector::First](#first)|返回指定该向量中第一个元素的迭代器。|
|[Vector::GetAt](#getat)|检索由指定索引标识的当前向量的元素。|
|[Vector::GetMany](#getmany)|从指定索引处开始，检索当前向量中的项目序列。|
|[Vector::GetView](#getview)|返回向量的只读视图，即 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)。|
|[Vector::IndexOf](#indexof)|在当前向量中搜索指定项，如果找到，则返回该项的索引。|
|[Vector::InsertAt](#insertat)|在当前 Vector 中由指定的索引标识的元素后面插入指定的项。|
|[Vector::ReplaceAll](#replaceall)|删除当前向量中的元素，然后插入来自指定数组的元素。|
|[Vector::RemoveAt](#removeat)|从当前向量删除指定索引标识的元素。|
|[Vector::RemoveAtEnd](#removeatend)|删除当前矢量末尾的元素。|
|[Vector::SetAt](#setat)|将指定值分配给当前向量中指定索引标识的元素。|
|[Vector::Size](#size)|返回当前向量对象中的元素数目。|

### <a name="events"></a>事件

|||
|-|-|
|name|描述|
|事件[Windows::Foundation::Collection::VectorChangedEventHandler\<T > ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|当向量更改时发生。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Vector`

### <a name="requirements"></a>要求

**标头：** collection.h

**命名空间：** Platform::Collections

## <a name="append"></a>  Vector:: append 方法

在当前向量中的最后一项后插入指定项。

### <a name="syntax"></a>语法

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>参数

*index*  
要插入到向量中的项。 类型*项*由定义*T*类型名称。

## <a name="clear"></a>  Vector:: clear 方法

删除当前向量中的所有元素。

### <a name="syntax"></a>语法

```cpp
virtual void Clear();
```

## <a name="first"></a>  Vector:: first 方法

返回指向该向量中第一个元素的迭代器。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>返回值

指向该向量中第一个元素的迭代器。

### <a name="remarks"></a>备注

保留 first （） 返回的迭代器的简便方法是将返回值分配为使用声明的变量**自动**类型推导关键字。 例如 `auto x = myVector->First();`。 此迭代器知道该集合的长度。

当您需要一对迭代器将传递到 STL 函数时，使用免费的函数[Windows::Foundation::Collections:: begin](../cppcx/begin-function.md)和[格式](../cppcx/end-function.md)

## <a name="getat"></a>  Vector:: getat 方法

检索由指定索引标识的当前向量的元素。

### <a name="syntax"></a>语法

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>参数

*index*  
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

### <a name="return-value"></a>返回值

指定的元素*索引*参数。 通过定义元素类型*T*类型名称。

## <a name="getmany"></a>  Vector:: getmany 方法

检索当前向量中的项序列，从指定的索引开始，并将它们复制到调用方分配的数组中。

### <a name="syntax"></a>语法

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>参数

*startIndex*  
要检索的项开头从零开始的索引。

*dest*  
在指定的元素处开始的项的调用方分配的数组*startIndex*向量中最后一个元素结尾。

### <a name="return-value"></a>返回值

已检索的项的数量。

### <a name="remarks"></a>备注

此函数并非旨在由客户端代码直接使用。 在内部在使用它[to_vector 函数](../cppcx/to-vector-function.md)若要启用的 platform 到 std:: vector 实例的高效转换。

## <a name="getview"></a>  Vector:: getview 方法

返回向量的只读视图，即 IVectorView。

### <a name="syntax"></a>语法

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>返回值

一个 IVectorView 对象。

## <a name="indexof"></a>  Vector:: indexof 方法

在当前向量中搜索指定项，如果找到，则返回该项的索引。

### <a name="syntax"></a>语法

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>参数

*value*  
要查找的项。

*index*  
项的从零开始的索引如果参数*值*找到; 否则为 0。

*索引*参数为 0，如果项目是 Vector 的第一个元素，或者找不到该项。 如果返回值为 `true`，则表明找到该项目，并且它是第一个元素；否则，表示未找到该项目。

### <a name="return-value"></a>返回值

如果找到指定项目，则为 `true`；否则，为 `false`。

### <a name="remarks"></a>备注

IndexOf 使用 std::find_if 查找该项目。 因此，自定义元素类型应该重载 == 和 != 运算符以支持 find_if 所需的相等性比较。

##  <a name="insertat"></a>  Vector:: insertat 方法

在当前 Vector 中由指定的索引标识的元素后面插入指定的项。

### <a name="syntax"></a>语法

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>参数

*index*  
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

*项*  
项后指定的元素插入到向量*索引*。 类型*项*由定义*T*类型名称。

## <a name="removeat"></a>  Vector:: removeat 方法

从当前向量删除指定索引标识的元素。

### <a name="syntax"></a>语法

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>参数

*index*  
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

## <a name="removeatend"></a>  Vector:: removeatend 方法

删除当前矢量末尾的元素。

### <a name="syntax"></a>语法

```cpp
virtual void RemoveAtEnd();
```

## <a name="replaceall"></a>  Vector:: replaceall 方法

删除当前向量中的元素，然后插入来自指定数组的元素。

### <a name="syntax"></a>语法

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>参数

*arr*  
其类型定义的对象的数组*T*类型名称。

## <a name="setat"></a>  Vector:: setat 方法

将指定值分配给当前向量中指定索引标识的元素。

### <a name="syntax"></a>语法

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>参数

*index*  
从零开始的无符号整数，用于指定 Vector 对象中的特定元素。

*项*  
要分配给指定元素的值。 类型*项*由定义*T*类型名称。

## <a name="size"></a>  Vector:: size 方法

返回当前向量对象中的元素数目。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

当前 Vector 中的元素数目。

## <a name="ctor"></a>  Vector:: vector 构造函数

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

*a*  
一个[std:: array](../standard-library/array-class-stl.md)将用于初始化此矢量。

*arr*  
一个[platform:: array](../cppcx/platform-array-class.md)将用于初始化此矢量。

*InIt*  
用于初始化当前向量的对象集合的类型。

*il*  
一个[std:: initializer_list](../standard-library/initializer-list-class.md)类型的对象的*T*将用于初始化此矢量。

*N*  
用于初始化当前向量的对象集合中的元素数。

*size*  
向量中元素的数目。

*value*  
用于初始化当前向量中每个元素的值。

*v*  
[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)到[std:: vector](../standard-library/vector-class.md)用于初始化当前向量。

*ptr*  
指向用于初始化当前向量的 `std::vector` 的指针。

*first*  
用于初始化当前向量的对象序列中的第一个元素。 类型*第一个*通过传递*完美转发*。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*最后一个*  
用于初始化当前向量的对象序列中的最后一个元素。 类型*上次*通过传递*完美转发*。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>请参阅

[平台 Namespace](platform-namespace-c-cx.md)  
[C + + 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  