---
title: atomic_flag 结构
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ff60e05c7d14104e164e8251a9146f8b0d0dcde3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203918"
---
# <a name="atomic_flag-structure"></a>atomic_flag 结构

描述一个对象，该对象以原子方式设置并清除 **`bool`** 标志。 对原子标志执行的操作始终是无锁的。

## <a name="syntax"></a>语法

```cpp
struct atomic_flag;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[清除](#clear)|将存储的标志设置为 **`false`** 。|
|[test_and_set](#test_and_set)|将存储的标志设置为 **`true`** 并返回初始标志值。|

## <a name="remarks"></a>备注

`atomic_flag` 对象可传递给非成员函数 [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)、[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)、[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) 和 [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)。 可使用值 `ATOMIC_FLAG_INIT` 对其进行初始化。

## <a name="requirements"></a>要求

**标头：**\<atomic>

**命名空间:** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag：： clear

将 **`bool`** 存储在中的标志设置 **`*this`** 为在 **`false`** 指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束内。

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>参数

*为了*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag：： test_and_set

将 **`bool`** 存储在中的标志设置 **`*this`** 为在 **`true`** 指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束内。

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>参数

*为了*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

存储在中的标志的初始值 **`*this`** 。

## <a name="see-also"></a>另请参阅

[\<atomic>](../standard-library/atomic.md)
