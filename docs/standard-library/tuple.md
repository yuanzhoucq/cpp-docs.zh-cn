---
title: '&lt;tuple&gt;'
ms.date: 11/04/2016
f1_keywords:
- <tuple>
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
ms.openlocfilehash: a391a77ea65a203a7eddde12046c5df89a77194a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447149"
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
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|`tuple`比较对象是否相等。|
|[operator!=](../standard-library/tuple-operators.md#op_neq)|比较对象`tuple` , 而不是。|
|[operator<](../standard-library/tuple-operators.md#op_lt)|`tuple`比较对象, 小于。|
|[operator<=](../standard-library/tuple-operators.md#op_lt_eq)|`tuple`比较对象, 小于或等于。|
|[operator>](../standard-library/tuple-operators.md#op_gt)|`tuple`比较对象, 大于。|
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|对象的`tuple`比较, 大于或等于。|

### <a name="functions"></a>函数

|||
|-|-|
|[apply](../standard-library/tuple-functions.md#apply)|使用元组调用函数。|
|[forward_as_tuple](../standard-library/tuple-functions.md#forward)|构造一个引用元组。|
|[get](../standard-library/tuple-functions.md#get)|从 `tuple` 对象获取一个元素。|
|[make_from_tuple](../standard-library/tuple-functions.md#make_from_tuple)|要生成的`tuple`速记。|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|从元素值中生成一个 `tuple`。|
|[swap](../standard-library/tuple-functions.md#swap)||
|[tie](../standard-library/tuple-functions.md#tie)|从元素引用中生成一个 `tuple`。|
|[tuple_cat](../standard-library/tuple-functions.md#tuple_cat)|使用一系列类型元素构造元组对象。|

## <a name="see-also"></a>请参阅

[\<array>](../standard-library/array.md)
