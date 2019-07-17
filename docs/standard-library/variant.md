---
title: '&lt;变体&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 7a812ccc3c8cb2a660c01ad2b17ea75b5d5c9542
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268439"
---
# <a name="ltvariantgt"></a>&lt;变体&gt;

变体对象保存和管理值。 如果将该变量保留了一个值，该值的类型必须是提供给变体的模板自变量类型之一。 这些模板自变量被调用替代项。

## <a name="requirements"></a>要求

**标头：** \<变量 >

**命名空间：** std

## <a name="members"></a>成员

### <a name="operators"></a>运算符

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|测试运算符左侧的变体对象是否等于右侧的变体对象。|
|[operator!=](../standard-library/forward-list-operators.md#op_neq)|测试运算符左侧的变体对象是否不等于右侧的变体对象。|
|[operator<](../standard-library/forward-list-operators.md#op_lt)|测试运算符左侧的变体对象是否小于右侧的变体对象。|
|[operator<=](../standard-library/forward-list-operators.md#op_lt_eq)|测试运算符左侧的变体对象小于或等于变体对象，在右侧。|
|[operator>](../standard-library/forward-list-operators.md#op_gt)|测试运算符左侧的变体对象是否大于右侧的变体对象。|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|测试运算符左侧的变体对象是否大于或等于右侧的变体对象。|

### <a name="functions"></a>函数

|||
|-|-|
|[get](../standard-library/variant-functions.md#get)|获取一个对象的变体。|
|[get_if](../standard-library/variant-functions.md#get_if)|如果它存在，则获取一个对象的变体。|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|返回 **，则返回 true**如果存在一个变体。|
|[swap](../standard-library/variant-functions.md#swap)|交换**变体**。|
|[请访问](../standard-library/variant-functions.md#visit)|将移动到下一步**变体**。|

### <a name="classes"></a>类

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|向报表为变量对象的值的无效访问引发的对象。|
|[变体](../standard-library/variant.md)|为对象保留一个及其替代的类型，或没有值的值。|

### <a name="structs"></a>结构

|||
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|要将变体类型默认可构造一个变体的替代类型。|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|可帮助您的变体对象。|
|[variant_size](../standard-library/variant-size-structure.md)|可帮助您的变体对象。|

### <a name="objects"></a>对象

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
