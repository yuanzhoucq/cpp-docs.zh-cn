---
title: '&lt;tuple&gt;'
ms.date: 11/04/2016
f1_keywords:
- <tuple>
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
ms.openlocfilehash: ce6e005990d05676fb20752b5808d32ec88dd7b3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241540"
---
# <a name="lttuplegt"></a>&lt;tuple&gt;

定义了一个模板 `tuple`它的实例包括不同类型的对象。

## <a name="requirements"></a>要求

**标头：** \<tuple>

**命名空间：** std

## <a name="members"></a>成员

### <a name="classes-and-structs"></a>类和结构

|||
|-|-|
|[tuple 类](../standard-library/tuple-class.md)|包装元素的固定长度序列。|
|[tuple_element 类](../standard-library/tuple-element-class-tuple.md)|包装的 `tuple` 类型的元素。|
|[tuple_size 类](../standard-library/tuple-size-class-tuple.md)|包装 `tuple` 元素计数。|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||

### <a name="objects"></a>对象

|||
|-|-|
|[tuple_element_t](../standard-library/tuple-functions.md#tuple_element_t)||
|[tuple_size_v](../standard-library/tuple-functions.md#tuple_size_v)||

### <a name="operators"></a>运算符

|||
|-|-|
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|比较`tuple`对象是否相等。|
|[operator!=](../standard-library/tuple-operators.md#op_neq)|比较`tuple`对象是否不相等。|
|[operator<](../standard-library/tuple-operators.md#op_lt)|比较`tuple`对象，小于。|
|[operator<=](../standard-library/tuple-operators.md#op_lt_eq)|比较`tuple`对象，小于或等于。|
|[operator>](../standard-library/tuple-operators.md#op_gt)|比较`tuple`对象是否更大。|
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|比较`tuple`对象，大于或等于。|

### <a name="functions"></a>函数

|||
|-|-|
|[apply](../standard-library/tuple-functions.md#apply)|调用函数的元组。|
|[forward_as_tuple](../standard-library/tuple-functions.md#forward)|构造元组的引用。|
|[get](../standard-library/tuple-functions.md#get)|从 `tuple` 对象获取一个元素。|
|[make_from_tuple](../standard-library/tuple-functions.md#make_from_tuple)|简写形式，以使`tuple`。|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|从元素值中生成一个 `tuple`。|
|[swap](../standard-library/tuple-functions.md#swap)||
|[tie](../standard-library/tuple-functions.md#tie)|从元素引用中生成一个 `tuple`。|
|[tuple_cat](../standard-library/tuple-functions.md#tuple_cat)|构造具有一系列类型元素的元组对象。|

## <a name="see-also"></a>请参阅

[\<array>](../standard-library/array.md)<br/>
