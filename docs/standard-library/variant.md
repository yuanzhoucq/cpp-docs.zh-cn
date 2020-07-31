---
title: '&lt;变量&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 6074c80b20ae0c69d34768bc16d7aaae16c99579
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232815"
---
# <a name="ltvariantgt"></a>&lt;变量&gt;

变量对象保存和管理值。 如果变量包含一个值，则该值的类型必须是赋予 variant 的模板参数类型之一。 这些模板参数称为替代项。

## <a name="requirements"></a>要求

**标头：**\<variant>

**命名空间:** std

## <a name="members"></a>成员

### <a name="operators"></a>运算符

|||
|-|-|
|[operator = =](../standard-library/forward-list-operators.md#op_eq_eq)|测试运算符左侧的变量对象是否等于右侧的变体对象。|
|[operator！ =](../standard-library/forward-list-operators.md#op_neq)|测试运算符左侧的变量对象是否不等于右侧的变体对象。|
|[运算符<](../standard-library/forward-list-operators.md#op_lt)|测试运算符左侧的变量对象是否小于右侧的变体对象。|
|[运算符<=](../standard-library/forward-list-operators.md#op_lt_eq)|测试运算符左侧的变量对象是否小于或等于右侧的变体对象的。|
|[运算符>](../standard-library/forward-list-operators.md#op_gt)|测试运算符左侧的变量对象是否大于右侧的变体对象。|
|[运算符>=](../standard-library/forward-list-operators.md#op_lt_eq)|测试运算符左侧的变量对象是否大于或等于右侧的变体对象的。|

### <a name="functions"></a>函数

|||
|-|-|
|[get](../standard-library/variant-functions.md#get)|获取对象的变体。|
|[get_if](../standard-library/variant-functions.md#get_if)|获取对象的变体（如果存在）。|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|**`true`** 如果变量存在，则返回。|
|[swap](../standard-library/variant-functions.md#swap)|交换**变体**。|
|[参阅](../standard-library/variant-functions.md#visit)|移到下一个**变体**。|

### <a name="classes"></a>类

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|引发以报告对变体对象的值的无效访问的对象。|
|[变量](../standard-library/variant.md)|要保存其替代类型之一的值或没有值的对象。|

### <a name="structs"></a>结构

|||
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|用于使变体类型成为默认可构造的变量的替代类型。|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|辅助变体对象。|
|[variant_size](../standard-library/variant-size-structure.md)|辅助变体对象。|

### <a name="objects"></a>对象

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>另请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
