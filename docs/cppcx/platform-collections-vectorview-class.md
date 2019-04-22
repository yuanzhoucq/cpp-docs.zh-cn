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
ms.openlocfilehash: 02b5e15a816ec057bfb0a8201b7591e628c3ea2c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745285"
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

`VectorView`类实现[Windows::Foundation::Collections::IVectorView\<T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)接口，并支持标准模板库迭代器。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[VectorView::VectorView](#ctor)|初始化 VectorView 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[VectorView::First](#first)|返回指定 VectorView 中的第一个元素的迭代器。|
|[VectorView::GetAt](#getat)|检索由指定的索引表示的当前 VectorView 的元素。|
|[VectorView::GetMany](#getmany)|从当前 VectorView 检索项序列，从指定索引处开始。|
|[VectorView::IndexOf](#indexof)|在当前 VectorView 中搜索指定项，如果找到，则返回该项的索引。|
|[VectorView::Size](#size)|返回当前 VectorView 对象中的元素数目。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`VectorView`

### <a name="requirements"></a>要求

**标头：** collection.h

**命名空间：** Platform::Collections

## <a name="first"></a>  Vectorview:: First 方法

返回指定 VectorView 中的第一个元素的迭代器。

### <a name="syntax"></a>语法

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>返回值

指定 VectorView 中第一个元素的迭代器。

### <a name="remarks"></a>备注

保留 first （） 返回的迭代器的简便方法是将返回值分配为使用声明的变量**自动**类型推导关键字。 例如 `auto x = myVectorView->First();`。

## <a name="getat"></a>  Vectorview:: Getat 方法

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


  `index` 参数指定的元素。 元素类型由 VectorView 模板参数指定 *T* 。

## <a name="getmany"></a>  Vectorview:: Getmany 方法

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

*dest*<br/>
此操作完成时的项列表，以由 `startIndex` 指定的元素开始，以 VectorView 中最后一个元素结尾。

### <a name="return-value"></a>返回值

已检索的项的数量。

## <a name="indexof"></a>  Vectorview:: Indexof 方法

在当前 VectorView 中搜索指定项，如果找到，则返回该项的索引。

### <a name="syntax"></a>语法

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>参数

*值*<br/>
要查找的项。

*index*<br/>
如果找到参数 `value`，则为该项的从零开始的索引；否则，为 0。

*索引*参数为 0，如果任一项的第一个元素`VectorView`或找不到该项。 如果返回值是 **，则返回 true**，找到该项目，它是第一个元素; 否则，未找到项。

### <a name="return-value"></a>返回值

**true**如果指定的项; 否则为**false**。

## <a name="size"></a>  Vectorview:: Size 方法

返回当前 VectorView 对象中的元素数目。

### <a name="syntax"></a>语法

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

当前 VectorView 中的元素数目。

## <a name="ctor"></a>  Vectorview:: Vectorview 构造函数

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

*InIt*<br/>
用于初始化当前 VectorView 的对象集合的类型。

*il*<br/>
一个[std:: initializer_list](../standard-library/initializer-list-class.md)其元素将用于初始化 VectorView。

*N*<br/>
用于初始化当前 VectorView 的对象集合中元素的数量。

*size*<br/>
VectorView 中元素的数量。

*值*<br/>
用于初始化当前 VectorView 中每个元素的值。

*v*<br/>
[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)到[std:: vector](../standard-library/vector-class.md)用于初始化当前 VectorView。

*ptr*<br/>
指向用于初始化当前 VectorView 的 `std::vector` 的指针。

*arr*<br/>
一个[platform:: array](../cppcx/platform-array-class.md)用于初始化当前 VectorView 的对象。

*a*<br/>
一个[std:: array](../standard-library/array-class-stl.md)用于初始化当前 VectorView 的对象。

*first*<br/>
用于初始化当前 VectorView 的对象序列中的第一个元素。 类型`first`通过传递*完美转发*。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*last*<br/>
用于初始化当前 VectorView 的对象序列中的最后一个元素。 类型`last`通过传递*完美转发*。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>请参阅

[平台 Namespace](platform-namespace-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
