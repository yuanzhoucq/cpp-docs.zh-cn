---
title: Platform::Collections::InputIterator 类
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 92f9b15f474a5aa3d063f0ccfb663f56baf8de31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354567"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator 类

为从 Windows 运行时派生的集合提供标准模板库输入迭代器。

## <a name="syntax"></a>语法

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>参数

*Ⅹ*<br/>
InputIterator 模板类的类型名称。

### <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`difference_type`|指针差异 (ptrdiff_t)。|
|`iterator_category`|输入迭代器 (::std::input_iterator_tag) 的类别。|
|`pointer`|指向 `const X`|
|`reference`|对 `const X` 的引用|
|`value_type`|`X` 类型名称。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[输入迭代器：：输入迭代器](#ctor)|初始化 InputIterator 类的新实例。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[输入迭代器：：操作员！= 操作员](#operator-inequality)|指示当前 InputIterator 是否不等于指定的 InputIterator。|
|[InputIterator::operator* 运算符](#operator-dereference)|检索对当前 InputIterator 指定的元素的引用。|
|[输入迭代器：：运算符* 运算符](#operator-increment)|递增当前 InputIterator。|
|[输入迭代器：：运算符 = 运算符](#operator-equality)|指示当前 InputIterator 是否等于指定的 InputIterator。|
|[输入迭代器：：操作员->运算符](#operator-arrow)|检索当前 InputIterator 引用的元素的地址。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`InputIterator`

### <a name="requirements"></a>要求

**标题：** 集合.h

**命名空间：** Platform::Collections

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>输入迭代器：：输入迭代器构造函数

初始化 InputIterator 类的新实例。

### <a name="syntax"></a>语法

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>参数

*迭 代*<br/>
迭代器对象。

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>输入迭代器：：操作员-&gt;操作员

检索当前 InputIterator 指定的元素的地址。

### <a name="syntax"></a>语法

```
pointer operator->() const;
```

### <a name="return-value"></a>返回值

当前 InputIterator 指定的元素的地址。

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>输入迭代器：：操作员\*

检索对当前 InputIterator 指定的元素的引用。

### <a name="syntax"></a>语法

```
reference operator*() const;
```

### <a name="return-value"></a>返回值

当前 InputIterator 指定的元素。

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>输入迭代器：：运算符 = 运算符

指示当前 InputIterator 是否等于指定的 InputIterator。

### <a name="syntax"></a>语法

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一个 InputIterator。

### <a name="return-value"></a>返回值

如果当前输入迭代器等于*其他*输入迭代器，**则为 true;** 否则，**假**。

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>输入迭代器：：运算符* 运算符

递增当前 InputIterator。

### <a name="syntax"></a>语法

```
InputIterator& operator++();
InputIterator operator++(int);
```

### <a name="return-value"></a>返回值

第一个语法先递增然后返回当前 InputIterator。 第二个语法先返回当前 InputIterator 的副本然后递增当前 InputIterator。

### <a name="remarks"></a>备注

第一个 InputIterator 预先递增当前 InputIterator。

第二个语法后递增当前 InputIterator。 第二个语法中的 `int` 类型指示后递增操作，而不是实际整数操作数。

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>输入迭代器：：操作员！= 操作员

指示当前 InputIterator 是否不等于指定的 InputIterator。

### <a name="syntax"></a>语法

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一个 InputIterator。

### <a name="return-value"></a>返回值

如果当前输入迭代器不等于*其他*输入迭代器，**则为 true;** 否则，**假**。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)
