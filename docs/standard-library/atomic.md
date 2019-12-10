---
title: '&lt;atomic&gt;'
description: 描述标准C++库的原子标头中可用的类型和函数。
ms.date: 12/06/2019
f1_keywords:
- <atomic>
- atomic/std::atomic_int_least32_t
- atomic/std::atomic_ullong
- atomic/std::atomic_ptrdiff_t
- atomic/std::atomic_char16_t
- atomic/std::atomic_schar
- atomic/std::atomic_ulong
- atomic/std::atomic_uint_fast32_t
- atomic/std::atomic_uint8_t
- atomic/std::atomic_int32_t
- atomic/std::atomic_uint_fast64_t
- atomic/std::atomic_uint32_t
- atomic/std::atomic_int16_t
- atomic/std::atomic_uintmax_t
- atomic/std::atomic_intmax_t
- atomic/std::atomic_long
- atomic/std::atomic_int
- atomic/std::atomic_uint_least8_t
- atomic/std::atomic_size_t
- atomic/std::atomic_uint_fast16_t
- atomic/std::atomic_wchar_t
- atomic/std::atomic_int_fast64_t
- atomic/std::atomic_uint_fast8_t
- atomic/std::atomic_int_fast8_t
- atomic/std::atomic_intptr_t
- atomic/std::atomic_uint
- atomic/std::atomic_uint16_t
- atomic/std::atomic_char32_t
- atomic/std::atomic_uint64_t
- atomic/std::atomic_ushort
- atomic/std::atomic_int_least16_t
- atomic/std::atomic_char
- atomic/std::atomic_uint_least32_t
- atomic/std::atomic_uintptr_t
- atomic/std::atomic_short
- atomic/std::atomic_llong
- atomic/std::atomic_uint_least16_t
- atomic/std::atomic_int_fast16_t
- atomic/std::atomic_int_least8_t
- atomic/std::atomic_int_least64_t
- atomic/std::atomic_int_fast32_t
- atomic/std::atomic_uchar
- atomic/std::atomic_int8_t
- atomic/std::atomic_int64_t
- atomic/std::atomic_uint_least64_t
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
ms.openlocfilehash: d11e8bf2067c1c8525725ae74e713ac834d89ec4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991165"
---
# <a name="ltatomicgt"></a>&lt;atomic&gt;

定义用于创建支持原子操作的类型的类和类模板。

## <a name="syntax"></a>语法

```cpp
#include <atomic>
```

## <a name="remarks"></a>备注

> [!NOTE]
> 在使用[/clr： pure](../build/reference/clr-common-language-runtime-compilation.md)编译的代码中，此标头被阻止。 在 Visual Studio 2017 及更高版本中，不推荐使用 **/clr： pure**和 **/clr： safe** 。

一个原子操作有两个关键属性，帮助你使用多个线程正确操控对象，而无需使用互斥锁。

- 由于原子操作是不可分的，因此，来自不同线程的同一对象的第二个原子操作只能在第一个原子操作之前或之后获取该对象的状态。

- 基于其 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 参数，原子操作可以针对同一个线程中其他原子操作的影响可见性建立排序要求。 因此，它会抑制违反排序要求的编译器优化。

在某些平台上，如果不使用 `mutex` 锁，可能无法有效地实施某些类型的原子操作。 如果对该类型执行的原子操作都没有使用锁，则原子类型为*无锁*。

**C + + 11**：在信号处理程序中，如果 `obj.is_lock_free()` 或 `atomic_is_lock_free(x)` 为 true，则可以对对象 `obj` 执行原子操作。

类[atomic_flag](../standard-library/atomic-flag-structure.md)提供保存**bool**标志的最小原子类型。 其操作始终为无锁操作。

类模板 `atomic<T>` 存储其参数类型的对象 `T`，并提供对该存储值的原子访问。 你可以使用可通过 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 复制的任何类型对该类进行实例化，并通过使用 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) 测试是否相等。 特别是，你可以将其与满足这些要求的用户定义类型结合使用，在很多情况下是与浮点类型结合使用。

另外，该模板还具有一套用于整型类型的专用化和用于指针的部分专用化。 这些专用化提供了无法通过主模板获得的其他操作。

## <a name="pointer-specializations"></a>指针专用化

`atomic<T *>` 部分专用化应用于所有指针类型。 它们提供用于指针算术的方法。

## <a name="integral-specializations"></a>整型专用化

`atomic<integral>` 专用化将应用于所有整型类型。 它们提供了无法通过主模板获得的其他操作。

每个 `atomic<integral>` 类型都有一个对应的宏，你可以在 `if directive` 中使用该宏来确定编译时对该类型执行的操作是否为无锁。 如果宏的值为零，则对该类型的操作不会无锁。 如果值为 1，则操作可能为无锁，且需要进行运行时检查。 如果值为 2，操作为无锁。 可以使用函数 `atomic_is_lock_free` 确定在运行时对类型执行的操作是否为无锁。

对于每个整型类型，都有一个对应的命名原子类型，用于管理该整型类型的对象。 每个 `atomic_integral` 类型都具有与 `atomic<T>` 的相应实例化相同的成员函数集，并且可以传递至任何非成员原子函数。

|`atomic_integral` 类型|整型类型|`atomic_is_lock_free` 宏|
|----------------------------|-------------------|---------------------------------|
|`atomic_char`|**char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_schar`|**带符号字符**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_uchar`|**unsigned char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_char16_t`|`char16_t`|ATOMIC_CHAR16_T_LOCK_FREE|
|`atomic_char32_t`|`char32_t`|ATOMIC_CHAR32_T_LOCK_FREE|
|`atomic_wchar_t`|**wchar_t**|ATOMIC_WCHAR_T_LOCK_FREE|
|`atomic_short`|**short**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_ushort`|**unsigned short**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_int`|**int**|ATOMIC_INT_LOCK_FREE|
|`atomic_uint`|**unsigned int**|ATOMIC_INT_LOCK_FREE|
|`atomic_long`|**long**|ATOMIC_LONG_LOCK_FREE|
|`atomic_ulong`|**unsigned long**|ATOMIC_LONG_LOCK_FREE|
|`atomic_llong`|**long long**|ATOMIC_LLONG_LOCK_FREE|
|`atomic_ullong`|**无符号长长**|ATOMIC_LLONG_LOCK_FREE|

对于标头 \<inttypes.h> 中定义的某些类型，原子模版的专用化存在 Typedef 名称。

|原子类型|Typedef 名称|
|-----------------|------------------|
|`atomic_int8_t`|`atomic<int8_t>`|
|`atomic_uint8_t`|`atomic<uint8_t>`|
|`atomic_int16_t`|`atomic<int16_t>`|
|`atomic_uint16_t`|`atomic<uint16_t>`|
|`atomic_int32_t`|`atomic<int32_t>`|
|`atomic_uint32_t`|`atomic<uint32_t>`|
|`atomic_int64_t`|`atomic<int64_t>`|
|`atomic_uint64_t`|`atomic<uint64_t>`|
|`atomic_int_least8_t`|`atomic<int_least8_t>`|
|`atomic_uint_least8_t`|`atomic<uint_least8_t>`|
|`atomic_int_least16_t`|`atomic<int_least16_t>`|
|`atomic_uint_least16_t`|`atomic<uint_least16_t>`|
|`atomic_int_least32_t`|`atomic<int_least32_t>`|
|`atomic_uint_least32_t`|`atomic<uint_least32_t>`|
|`atomic_int_least64_t`|`atomic<int_least64_t>`|
|`atomic_uint_least64_t`|`atomic<uint_least64_t>`|
|`atomic_int_fast8_t`|`atomic<int_fast8_t>`|
|`atomic_uint_fast8_t`|`atomic<uint_fast8_t>`|
|`atomic_int_fast16_t`|`atomic<int_fast16_t>`|
|`atomic_uint_fast16_`|`atomic<uint_fast16_t>`|
|`atomic_int_fast32_t`|`atomic<int_fast32_t>`|
|`atomic_uint_fast32_t`|`atomic<uint_fast32_t>`|
|`atomic_int_fast64_t`|`atomic<int_fast64_t>`|
|`atomic_uint_fast64_t`|`atomic<uint_fast64_t>`|
|`atomic_intptr_t`|`atomic<intptr_t>`|
|`atomic_uintptr_t`|`atomic<uintptr_t>`|
|`atomic_size_t`|`atomic<size_t>`|
|`atomic_ptrdiff_t`|`atomic<ptrdiff_t>`|
|`atomic_intmax_t`|`atomic<intmax_t>`|
|`atomic_uintmax_t`|`atomic<uintmax_t>`|

## <a name="structs"></a>结构

|Name|描述|
|----------|-----------------|
|[atomic 结构](../standard-library/atomic-structure.md)|描述对存储值执行原子操作的对象。|
|[atomic_flag 结构](../standard-library/atomic-flag-structure.md)|描述一个对象，该对象以原子方式设置并清除**布尔**型标志。|

## <a name="enums"></a>枚举

|Name|描述|
|----------|-----------------|
|[memory_order 枚举](../standard-library/atomic-enums.md#memory_order_enum)|为内存位置上的同步操作提供符号名称。 这些操作将影响一个线程内的分配如何在另一个线程内变得可见。|

## <a name="functions"></a>函数

在下面的列表中，不以 `_explicit` 结尾的函数具有相应 `_explicit`的语义，只不过它们具有 `memory_order_seq_cst`的隐式[memory_order](../standard-library/atomic-enums.md#memory_order_enum)参数。

|Name|描述|
|----------|-----------------|
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|执行*原子比较和交换*操作。|
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|执行*原子比较和交换*操作。|
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|执行*弱原子比较和交换*操作。|
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|执行*弱原子比较和交换*操作。|
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|替换存储值。|
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|替换存储值。|
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|将指定的值添加到现有存储值。|
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|将指定的值添加到现有存储值。|
|[atomic_fetch_and](../standard-library/atomic-functions.md#atomic_fetch_and)|对指定值和现有存储值执行按位 `and`。|
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|对指定值和现有存储值执行按位 `and`。|
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|对指定值和现有存储值执行按位 `or`。|
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|对指定值和现有存储值执行按位 `or`。|
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|从现有存储值减去指定的值。|
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|从现有存储值减去指定的值。|
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|对指定值和现有存储值执行按位 `exclusive or`。|
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|对指定值和现有存储值执行按位 `exclusive or`。|
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|将 `atomic_flag` 对象中的标志设置为**false**。|
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|将 `atomic_flag` 对象中的标志设置为**false**。|
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|将 `atomic_flag` 对象中的标志设置为**true**。|
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|将 `atomic_flag` 对象中的标志设置为**true**。|
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|设置 `atomic` 对象中存储的值。|
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|指定对指定对象执行的原子操作是否为无锁。|
|[atomic_load](../standard-library/atomic-functions.md#atomic_load)|以原子方式检索一个值。|
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|以原子方式检索一个值。|
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|充当 *fence*，用于在调用线程中信号处理程序在同一线程中执行的 fence 之间建立内存排序要求。|
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|以原子方式存储一个值。|
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|以原子方式存储一个值。|
|[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)|充当就其他 fence 建立内存排序要求的 *fence*。|
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|中断可能的依赖关系链。|

## <a name="see-also"></a>另请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
