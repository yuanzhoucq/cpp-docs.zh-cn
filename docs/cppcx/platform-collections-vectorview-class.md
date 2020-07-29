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
ms.openlocfilehash: 207f5d517eaae475af1c65a284a3d1ebe50621af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218385"
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

*电邮*<br/>
使用 `T`类型的值指定测试相等性的二进制谓词。 默认值为 `std::equal_to<T>`。

### <a name="remarks"></a>备注

`VectorView`类实现[Windows：： Foundation：：集合：： IVectorView \<T> ](/uwp/api/windows.foundation.collections.ivectorview-1)接口，并支持标准模板库迭代器。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[VectorView：： VectorView](#ctor)|初始化 VectorView 类的新实例。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[VectorView：： First](#first)|返回指定 VectorView 中的第一个元素的迭代器。|
|[VectorView：： GetAt](#getat)|检索由指定的索引表示的当前 VectorView 的元素。|
|[VectorView：： GetMany](#getmany)|从当前 VectorView 检索项序列，从指定索引处开始。|
|[VectorView：： IndexOf](#indexof)|在当前 VectorView 中搜索指定项，如果找到，则返回该项的索引。|
|[VectorView::Size](#size)|返回当前 VectorView 对象中的元素数目。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`VectorView`

### <a name="requirements"></a>要求

**标头：** 集合。h

**命名空间：** Platform::Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a>VectorView：： First 方法

返回指定 VectorView 中的第一个元素的迭代器。

### <a name="syntax"></a>语法

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>返回值

指定 VectorView 中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存第一个（）返回的迭代器的一种简便方法是将返回值分配给使用 **`auto`** 类型推导关键字声明的变量。 例如，`auto x = myVectorView->First();`。

## <a name="vectorviewgetat-method"></a><a name="getat"></a>VectorView：： GetAt 方法

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

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>VectorView：： GetMany 方法

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

*目的*<br/>
此操作完成时的项列表，以由 `startIndex` 指定的元素开始，以 VectorView 中最后一个元素结尾。

### <a name="return-value"></a>返回值

已检索的项的数量。

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>VectorView：： IndexOf 方法

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

如果*index*项是的第一个元素 `VectorView` 或未找到该项，则索引参数为0。 如果返回值为 **`true`** ，则发现该项并且它是第一个元素; 否则找不到该项。

### <a name="return-value"></a>返回值

**`true`** 如果找到指定的项，则为;否则为 **`false`** 。

## <a name="vectorviewsize-method"></a><a name="size"></a>VectorView：： Size 方法

返回当前 VectorView 对象中的元素数目。

### <a name="syntax"></a>语法

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

当前 VectorView 中的元素数目。

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>VectorView：： VectorView 构造函数

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
[Std：： initializer_list](../standard-library/initializer-list-class.md) ，其元素将用于初始化 VectorView。

N**<br/>
用于初始化当前 VectorView 的对象集合中元素的数量。

*大小*<br/>
VectorView 中元素的数量。

*value*<br/>
用于初始化当前 VectorView 中每个元素的值。

*向量*<br/>
用于初始化当前 VectorView 的[std：： vector](../standard-library/vector-class.md)的[左值和右](../cpp/lvalues-and-rvalues-visual-cpp.md)。

*ptr*<br/>
指向用于初始化当前 VectorView 的 `std::vector` 的指针。

*arr*<br/>
用于初始化当前 VectorView 的[Platform：： Array](../cppcx/platform-array-class.md)对象。

*的*<br/>
用于初始化当前 VectorView 的[std：： array](../standard-library/array-class-stl.md)对象。

*first*<br/>
用于初始化当前 VectorView 的对象序列中的第一个元素。 的类型 `first` 是通过*完美转发*传递的。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*last*<br/>
用于初始化当前 VectorView 的对象序列中的最后一个元素。 的类型 `last` 是通过*完美转发*传递的。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
