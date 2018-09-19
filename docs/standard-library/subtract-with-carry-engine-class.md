---
title: subtract_with_carry_engine 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a956212df2579298f1f947bf2388dec1532dff10
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721729"
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine 类

通过带进位减法（滞后型斐波那契）算法生成随机序列。

## <a name="syntax"></a>语法

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>参数

*UIntType*<br/>
无符号的整数结果类型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。

*W*<br/>
**字大小**。 状态序列的每个字的大小（以字节为单位）。 **前提条件**：`0 < W ≤ numeric_limits<UIntType>::digits`

*S*<br/>
**短滞后**。 整数值数。 **前提条件**：`0 < S < R`

*R*<br/>
**长滞后**。 确定生成的系列中的重复。

## <a name="members"></a>Members

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed` 是定义为 `19780503u` 且用作 `subtract_with_carry_engine::seed` 和单个值的构造函数的默认参数值的成员常量。|||

有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>备注

`substract_with_carry_engine` 模板类是基于 [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md) 的改进。 这两个引擎的速度和结果的质量都不如 [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md)。

此引擎使用重复关系（*周期*）`x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`产生用户指定的无符号整型值，其中如果 `cy(i)`，则 `1` 包含值 `x(i - S) - x(i - R) - cy(i - 1) < 0`；如果 `0`，则 `M` 包含 `2`<sup>W</sup>。引擎的状态是进位指示器加上*R*值。 这些值包含的上一次*R*值返回的 if`operator()`至少已调用*R*次，否则`N`已返回的值和最后一个`R - N`种子值。

模板参数 `UIntType` 必须大到足以保留最多 `M - 1` 个值。

虽然可以从此引擎直接构造生成器，但也可以使用预定义的 typedef 之一：

`ranlux24_base`：用作 `ranlux24` 的基础。
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`：用作 `ranlux48` 的基础。
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

有关带进位减法引擎算法的详细信息，请参阅 Wikipedia 文章 [Lagged Fibonacci generator](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator)（滞后斐波纳契生成器）。

## <a name="requirements"></a>要求

**标头：**\<random>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)<br/>
