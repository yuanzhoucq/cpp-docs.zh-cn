---
title: duration_values 结构
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: ba4b202a5c8c6da742ac884bf58a5b8c55373d14
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454292"
---
# <a name="durationvalues-structure"></a>duration_values 结构

为[持续时间](../standard-library/duration-class.md)模板参数 `Rep` 提供指定值。

## <a name="syntax"></a>语法

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[max](#max)|静态。 指定类型 `Rep` 的值上限。|
|[min](#min)|静态。 指定类型 `Rep` 的值下限。|
|[无](#zero)|静态。 返回 `Rep(0)`。|

## <a name="requirements"></a>要求

**标头:** \<chrono >

**命名空间：** std::chrono

## <a name="max"></a>  duration_values::max

返回类型 `Ref` 的值上限的静态方法。

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>返回值

实际上，返回 `numeric_limits<Rep>::max()`。

### <a name="remarks"></a>备注

当 `Rep` 是用户定义类型时，返回值必须大于 [duration_values::zero](#zero)。

## <a name="min"></a>  duration_values::min

返回类型值下限的静态方法`Ref`。

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>返回值

实际上，返回 `numeric_limits<Rep>::lowest()`。

### <a name="remarks"></a>备注

当 `Rep` 是用户定义类型时，返回值必须小于或等于 [duration_values::zero](#zero)。

## <a name="zero"></a>  duration_values::zero

返回 `Rep(0)`。

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>备注

当 `Rep` 是用户定义类型时，返回值必须表示正无穷大。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
