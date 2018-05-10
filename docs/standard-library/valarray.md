---
title: '&lt;valarray&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <valarray>
dev_langs:
- C++
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 578dd43f747eddbf37f76c41a2fa35df8edca658
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

定义模板类 valarray 和大量支持模板类和函数。

## <a name="syntax"></a>语法

```cpp
#include <valarray>

```

## <a name="remarks"></a>备注

为了提高性能，允许这些模板类和函数有异常的纬度。 具体而言，任何返回类型 **valarray\<** T1**>** 的函数可能会返回某个其他类型 T2 的对象。 在这种情况下，任何接受类型 **valarray\<** T2**>** 的一个或多个参数的函数必须具有接受这些参数（每个替换为类型 T2 的参数）的任意组合的重载。

### <a name="functions"></a>函数

|函数|描述|
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的绝对值。|
|[acos](../standard-library/valarray-functions.md#acos)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的反余弦值。|
|[asin](../standard-library/valarray-functions.md#asin)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的反正弦值。|
|[atan](../standard-library/valarray-functions.md#atan)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的反正切主值。|
|[atan2](../standard-library/valarray-functions.md#atan2)|返回的 valarrays 的元素等于由 valarray 常量和元素的组合指定的笛卡尔组件的反正切值。|
|[cos](../standard-library/valarray-functions.md#cos)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的余弦值。|
|[cosh](../standard-library/valarray-functions.md#cosh)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的双曲余弦值。|
|[exp](../standard-library/valarray-functions.md#exp)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的自然指数。|
|[log](../standard-library/valarray-functions.md#log)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的自然对数。|
|[log10](../standard-library/valarray-functions.md#log10)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的以 10 为底的对数或常用对数。|
|[pow](../standard-library/valarray-functions.md#pow)|对输入 valarray 的元素和常数进行操作，返回的 valarray 的元素等于由输入 valarray 的元素所指定的基数，或者等于具有一定指数的常数所指定的基数，该指数由输入 valarray 的元素或常数指定。|
|[sin](../standard-library/valarray-functions.md#sin)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的正弦值。|
|[sinh](../standard-library/valarray-functions.md#sinh)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的双曲正弦值。|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的平方根。|
|[swap](../standard-library/valarray-functions.md#swap)||
|[tan](../standard-library/valarray-functions.md#tan)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的正切值。|
|[tanh](../standard-library/valarray-functions.md#tanh)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的双曲正切值。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator!=](../standard-library/valarray-operators.md#op_neq)|测试两个相同大小的 valarray 的对应元素是否不相等或者 valarray 的所有元素是否都不等于 valarray 元素类型的指定值。|
|[operator%](../standard-library/valarray-operators.md#op_mod)|获取 valarray 的元素类型的指定值除以两个大小相同的 valarray 的对应元素所得的余数或除以 valarray 所得的余数，或 valarray 除以指定值所得的余数。|
|[operator&](../standard-library/valarray-operators.md#op_amp)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位 **AND**。|
|[operator&&](../standard-library/valarray-operators.md#op_amp_amp)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的逻辑 **AND**。|
|[operator>](../standard-library/valarray-operators.md#op_gt)|测试某个 valarray 的元素是否大于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于或小于 valarray 元素类型的指定值。|
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|测试某个 valarray 的元素是否大于或等于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于等于或小于等于某个指定值。|
|[operator>>](../standard-library/valarray-operators.md#op_gt_gt)|将 valarray 的每个元素的位以指定数位向右移位，或按由第二个 valarray 指定的元素指向值向右移位。|
|[operator<](../standard-library/valarray-operators.md#op_lt)|测试某个 valarray 的元素是否小于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于或小于某个指定值。|
|[operator<=](../standard-library/valarray-operators.md#op_lt_eq)|测试某个 valarray 的元素是否小于或等于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于等于或小于等于某个指定值。|
|[operator<<](../standard-library/valarray-operators.md#op_lt_lt)|将 valarray 的每个元素的位以指定数位向左移位，或按由第二个 valarray 指定的元素指向值向左移位。|
|[operator*](../standard-library/valarray-operators.md#op_star)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向乘积。|
|[operator+](../standard-library/valarray-operators.md#op_add)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向总和。|
|[operator-](../standard-library/valarray-operators.md#operator-)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向差值。|
|[operator/](../standard-library/valarray-operators.md#op_div)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向商。|
|[operator==](../standard-library/valarray-operators.md#op_eq_eq)|测试两个相同大小的 valarray 的对应元素是否相等或者 valarray 的所有元素是否都等于 valarray 元素类型的指定值。|
|[operator^](../standard-library/valarray-operators.md#op_xor)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位异 `OR`。|
|[operator|](../standard-library/valarray-operators.md#op_or)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位 `OR`。|
|[operator||](../standard-library/valarray-operators.md#op_lor)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的逻辑 `OR`。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[gslice 类](../standard-library/gslice-class.md)|用于定义 valarray 多维切分的 valarray 实用程序类。|
|[gslice_array 类](../standard-library/gslice-array-class.md)|一个内部的辅助模板类，该类通过提供由 valarray 的泛切分定义的子集阵列之间的操作来支持泛切分对象。|
|[indirect_array 类](../standard-library/indirect-array-class.md)|一个内部的辅助模板类，该类通过提供子集阵列（通过指定父级 valarray 的索引子集进行定义）之间的操作来支持作为 valarray 的子集的对象。|
|[mask_array 类](../standard-library/mask-array-class.md)|一个内部的辅助模板类，该类通过提供子集阵列之间的操作来支持作为父级 valarray（使用布尔表达式指定）的子集的对象。|
|[slice 类](../standard-library/slice-class.md)|一个用于定义 valarray 的一维矢量型子集的 valarray 实用程序类。|
|[slice_array 类](../standard-library/slice-array-class.md)|一个内部的辅助模板类，该类通过提供由 valarray 的切分定义的子集阵列之间的操作来支持切分对象。|
|[valarray 类](../standard-library/valarray-class.md)|该模板类描述了一个对象，该对象控制类型 **Type** 的元素序列，这些元素存储为数组并用于执行高速数学运算，且针对计算性能进行了优化。|

### <a name="specializations"></a>专用化

|||
|-|-|
|[valarray\<bool> 类](../standard-library/valarray-bool-class.md)|类型 `bool` 的元素的模板类 valarray\<**Type**> 的专用版本。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
