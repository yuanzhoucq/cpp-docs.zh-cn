---
title: '&lt;chrono&gt;'
ms.date: 05/07/2019
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: 72d16b068f337fe935d07e1eb2d0e2b74de6268f
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244868"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

包括标准标头 \< chrono > 来定义表示和操作持续时间及时刻的类和函数。

开始在 Visual Studio 2015 中，实现`steady_clock`发生更改，以满足C++标准对稳定性和单一性的需求。 `steady_clock` 现在基于 QueryPerformanceCounter()，且 `high_resolution_clock` 现在是 `steady_clock` 的 typedef。 因此，在 MicrosoftC++编译器`steady_clock::time_point`现在是 typedef `chrono::time_point<steady_clock>`; 但是，此规则并不一定是其他实现这种情况。

## <a name="requirements"></a>要求

**标头：** \<chrono >

**命名空间：** std

## <a name="members"></a>成员

### <a name="classes"></a>类

|||
|-|-|
|[duration 类](../standard-library/duration-class.md)|描述保持时间间隔的类型。|
|[time_point 类](../standard-library/time-point-class.md)|描述表示时间点的类型。|

### <a name="structs"></a>结构

|||
|-|-|
|[common_type 结构](../standard-library/common-type-structure.md)|介绍有关 `duration` 和 `time_point` 实例化的 [common_type](../standard-library/common-type-class.md) 模板类的专用化。|
|[duration_values 结构](../standard-library/duration-values-structure.md)|提供 `duration` 模板参数 `Rep` 的特定值。|
|[high_resolution_clock 结构](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock 结构](../standard-library/steady-clock-struct.md)|表示 `steady` 时钟。|
|[system_clock 结构](../standard-library/system-clock-structure.md)|表示基于系统实时时钟的*时钟类型*。|
|[treat_as_floating_point 结构](../standard-library/treat-as-floating-point-structure.md)|指定是否可将一种类型视为浮点类型。|

### <a name="functions"></a>函数

|||
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|将 `duration` 对象转换为指定类型。|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|将 `time_point` 对象转换为指定类型。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator-](../standard-library/chrono-operators.md#operator-)|用于对 `duration` 和 `time_point` 对象进行减法或求反运算的运算符。|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|与 `duration` 或 `time_point` 对象一起使用的不等运算符。|
|[operator modulo](../standard-library/chrono-operators.md#op_modulo)|用于对 `duration` 对象进行取模操作的运算符。|
|[operator*](../standard-library/chrono-operators.md#op_star)|`duration` 对象的乘法运算符。|
|[operator/](../standard-library/chrono-operators.md#op_div)|`duration` 对象的除法运算符。|
|[operator+](../standard-library/chrono-operators.md#op_add)|将 `duration` 和 `time_point` 对象相加。|
|[operator&lt;](../standard-library/chrono-operators.md#op_lt)|确定一个 `duration` 或 `time_point` 对象是否小于另一个 `duration` 或 `time_point` 对象。|
|[operator&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|确定一个 `duration` 或 `time_point` 对象是否小于或等于另一个 `duration` 或 `time_point` 对象。|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|确定两个 `duration` 对象是否表示相同长度的时间间隔，或两个 `time_point` 对象是否表示相同的时间点。|
|[operator&gt;](../standard-library/chrono-operators.md#op_gt)|确定一个 `duration` 或 `time_point` 对象是否大于另一个 `duration` 或 `time_point` 对象。|
|[operator&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|确定一个 `duration` 或 `time_point` 对象是否大于或等于另一个 `duration` 或 `time_point` 对象。|

### <a name="typedefs-predefined-duration-types"></a>Typedef （预定义的持续时间类型）

有关在以下 typedefs 中使用的比率类型的详细信息，请参阅 [\<ratio>](../standard-library/ratio.md)。

|||||||`typedef duration<long long, nano> nanoseconds;`|同义词`duration`时钟周期 1 纳秒的类型。 | |`typedef duration<long long, micro> microseconds;`|同义词`duration`具有时钟周期为 1 微秒的类型。 | |`typedef duration<long long, milli> milliseconds;`|同义词`duration`类型的时钟周期为 1 毫秒。 | |`typedef duration<long long> seconds;`|同义词`duration`时钟周期为 1 秒的类型。 | |`typedef duration<int, ratio<60> > minutes;`|同义词`duration`时钟周期为 1 分钟的类型。 | |`typedef duration<int, ratio<3600> > hours;`|同义词`duration`时钟周期为 1 小时的类型。 |

### <a name="literals"></a>文本

**(C + + 11)** \<Chrono > 标头定义了以下[用户定义的文本](../cpp/user-defined-literals-cpp.md)可用于更方便、 类型安全和你的代码的可维护性。 这些文本在 `literals::chrono_literals` 内联命名空间中定义，并且在 std::chrono 存在于作用域中时也存在于作用域中。

|||
|-|-|
|小时运算符""h (无符号长长 Val)|指定整数值形式的小时数。|
|持续时间\<双倍，比\<3600 >> 运算符""h （长双精度值）|指定浮点值形式的小时数。|
|分钟 (运算符""最小值) （无符号长长 Val）|指定整数值形式的分钟数。|
|持续时间\<双倍，比\<60 >> (运算符""最小值) （长双精度值）|指定浮点值形式的分钟数。|
|秒运算符""s (无符号长长 Val)|指定整数值形式的分钟数。|
|持续时间\<双精度 > 运算符""s （长双精度值）|指定浮点值形式的描述。|
|毫秒运算符""ms (无符号长长 Val)|指定整数值形式的毫秒数。|
|持续时间\<双精度、 milli > 运算符""ms （长双精度值）|指定浮点值形式的毫秒数。|
|微秒运算符""我们 (无符号长长 Val)|指定整数值形式的微秒数。|
|持续时间\<双精度，micro > 运算符""我们 （长双精度值）|指定浮点值形式的微秒数。|
|纳秒为单位运算符""ns (无符号长长 Val)|指定整数值形式的纳秒数。|
|持续时间\<双精度，nano > 运算符""ns （长双精度值）|指定浮点值形式的纳秒数。|

下面的示例演示如何使用 chrono 文本。

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
