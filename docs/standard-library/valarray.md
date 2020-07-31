---
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: eb782b0d16c4bc826da4ea9291756f34ca0eaf29
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215408"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

定义类模板 valarray 和众多支持类模板和函数。

## <a name="requirements"></a>要求

**标头：**\<valarray>

**命名空间:** std

> [!NOTE]
> \<valarray>库使用 "#include <initializer_list>" 语句。

## <a name="remarks"></a>备注

这些类模板和函数允许使用异常纬度来提高性能。 具体而言，返回类型的任何函数 `valarray<T1>` 都可能返回某个其他类型 T2 的对象。 在这种情况下，任何接受类型的一个或多个参数的函数 `valarray<T2>` 必须具有接受这些参数的任意组合的重载，每个重载都替换为类型 T2 的参数。

## <a name="members"></a>成员

### <a name="functions"></a>函数

|||
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的绝对值。|
|[acos](../standard-library/valarray-functions.md#acos)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的反余弦值。|
|[asin](../standard-library/valarray-functions.md#asin)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的反正弦值。|
|[atan](../standard-library/valarray-functions.md#atan)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的反正切主值。|
|[atan2](../standard-library/valarray-functions.md#atan2)|返回的 valarrays 的元素等于由 valarray 常量和元素的组合指定的笛卡尔组件的反正切值。|
|[准备](../standard-library/valarray-functions.md#begin)||
|[缆](../standard-library/valarray-functions.md#cos)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的余弦值。|
|[cosh](../standard-library/valarray-functions.md#cosh)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的双曲余弦值。|
|[end](../standard-library/valarray-functions.md#end)||
|[exp](../standard-library/valarray-functions.md#exp)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的自然指数。|
|[日志](../standard-library/valarray-functions.md#log)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的自然对数。|
|[log10](../standard-library/valarray-functions.md#log10)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的以 10 为底的对数或常用对数。|
|[pow](../standard-library/valarray-functions.md#pow)|对输入 valarray 的元素和常数进行操作，返回的 valarray 的元素等于由输入 valarray 的元素所指定的基数，或者等于具有一定指数的常数所指定的基数，该指数由输入 valarray 的元素或常数指定。|
|[sin](../standard-library/valarray-functions.md#sin)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的正弦值。|
|[sinh](../standard-library/valarray-functions.md#sinh)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的双曲正弦值。|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的平方根。|
|[swap](../standard-library/valarray-functions.md#swap)||
|[tan](../standard-library/valarray-functions.md#tan)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的正切值。|
|[tanh](../standard-library/valarray-functions.md#tanh)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的双曲正切值。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator！ =](../standard-library/valarray-operators.md#op_neq)|测试两个相同大小的 valarray 的对应元素是否不相等或者 valarray 的所有元素是否都不等于 valarray 元素类型的指定值。|
|[操作员](../standard-library/valarray-operators.md#op_mod)|获取 valarray 的元素类型的指定值除以两个大小相同的 valarray 的对应元素所得的余数或除以 valarray 所得的余数，或 valarray 除以指定值所得的余数。|
|[运算符&](../standard-library/valarray-operators.md#op_amp)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位 `AND`。|
|[运算符&&](../standard-library/valarray-operators.md#op_amp_amp)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的逻辑 `AND`。|
|[运算符>](../standard-library/valarray-operators.md#op_gt)|测试某个 valarray 的元素是否大于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于或小于 valarray 元素类型的指定值。|
|[运算符>=](../standard-library/valarray-operators.md#op_gt_eq)|测试某个 valarray 的元素是否大于或等于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于等于或小于等于某个指定值。|
|[运算符>>](../standard-library/valarray-operators.md#op_gt_gt)|将 valarray 的每个元素的位以指定数位向右移位，或按由第二个 valarray 指定的元素指向值向右移位。|
|[运算符<](../standard-library/valarray-operators.md#op_lt)|测试某个 valarray 的元素是否小于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于或小于某个指定值。|
|[运算符<=](../standard-library/valarray-operators.md#op_lt_eq)|测试某个 valarray 的元素是否小于或等于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于等于或小于等于某个指定值。|
|[运算符<<](../standard-library/valarray-operators.md#op_lt_lt)|将 valarray 的每个元素的位以指定数位向左移位，或按由第二个 valarray 指定的元素指向值向左移位。|
|[操作员](../standard-library/valarray-operators.md#op_star)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向乘积。|
|[operator +](../standard-library/valarray-operators.md#op_add)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向总和。|
|[操作员](../standard-library/valarray-operators.md#operator-)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向差值。|
|[操作员](../standard-library/valarray-operators.md#op_div)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向商。|
|[operator = =](../standard-library/valarray-operators.md#op_eq_eq)|测试两个相同大小的 valarray 的对应元素是否相等或者 valarray 的所有元素是否都等于 valarray 元素类型的指定值。|
|[运算符 ^](../standard-library/valarray-operators.md#op_xor)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位异 `OR`。|
|[运算符&#124;](../standard-library/valarray-operators.md#op_or)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位 `OR`。|
|[运算符&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的逻辑 `OR`。|

### <a name="classes"></a>类

|||
|-|-|
|[gslice 类](../standard-library/gslice-class.md)|用于定义 valarray 多维切分的 valarray 实用程序类。|
|[gslice_array 类](../standard-library/gslice-array-class.md)|一个内部的辅助类模板，它通过提供由 valarray 的常规切片定义的子集数组之间的操作来支持常规切片对象。|
|[indirect_array 类](../standard-library/indirect-array-class.md)|一个内部的辅助类模板，它通过在通过指定父级 valarray 的索引子集定义的子集数组间提供操作来支持作为 valarray 子集的对象。|
|[mask_array 类](../standard-library/mask-array-class.md)|一个内部的辅助类模板，它通过提供子集数组之间的操作来支持作为父 valarray 的子集的对象（使用布尔表达式指定）。|
|[切片类](../standard-library/slice-class.md)|一个用于定义 valarray 的一维矢量型子集的 valarray 实用程序类。|
|[slice_array 类](../standard-library/slice-array-class.md)|一个内部的辅助类模板，它通过提供由 valarray 的切片定义的子集数组之间的操作来支持切片对象。|
|[valarray 类](../standard-library/valarray-class.md)|类模板描述了一个对象，该对象控制类型的元素的序列 `Type` ，这些元素存储为数组并针对计算性能进行了优化。|

### <a name="specializations"></a>专用化

|||
|-|-|
|[valarray \<bool> 类](../standard-library/valarray-bool-class.md)|类模板的专用版本 valarray \<**Type**> 类型的元素 **`bool`** 。|

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
