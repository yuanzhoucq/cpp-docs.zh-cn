---
title: Platform::Collections::VectorView 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
ms.openlocfilehash: cecbd61ad8862d5046cab9e0b418d5c4d16829d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363807"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView 类

表示可按照索引单独访问的对象的顺序集合的只读视图。 集合中每个对象的类型由模板参数指定。

## <a name="syntax"></a>语法

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>参数

*T*<br/>
`VectorView` 对象中包含的元素的类型。

*E*<br/>
使用 `T`类型的值指定测试相等性的二进制谓词。 默认值为 `std::equal_to<T>`。

### <a name="remarks"></a>备注

该`VectorView`类实现[Windows：基础：：集合：：iVectorView\<T>](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)接口，并支持标准模板库迭代器。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[矢量视图：矢量视图](#ctor)|初始化 VectorView 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[矢量视图：第一](#first)|返回指定 VectorView 中的第一个元素的迭代器。|
|[矢量视图：获取](#getat)|检索由指定的索引表示的当前 VectorView 的元素。|
|[矢量视图：获取许多](#getmany)|从当前 VectorView 检索项序列，从指定索引处开始。|
|[矢量视图：索引](#indexof)|在当前 VectorView 中搜索指定项，如果找到，则返回该项的索引。|
|[VectorView::Size](#size)|返回当前 VectorView 对象中的元素数目。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`VectorView`

### <a name="requirements"></a>要求

**标题：** 集合.h

**命名空间：** Platform::Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a>矢量视图：第一种方法

返回指定 VectorView 中的第一个元素的迭代器。

### <a name="syntax"></a>语法

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>返回值

指定 VectorView 中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存 First（） 返回的迭代器的一个方便方法是将返回值分配给使用**自动**类型扣减关键字声明的变量。 例如，`auto x = myVectorView->First();` 。

## <a name="vectorviewgetat-method"></a><a name="getat"></a>矢量视图：GetAt 方法

检索由指定的索引表示的当前 VectorView 的元素。

### <a name="syntax"></a>语法

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的无符号整数，用于指定 VectorView 对象中的特定元素。

### <a name="return-value"></a>返回值

`index` 参数指定的元素。 元素类型由 VectorView 模板参数*T*指定。

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>矢量视图：获取许多方法

从当前 VectorView 检索项序列，从指定索引处开始。

### <a name="syntax"></a>语法

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>参数

*startIndex*<br/>
要检索的项开头从零开始的索引。

dest**<br/>
此操作完成时的项列表，以由 `startIndex` 指定的元素开始，以 VectorView 中最后一个元素结尾。

### <a name="return-value"></a>返回值

已检索的项的数量。

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>矢量视图：方法索引

在当前 VectorView 中搜索指定项，如果找到，则返回该项的索引。

### <a name="syntax"></a>语法

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>参数

*value*<br/>
要查找的项。

*index*<br/>
如果找到参数 `value`，则为该项的从零开始的索引；否则，为 0。

如果项是 的第一个元素`VectorView`，或者未找到项，*则索引*参数为 0。 如果返回值为**true，** 则找到项，它是第一个元素;否则，未找到该项目。

### <a name="return-value"></a>返回值

如果找到指定的项，为 true;如果找到指定的项，则**为 true。** 否则，**假**。

## <a name="vectorviewsize-method"></a><a name="size"></a>矢量视图：大小方法

返回当前 VectorView 对象中的元素数目。

### <a name="syntax"></a>语法

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

当前 VectorView 中的元素数目。

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>矢量视图：矢量视图构造函数

初始化 VectorView 类的新实例。

### <a name="syntax"></a>语法

```
VectorView();
explicit VectorView(
   UInt32 size
);
VectorView(
   UInt32 size,
   T value
);
explicit VectorView(
   const ::std::vector<T>& v
);
explicit VectorView(
   ::std::vector<T>&& v
);
VectorView(
   const T * ptr,
   UInt32 size
);

template <
   size_t N
>
explicit VectorView(
   const T (&arr)[N]
);

template <
   size_t N
>
explicit VectorView(
   const ::std::array<T,
   N>& a
);

explicit VectorView(
   const ::Platform::Array<T>^ arr
);

template <
   typename InIt
>
VectorView(
   InItfirst,
   InItlast
);

VectorView(
   std::initializer_list<T> il
);
```

### <a name="parameters"></a>参数

*Init*<br/>
用于初始化当前 VectorView 的对象集合的类型。

*I l*<br/>
[std：：initializer_list](../standard-library/initializer-list-class.md)其元素将用于初始化 VectorView。

*N*<br/>
用于初始化当前 VectorView 的对象集合中元素的数量。

*大小*<br/>
VectorView 中元素的数量。

*value*<br/>
用于初始化当前 VectorView 中每个元素的值。

*v*<br/>
用于初始化当前 VectorView 的 l[值和 R 值](../cpp/lvalues-and-rvalues-visual-cpp.md)到[std：：矢量](../standard-library/vector-class.md)。

*Ptr*<br/>
指向用于初始化当前 VectorView 的 `std::vector` 的指针。

*阿尔尔*<br/>
平台[：用于](../cppcx/platform-array-class.md)初始化当前 VectorView 的数组对象。

*a*<br/>
用于初始化当前 VectorView 的[std：：数组](../standard-library/array-class-stl.md)对象。

*第一*<br/>
用于初始化当前 VectorView 的对象序列中的第一个元素。 的类型`first`是通过*完美的转发*传递的。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*最后*<br/>
用于初始化当前 VectorView 的对象序列中的最后一个元素。 的类型`last`是通过*完美的转发*传递的。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
