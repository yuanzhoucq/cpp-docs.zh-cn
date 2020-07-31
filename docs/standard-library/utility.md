---
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 1beade28ceec0f1552def4bc70c2e95e6b2aa24d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215434"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

定义有助于构造和管理对象对的 C++ 标准库类型、函数和运算符，这些项在每次需要将两个对象视为单个对象时都非常有用。

## <a name="requirements"></a>要求

**标头：**\<utility>

**命名空间:** std

## <a name="remarks"></a>备注

对广泛用于 C++ 标准库中。 对于各种函数，需要将这些对用作参数和返回值，而对于 [map 类](../standard-library/map-class.md)和 [multimap 类](../standard-library/multimap-class.md)等容器，则需将其用作元素类型。 \<utility>标头由自动包含在内 \<map> ，以帮助管理其键/值对类型元素。

> [!NOTE]
> \<utility>标头使用语句 `#include <initializer_list>` 。 它还引用 `class tuple` 中定义的 \<tuple> 。

## <a name="members"></a>成员

### <a name="classes"></a>类

|类型|描述|
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|用于基元数值转换的浮点格式。|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|一个包装 `pair` 元素的类型的类。|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|一个包装 `pair` 元素计数的类。|

### <a name="objects"></a>对象

|模板|描述|
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)|为常见情况定义的别名模板，其中 `T` 是`std::size_t`  |
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)|用于将任何类型参数包转换为同一长度的索引序列的帮助程序别名模板|
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)| 用于简化类型创建的帮助程序别名模板 `std::index_sequence` 。 |
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)|用于简化类型创建的帮助程序别名模板 `std::integer_sequence` 。|

### <a name="functions"></a>函数

|函数|描述|
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|返回类型。|
|[declval](../standard-library/utility-functions.md#declval)|简写表达式计算。|
|[外汇](../standard-library/utility-functions.md#exchange)|将新值分配给对象并返回其旧值。|
|[结转](../standard-library/utility-functions.md#forward)|保留参数的引用类型（`lvalue` 或 `rvalue`），使其不被完美转发掩盖。|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|一个从 `pair` 对象获取元素的函数。|
|[make_pair](../standard-library/utility-functions.md#make_pair)|一个模板帮助程序函数，用于构造类型 `pair` 的对象，其中组件类型基于作为参数传递的数据类型。|
|[move](../standard-library/utility-functions.md#move)|将传入的参数作为 `rvalue` 引用返回。|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|交换两个 `pair` 对象的元素。|
|[to_chars](../standard-library/utility-functions.md#to_chars)|将值转换为字符串。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[operator！ =](../standard-library/utility-operators.md#op_neq)|测试运算符左侧和右侧的 pair 对象是否不相等。|
|[operator = =](../standard-library/utility-operators.md#op_eq_eq)|测试运算符左侧和右侧的 pair 对象是否相等。|
|[操作员\<](../standard-library/utility-operators.md#op_lt)|测试运算符左侧的 pair 对象是否小于右侧的 pair 对象。|
|[操作员\<=](../standard-library/utility-operators.md#op_gt_eq)|测试运算符左侧的 pair 对象是否小于或等于右侧的 pair 对象。|
|[运算符>](../standard-library/utility-operators.md#op_gt)|测试运算符左侧的 pair 对象是否大于右侧的 pair 对象。|
|[运算符>=](../standard-library/utility-operators.md#op_gt_eq)|测试运算符左侧的 pair 对象是否大于或等于右侧的 pair 对象。|

### <a name="structs"></a>结构

|结构|说明|
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|用于的结构 `from_chars` 。|
|[identity](../standard-library/identity-structure.md)|一个将类型定义作为模板参数提供的结构。|
|[in_place_t](../standard-library/in-place-t-struct.md)|还包括结构 `in_place_type_t` 和 `in_place_index_t` 。|
|[integer_sequence](../standard-library/integer-sequence-class.md)|表示整数序列。|
|[对](../standard-library/pair-structure.md)|一种类型，它提供了将两个对象视为单个对象的功能。|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|用于保留单独的构造函数和函数重载的类型。|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|用于的结构 `to_chars` 。|

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
