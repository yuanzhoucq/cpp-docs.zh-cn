---
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 76b04c3c26f6ec49f1d816feaeec7e21312d79a9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246284"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

定义有助于构造和管理对象对的 C++ 标准库类型、函数和运算符，这些项在每次需要将两个对象视为单个对象时都非常有用。

## <a name="requirements"></a>要求

**标头：** \<utility>

**命名空间：** std

## <a name="remarks"></a>备注

对广泛用于 C++ 标准库中。 对于各种函数，需要将这些对用作参数和返回值，而对于 [map 类](../standard-library/map-class.md)和 [multimap 类](../standard-library/multimap-class.md)等容器，则需将其用作元素类型。 \<map> 将自动包括 \<utility> 标头以帮助管理其键/值对类型元素。

> [!NOTE]
> \<实用程序 > 标头使用语句`#include <initializer_list>`。 它还指`class tuple`中定义\<元组 >。

## <a name="members"></a>成员

### <a name="classes"></a>类

|||
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|基元数值转换为浮点格式。|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|一个包装 `pair` 元素的类型的类。|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|一个包装 `pair` 元素计数的类。|

### <a name="objects"></a>对象

|||
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)||
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)||
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)||
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)||

### <a name="functions"></a>函数

|||
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|返回类型。|
|[declval](../standard-library/utility-functions.md#declval)|速记表达式求值。|
|[exchange](../standard-library/utility-functions.md#exchange)|向对象赋予新值并返回其旧值。|
|[forward](../standard-library/utility-functions.md#forward)|保留参数的引用类型（`lvalue` 或 `rvalue`），使其不被完美转发掩盖。|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|一个从 `pair` 对象获取元素的函数。|
|[make_pair](../standard-library/utility-functions.md#make_pair)|一个模板帮助程序函数，用于构造类型 `pair` 的对象，其中组件类型基于作为参数传递的数据类型。|
|[move](../standard-library/utility-functions.md#move)|将传入的参数作为 `rvalue` 引用返回。|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|交换两个 `pair` 对象的元素。|
|[to_chars](../standard-library/utility-functions.md#to_chars)|将值转换为字符字符串。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|测试运算符左侧和右侧的 pair 对象是否不相等。|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|测试运算符左侧和右侧的 pair 对象是否相等。|
|[operator\<](../standard-library/utility-operators.md#op_lt)|测试运算符左侧的 pair 对象是否小于右侧的 pair 对象。|
|[operator\<=](../standard-library/utility-operators.md#op_gt_eq)|测试运算符左侧的 pair 对象是否小于或等于右侧的 pair 对象。|
|[operator>](../standard-library/utility-operators.md#op_gt)|测试运算符左侧的 pair 对象是否大于右侧的 pair 对象。|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|测试运算符左侧的 pair 对象是否大于或等于右侧的 pair 对象。|

### <a name="structs"></a>结构

|||
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|结构用于`from_chars`。|
|[identity](../standard-library/identity-structure.md)|一个将类型定义作为模板参数提供的结构。|
|[in_place_t](../standard-library/in-place-t-struct.md)|此外包括结构`in_place_type_t`和`in_place_index_t`。|
|[integer_sequence](../standard-library/integer-sequence-class.md)|表示整数序列。|
|[pair](../standard-library/pair-structure.md)|一种类型，它提供了将两个对象视为单个对象的功能。|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|用于保留单独的构造函数和函数重载的类型。|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|结构用于`to_chars`。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
