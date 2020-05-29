---
title: duration_values 结构
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: e2c03b4540ea5f89843562d1310b71635b3bc259
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368745"
---
# <a name="duration_values-structure"></a>duration_values 结构

为[持续时间](../standard-library/duration-class.md)模板参数 `Rep` 提供指定值。

## <a name="syntax"></a>语法

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[麦克斯](#max)|静态。 指定类型 `Rep` 的值上限。|
|[分钟](#min)|静态。 指定类型 `Rep` 的值下限。|
|[零](#zero)|静态。 返回 `Rep(0)`。|

## <a name="requirements"></a>要求

**标题：**\<计时>

**命名空间：** std::chrono

## <a name="duration_valuesmax"></a><a name="max"></a>duration_values：最大

返回类型 `Ref` 的值上限的静态方法。

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>返回值

实际上，返回 `numeric_limits<Rep>::max()`。

### <a name="remarks"></a>备注

当 `Rep` 是用户定义类型时，返回值必须大于 [duration_values::zero](#zero)。

## <a name="duration_valuesmin"></a><a name="min"></a>duration_values：分钟

返回类型值下限的静态方法`Ref`。

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>返回值

实际上，返回 `numeric_limits<Rep>::lowest()`。

### <a name="remarks"></a>备注

当 `Rep` 是用户定义类型时，返回值必须小于或等于 [duration_values::zero](#zero)。

## <a name="duration_valueszero"></a><a name="zero"></a>duration_values：：零

返回 `Rep(0)`。

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>备注

当 `Rep` 是用户定义类型时，返回值必须表示正无穷大。

## <a name="see-also"></a>另请参阅

[标题文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
