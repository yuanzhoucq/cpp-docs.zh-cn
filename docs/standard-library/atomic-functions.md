---
title: '&lt;atomic&gt; 函数'
ms.date: 07/11/2018
f1_keywords:
- atomic/std::atomic_compare_exchange_strong
- atomic/std::atomic_compare_exchange_strong_explicit
- atomic/std::atomic_compare_exchange_weak
- atomic/std::atomic_compare_exchange_weak_explicit
- atomic/std::atomic_exchange
- atomic/std::atomic_exchange_explicit
- atomic/std::atomic_fetch_add
- atomic/std::atomic_fetch_add_explicit
- atomic/std::atomic_fetch_and
- atomic/std::atomic_fetch_and_explicit
- atomic/std::atomic_fetch_or
- atomic/std::atomic_fetch_or_explicit
- atomic/std::atomic_fetch_sub
- atomic/std::atomic_fetch_sub_explicit
- atomic/std::atomic_fetch_xor
- atomic/std::atomic_fetch_xor_explicit
- atomic/std::atomic_flag_clear
- atomic/std::atomic_flag_clear_explicit
- atomic/std::atomic_flag_test_and_set
- atomic/std::atomic_flag_test_and_set_explicit
- atomic/std::atomic_init
- atomic/std::atomic_is_lock_free
- atomic/std::atomic_load
- atomic/std::atomic_load_explicit
- atomic/std::atomic_signal_fence
- atomic/std::atomic_store
- atomic/std::atomic_store_explicit
- atomic/std::atomic_thread_fence
- atomic/std::kill_dependency
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
helpviewer_keywords:
- std::atomic_compare_exchange_strong [C++]
- std::atomic_compare_exchange_strong_explicit [C++]
- std::atomic_compare_exchange_weak [C++]
- std::atomic_compare_exchange_weak_explicit [C++]
- std::atomic_exchange [C++]
- std::atomic_exchange_explicit [C++]
- std::atomic_fetch_add [C++]
- std::atomic_fetch_add_explicit [C++]
- std::atomic_fetch_and [C++]
- std::atomic_fetch_and_explicit [C++]
- std::atomic_fetch_or [C++]
- std::atomic_fetch_or_explicit [C++]
- std::atomic_fetch_sub [C++]
- std::atomic_fetch_sub_explicit [C++]
- std::atomic_fetch_xor [C++]
- std::atomic_fetch_xor_explicit [C++]
- std::atomic_flag_clear [C++]
- std::atomic_flag_clear_explicit [C++]
- std::atomic_flag_test_and_set [C++]
- std::atomic_flag_test_and_set_explicit [C++]
- std::atomic_init [C++]
- std::atomic_is_lock_free [C++]
- std::atomic_load [C++]
- std::atomic_load_explicit [C++]
- std::atomic_signal_fence [C++]
- std::atomic_store [C++]
- std::atomic_store_explicit [C++]
- std::atomic_thread_fence [C++]
- std::kill_dependency [C++]
ms.openlocfilehash: b6d03da446e4a3bae02f662e5b106bd5de534d0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376890"
---
# <a name="ltatomicgt-functions"></a>&lt;atomic&gt; 函数

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

执行原子比较和交换操作。

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型`Ty`值的*原子*对象的指针。

*Exp*\
指向类型 `Ty` 的值的指针。

*价值*\
一个 `Ty` 类型的值。

### <a name="return-value"></a>返回值

如果值相等，则**为 true，** 否则**为 false**。

### <a name="remarks"></a>备注

此方法使用隐式 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 参数执行原子比较和交换操作。 有关详细信息，请参阅 [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)。

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

执行*原子比较和交换*操作。

```cpp
template <class T>
inline bool atomic_compare_exchange_strong_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `Ty` 值的 `atomic` 对象的指针。

*Exp*\
指向类型 `Ty` 的值的指针。

*价值*\
一个 `Ty` 类型的值。

*订单1*\
第一个 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 参数。

*订单2*\
第二个 `memory_order` 参数。 *Order2*的值不能`memory_order_release`或`memory_order_acq_rel`，它不能比订单*1*的值强。

### <a name="return-value"></a>返回值

如果值相等，则**为 true，** 否则**为 false**。

### <a name="remarks"></a>备注

*原子比较和交换操作*将*存储在 Atom*指向的对象中的值与*Exp*指向的值进行比较。如果值相等，则存储在*由原子*指向的对象中的值将替换为*Value，* 使用操作`read-modify-write`并应用*Order1*指定的内存顺序约束。 如果值不相等，则操作将*Exp*指向的值替换为存储在*Atom*指向的对象中的值，并应用*Order2*指定的内存顺序约束。

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

执行*弱原子比较和交换*操作。

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `Ty` 值的 `atomic` 对象的指针。

*Exp*\
指向类型 `Ty` 的值的指针。

*价值*\
一个 `Ty` 类型的值。

### <a name="return-value"></a>返回值

如果值相等，则**为 true，** 否则**为 false**。

### <a name="remarks"></a>备注

此方法执行具有隐式 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 参数的*弱原子比较和交换*操作。 有关详细信息，请参阅 [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)。

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

执行*弱原子比较和交换*操作。

```cpp
template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `Ty` 值的 `atomic` 对象的指针。

*Exp*\
指向类型 `Ty` 的值的指针。

*价值*\
一个 `Ty` 类型的值。

*订单1*\
第一个 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 参数。

*订单2*\
第二个 `memory_order` 参数。 *Order2*的值不能`memory_order_release`或`memory_order_acq_rel`，也不能比*Order1*的值强。

### <a name="return-value"></a>返回值

如果值相等，则**为 true，** 否则**为 false**。

### <a name="remarks"></a>备注

*原子比较和交换操作*的强弱味道都保证，如果预期值和当前值不相等，它们不会存储新值。 如果预期值和当前值相等，则强风味保证将存储新值。 弱味有时可能返回**false，** 并且即使当前值和预期值相等，也不会存储新值。 换句话说，函数将返回**false，** 但以后对预期值的检查可能会显示它没有变化，因此应该比较为相等。

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

使用*值*替换*Atom*的存储值。

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `Ty` 值的 `atomic` 对象的指针。

*价值*\
一个 `Ty` 类型的值。

### <a name="return-value"></a>返回值

交换前*Atom*的存储值。

### <a name="remarks"></a>备注

函数`atomic_exchange`执行一个`read-modify-write`操作，使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)将存储在*Atom*中的值与*值*交换。

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

将*Atom*的存储值替换为*值*。

```cpp
template <class Ty>
inline Ty atomic_exchange_explicit(
    volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_exchange_explicit(
    atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `Ty` 值的 `atomic` 对象的指针。

*价值*\
一个 `Ty` 类型的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

交换前*Atom*的存储值。

### <a name="remarks"></a>备注

函数`atomic_exchange_explicit`执行一个`read-modify-write`操作，在*Order*指定的内存约束中将存储在*Atom*中*的值与值*交换。

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

将值添加到 `atomic` 对象中存储的现有值。

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
一个指向 `atomic` 对象的指针，该对象存储指向类型 `T` 的指针。

*价值*\
一个 `ptrdiff_t` 类型的值。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的指针的值。

### <a name="remarks"></a>备注

函数`atomic_fetch_add`执行一个`read-modify-write`操作，使用`memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束在*原子*中以原子方式将*值*添加到存储的值。

当原子类型 为`atomic_address`时 *，值*具有类型`ptrdiff_t`，操作将存储的指针视为`char *`。

另外还将为整型类型重载该操作：

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a><a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

将值添加到 `atomic` 对象中存储的现有值。

```cpp
template <class T>
T* atomic_fetch_add_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_add_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
一个指向 `atomic` 对象的指针，该对象存储指向类型 `T` 的指针。

*价值*\
一个 `ptrdiff_t` 类型的值。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的指针的值。

### <a name="remarks"></a>备注

函数`atomic_fetch_add_explicit``read-modify-write`执行操作，在 指定的`Order`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束内，以原子方式将*值*添加到*Atom*中的存储值。

当原子类型为 `atomic_address` 时，`Value` 具有类型 `ptrdiff_t`，并且操作将存储指针视为 `char *`。

另外还将为整型类型重载该操作：

```cpp
integral atomic_fetch_add_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_add_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_and"></a><a name="atomic_fetch_and"></a>atomic_fetch_and

对某个值和存储在 `atomic` 对象中的一个现有值执行按位 `and`。

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `T` 值的 `atomic` 对象的指针。

*价值*\
一个 `T` 类型的值。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

函数`atomic_fetch_and`执行一个`read-modify-write`操作，使用`memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束将*Atom*的存储`and`*值*替换为值的位值和存储在*Atom*中的当前值。

## <a name="atomic_fetch_and_explicit"></a><a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

对某个值和存储在 `atomic` 对象中的一个现有值执行按位 `and`。

```cpp
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `T` 值的 `atomic` 对象的指针。

*价值*\
一个 `T` 类型的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

函数`atomic_fetch_and_explicit`执行一个`read-modify-write`操作，在*Order*指定的内存约束中，将`and`*Atom*的存储值替换为位*值*和存储在*Atom*中的当前值。

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

对某个值和存储在 `atomic` 对象中的一个现有值执行按位 `or`。

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `T` 值的 `atomic` 对象的指针。

*价值*\
一个 `T` 类型的值。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

函数`atomic_fetch_or`执行一个`read-modify-write`操作，使用`memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)将*Atom*的存储值`or`替换为位*值*和存储在*Atom*中的当前值。

## <a name="atomic_fetch_or_explicit"></a><a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

对某个值和存储在 `atomic` 对象中的一个现有值执行按位 `or`。

```cpp
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `T` 值的 `atomic` 对象的指针。

*价值*\
一个 `T` 类型的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

该`atomic_fetch_or_explicit`函数执行一`read-modify-write`个操作，在*Order*指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束内，将`or` *Atom*的存储值替换为位*值*和存储在*Atom*中的当前值。

## <a name="atomic_fetch_sub"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub

从 `atomic` 对象存储的现有值中减去一个值。

```cpp
template <class T>
T* atomic_fetch_sub(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;

template <class T>
T* atomic_fetch_sub(
    atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
一个指向 `atomic` 对象的指针，该对象存储指向类型 `T` 的指针。

*价值*\
一个 `ptrdiff_t` 类型的值。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的指针的值。

### <a name="remarks"></a>备注

函数`atomic_fetch_sub`使用`memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束`read-modify-write`执行一个操作，在*原子*中从存储的值中从存储值中从原子中从原子中从原子中从原子中减去*值*。

当原子类型 为`atomic_address`时 *，值*具有类型`ptrdiff_t`，操作将存储的指针视为`char *`。

另外还将为整型类型重载该操作：

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a><a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

从 `atomic` 对象存储的现有值中减去一个值。

```cpp
template <class T>
T* atomic_fetch_sub_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_sub_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value, memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
一个指向 `atomic` 对象的指针，该对象存储指向类型 `T` 的指针。

*价值*\
一个 `ptrdiff_t` 类型的值。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的指针的值。

### <a name="remarks"></a>备注

函数`atomic_fetch_sub_explicit`执行一个`read-modify-write`操作，在指定的`Order`memory_order约束内，在*Atom*中存储的值中从存储值中从原子中从原子中从存储值中从原子中从原子中从[原子](../standard-library/atomic-enums.md#memory_order_enum)中减去*值*。

当原子类型 为`atomic_address`时 *，值*具有类型`ptrdiff_t`，操作将存储的指针视为`char *`。

另外还将为整型类型重载该操作：

```cpp
integral atomic_fetch_sub_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_sub_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_xor"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor

对某个值和存储在 `atomic` 对象中的一个现有值执行按位 `exclusive or`。

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `T` 值的 `atomic` 对象的指针。

*价值*\
一个 `T` 类型的值。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

函数`atomic_fetch_xor`执行一个`read-modify-write`操作，使用`memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)将*Atom*的存储值`exclusive or`替换为位*值*和存储在*Atom*中的当前值。

## <a name="atomic_fetch_xor_explicit"></a><a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

对某个值和存储在 `atomic` 对象中的一个现有值执行按位 `exclusive or`。

```cpp
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `T` 值的 `atomic` 对象的指针。

*价值*\
一个 `T` 类型的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

函数`atomic_fetch_xor_explicit`执行一个`read-modify-write`操作，在*Order*指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束中，将`exclusive or`*Atom*的存储值替换为位*值*和存储在*Atom*中的当前值。

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

将[atomic_flag](../standard-library/atomic-flag-structure.md)对象中的**bool**标志memory_order 中[memory_order](../standard-library/atomic-enums.md#memory_order_enum)`memory_order_seq_cst`设置为**false。**

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>参数

*国旗*\
指向 `atomic_flag` 对象的指针。

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

在指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束中，将[atomic_flag](../standard-library/atomic-flag-structure.md)对象中的**bool**标志设置为**false。**

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*国旗*\
指向 `atomic_flag` 对象的指针。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

在`memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)的约束下，将[atomic_flag](../standard-library/atomic-flag-structure.md)对象中的**bool**标志设置**为 true。**

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>参数

*国旗*\
指向 `atomic_flag` 对象的指针。

### <a name="return-value"></a>返回值

*标志*的初始值 。

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

在指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束中，将[atomic_flag](../standard-library/atomic-flag-structure.md)对象中的**bool**标志设置为**true。**

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*国旗*\
指向 `atomic_flag` 对象的指针。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

*标志*的初始值 。

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

设置 `atomic` 对象中存储的值。

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `Ty` 值的 `atomic` 对象的指针。

*价值*\
一个 `Ty` 类型的值。

### <a name="remarks"></a>备注

`atomic_init` 不是一个原子操作。 不是线程安全的。

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a>atomic_is_lock_free

指定对 `atomic` 对象执行的原子操作是否为*无锁*。

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向存储类型 `T` 值的 `atomic` 对象的指针。

### <a name="return-value"></a>返回值

如果*原子*上的原子操作是无锁的，**则为 true;** 否则，**假**。

### <a name="remarks"></a>备注

如果对该类型执行的原子操作都没有使用锁，则原子类型为无锁。 如果此函数返回 true，则类型可以安全地在信号处理程序中使用。

## <a name="atomic_load"></a><a name="atomic_load"></a>atomic_load

检索 `atomic` 对象中存储的值。

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向包含 `Ty` 类型值的 `atomic` 对象的指针。

### <a name="return-value"></a>返回值

存储在*Atom*中检索的值。

### <a name="remarks"></a>备注

`atomic_load` 隐式使用 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a>atomic_load_explicit

检索 `atomic` 对象中存储的值（限于指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum)）。

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向包含 `Ty` 类型值的 `atomic` 对象的指针。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 不要使用 `memory_order_release` 或 `memory_order_acq_rel`。

### <a name="return-value"></a>返回值

存储在*Atom*中检索的值。

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

充当调用线程中信号处理程序在同一线程中执行的其他 fence 之间的 *fence*（强制在加载/存储操作之间进行排序的内存同步基元）。

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*以*\
确定 fence 类型的内存排序约束。

### <a name="remarks"></a>备注

*Order*参数确定围栏类型。

|||
|-|-|
|`memory_order_relaxed`|fence 不起作用。|
|`memory_order_consume`|fence 为 acquire fence。|
|`memory_order_acquire`|fence 为 acquire fence。|
|`memory_order_release`|fence 为 release fence。|
|`memory_order_acq_rel`|fence 既是 acquire fence 也是 release fence。|
|`memory_order_seq_cst`|fence 既是 acquire fence 也是 release fence，并且在顺序上保持一致。|

## <a name="atomic_store"></a><a name="atomic_store"></a>atomic_store

自动将值存储到原子对象中。

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向包含 `Ty` 类型值的原子对象的指针。

*价值*\
一个 `Ty` 类型的值。

### <a name="remarks"></a>备注

`atomic_store`在`memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束中存储*Atom*指向的对象中*的值*。

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a>atomic_store_explicit

自动将值存储到原子对象中。

```cpp
template <class Ty>
inline Ty atomic_store_explicit(
    const volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_store_explicit(
    const atomic<Ty>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*原子*\
指向包含 `Ty` 类型值的 `atomic` 对象的指针。

*价值*\
一个 `Ty` 类型的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 请勿使用 `memory_order_consume`、`memory_order_acquire` 或 `memory_order_acq_rel`。

### <a name="remarks"></a>备注

`atomic_store`在*Atom*指向的对象中存储*值*，在*Order*`memory_order`指定的 对象中。

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

充当 *fence* — 是强制在加载/存储操作之间进行排序的内存同步基元，没有关联的原子操作。

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*以*\
确定 fence 类型的内存排序约束。

### <a name="remarks"></a>备注

*Order*参数确定围栏类型。

|||
|-|-|
|`memory_order_relaxed`|fence 不起作用。|
|`memory_order_consume`|fence 为 acquire fence。|
|`memory_order_acquire`|fence 为 acquire fence。|
|`memory_order_release`|fence 为 release fence。|
|`memory_order_acq_rel`|fence 既是 acquire fence 也是 release fence。|
|`memory_order_seq_cst`|fence 既是 acquire fence 也是 release fence，并且在顺序上保持一致。|

## <a name="kill_dependency"></a><a name="kill_dependency"></a>kill_dependency

删除依赖关系。

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>参数

*精 氨 酸*\
一个 `Ty` 类型的值。

### <a name="return-value"></a>返回值

返回值为*Arg*。 *Arg*的评估不依赖于函数调用。 通过中断可能的依赖关系链，该函数可能允许编译器生成更高效的代码。

## <a name="see-also"></a>另请参阅

[\<原子>](../standard-library/atomic.md)
