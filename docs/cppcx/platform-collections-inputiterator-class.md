---
title: Platform::Collections::InputIterator 类
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 4aeef07a34c04bd1ab47acf808026024faada567
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218424"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator 类

为派生自 Windows 运行时的集合提供标准模板库 InputIterator。

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
|`reference`|对 `const X` 的引用|
|`value_type`|`X` 类型名称。|

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[InputIterator：： InputIterator](#ctor)|初始化 InputIterator 类的新实例。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[InputIterator：： operator！ = 运算符](#operator-inequality)|指示当前 InputIterator 是否不等于指定的 InputIterator。|
|[InputIterator::operator* 运算符](#operator-dereference)|检索对当前 InputIterator 指定的元素的引用。|
|[InputIterator：： operator + + 运算符](#operator-increment)|递增当前 InputIterator。|
|[InputIterator：： operator = = 运算符](#operator-equality)|指示当前 InputIterator 是否等于指定的 InputIterator。|
|[InputIterator：： operator-> 运算符](#operator-arrow)|检索当前 InputIterator 引用的元素的地址。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`InputIterator`

### <a name="requirements"></a>要求

**标头：** 集合。h

**命名空间：** Platform::Collections

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>InputIterator：： InputIterator 构造函数

初始化 InputIterator 类的新实例。

### <a name="syntax"></a>语法

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>参数

*器*<br/>
迭代器对象。

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>InputIterator：： operator- &gt; 运算符

检索当前 InputIterator 指定的元素的地址。

### <a name="syntax"></a>语法

```
pointer operator->() const;
```

### <a name="return-value"></a>返回值

当前 InputIterator 指定的元素的地址。

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>InputIterator：： operator \* 运算符

检索对当前 InputIterator 指定的元素的引用。

### <a name="syntax"></a>语法

```
reference operator*() const;
```

### <a name="return-value"></a>返回值

当前 InputIterator 指定的元素。

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>InputIterator：： operator = = 运算符

指示当前 InputIterator 是否等于指定的 InputIterator。

### <a name="syntax"></a>语法

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>参数

*以外*<br/>
另一个 InputIterator。

### <a name="return-value"></a>返回值

**`true`** 如果当前 InputIterator 等于*其他*值，则为; 否则为。否则为 **`false`** 。

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>InputIterator：： operator + + 运算符

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

第二个语法后递增当前 InputIterator。 **`int`** 第二个语法中的类型指示递增后操作，而不是实际整数操作数。

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>InputIterator：： operator！ = 运算符

指示当前 InputIterator 是否不等于指定的 InputIterator。

### <a name="syntax"></a>语法

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>参数

*以外*<br/>
另一个 InputIterator。

### <a name="return-value"></a>返回值

**`true`** 如果当前 InputIterator 不等于*其他*值，则为; 否则为。否则为 **`false`** 。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)
