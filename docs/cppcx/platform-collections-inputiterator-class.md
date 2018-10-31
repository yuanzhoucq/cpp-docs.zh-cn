---
title: Platform::Collections::InputIterator 类 |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
dev_langs:
- C++
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0aa56c511ac5f7b98ffdd75aebd7f71ef9f21ac
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162017"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator 类

派生自 Windows 运行时的集合提供标准模板库 InputIterator。

## <a name="syntax"></a>语法

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>参数

*X*<br/>
InputIterator 模板类的类型名称。

### <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`difference_type`|指针差异 (ptrdiff_t)。|
|`iterator_category`|输入迭代器 (::std::input_iterator_tag) 的类别。|
|`pointer`|指向 `const X`|
|`reference`|对 `const X`|
|`value_type`|`X` 类型名称。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[InputIterator::InputIterator](#ctor)|初始化 InputIterator 类的新实例。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[InputIterator::operator!= 运算符](#operator-inequality)|指示当前 InputIterator 是否不等于指定的 InputIterator。|
|[InputIterator::operator* 运算符](#operator-decrement)|检索对当前 InputIterator 指定的元素的引用。|
|[InputIterator::operator++ 运算符](#operator-increment)|递增当前 InputIterator。|
|[InputIterator::operator== 运算符](#operator-equality)|指示当前 InputIterator 是否等于指定的 InputIterator。|
|[InputIterator::operator-> 运算符](#operator-arrow)|检索当前 InputIterator 引用的元素的地址。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`InputIterator`

### <a name="requirements"></a>要求

**标头：** collection.h

**命名空间：** Platform::Collections

## <a name="ctor"></a>  Inputiterator:: Inputiterator 构造函数

初始化 InputIterator 类的新实例。

### <a name="syntax"></a>语法

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iter);
```

### <a name="parameters"></a>参数

*Iter*<br/>
迭代器对象。

## <a name="operator-arrow"></a>  Inputiterator:: Operator-&gt;运算符

检索当前 InputIterator 指定的元素的地址。

### <a name="syntax"></a>语法

```
pointer operator->() const;
```

### <a name="return-value"></a>返回值

当前 InputIterator 指定的元素的地址。

## <a name="operator-dereference"></a>  Inputiterator:: Operator\*运算符

检索对当前 InputIterator 指定的元素的引用。

### <a name="syntax"></a>语法

```
reference operator*() const;
```

### <a name="return-value"></a>返回值

当前 InputIterator 指定的元素。

## <a name="operator-equality"></a>  Inputiterator:: Operator = = 运算符

指示当前 InputIterator 是否等于指定的 InputIterator。

### <a name="syntax"></a>语法

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>参数

*other*<br/>
另一个 InputIterator。

### <a name="return-value"></a>返回值

**true**当前 InputIterator 是否等于*其他*; 否则为**false**。

## <a name="operator-increment"></a>  Inputiterator:: Operator + + 运算符

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

## <a name="operator-inequality"></a>  Inputiterator:: Operator ！ = 运算符

指示当前 InputIterator 是否不等于指定的 InputIterator。

### <a name="syntax"></a>语法

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>参数

*other*<br/>
另一个 InputIterator。

### <a name="return-value"></a>返回值

**true**当前 InputIterator 是否不相等*其他*; 否则为**false**。

## <a name="see-also"></a>请参阅

[平台 Namespace](platform-namespace-c-cx.md)