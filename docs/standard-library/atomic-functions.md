---
title: '&lt;atomic&gt; 函数 | Microsoft 文档'
ms.custom: ''
ms.date: 07/11/2018
ms.topic: reference
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
author: mikeblome
ms.author: mblome
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
ms.workload:
- cplusplus
ms.openlocfilehash: df0c7ea332cda65aa3621de581eb39419ee9b9d4
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39028312"
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

## <a name="atomic_compare_exchange_strong"></a>  atomic_compare_exchange_strong

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

*Atom*指向的指针*原子*对象，它存储类型的值`Ty`。

*Exp*指向类型的值的指针`Ty`。

*值*类型的值`Ty`。

### <a name="return-value"></a>返回值

**true**值是否相等，否则**false**。

### <a name="remarks"></a>备注

此方法使用隐式 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 参数执行原子比较和交换操作。 有关详细信息，请参阅 [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)。

## <a name="atomic_compare_exchange_strong_explicit"></a>  atomic_compare_exchange_strong_explicit

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

*Atom*指向的指针`atomic`对象，它存储类型的值`Ty`。

*Exp*指向类型的值的指针`Ty`。

*值*类型的值`Ty`。

*顺序排列 1*第一个[memory_order](../standard-library/atomic-enums.md#memory_order_enum)参数。

*Order2*第二个`memory_order`参数。 值*Order2*不能`memory_order_release`或`memory_order_acq_rel`，它不能比的值更强*顺序排列 1*。

### <a name="return-value"></a>返回值

**true**值是否相等，否则**false**。

### <a name="remarks"></a>备注

*原子比较和交换操作*所指向的对象中存储的值进行比较*Atom*与所指向的值*Exp*。如果值相等，所指向的对象中存储的值*atom*替换为`Val`使用`read-modify-write`操作和应用的内存顺序约束所指定的*顺序排列 1*。 如果值不相等，该操作将替换所指向的值*Exp*所指向的对象中存储的值与*Atom* ，并将应用的内存顺序约束的通过指定*Order2*。

## <a name="atomic_compare_exchange_weak"></a>  atomic_compare_exchange_weak

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

*Atom*指向的指针`atomic`对象，它存储类型的值`Ty`。

*Exp*指向类型的值的指针`Ty`。

*值*类型的值`Ty`。

### <a name="return-value"></a>返回值

**true**值是否相等，否则**false**。

### <a name="remarks"></a>备注

此方法执行具有隐式 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 参数的*弱原子比较和交换*操作。 有关详细信息，请参阅 [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)。

## <a name="atomic_compare_exchange_weak_explicit"></a>  atomic_compare_exchange_weak_explicit

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

*Atom*指向的指针`atomic`对象，它存储类型的值`Ty`。

*Exp*指向类型的值的指针`Ty`。

*值*类型的值`Ty`。

*顺序排列 1*第一个[memory_order](../standard-library/atomic-enums.md#memory_order_enum)参数。

*Order2*第二个`memory_order`参数。 值*Order2*不能`memory_order_release`或`memory_order_acq_rel`，也不能比的值更强*顺序排列 1*。

### <a name="return-value"></a>返回值

**true**值是否相等，否则**false**。

### <a name="remarks"></a>备注

强和弱风格*原子比较和交换操作*保证它们是否存储新值，如果预期的和当前值是否不相等。 强类型保证，它将存储的新值，如果预期的和当前值相等。 有时可能会返回弱风格**false**并不存储新值，即使当前和预期值是否相等。 换而言之，该函数将返回**false**，但它未更改，并因此应具有相等比较，可能会显示对所需的值的更高版本检查。

## <a name="atomic_exchange"></a>  atomic_exchange

使用*值*的存储的值替换*Atom*。

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向的指针`atomic`对象，它存储类型的值`Ty`。

*值*类型的值`Ty`。

### <a name="return-value"></a>返回值

存储的值*Atom*交换前。

### <a name="remarks"></a>备注

`atomic_exchange`函数执行`read-modify-write`操作来交换中存储的值*Atom*与*值*，并使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a>  atomic_exchange_explicit

替换存储的值*Atom*与*值*。

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

*Atom*指向的指针`atomic`对象，它存储类型的值`Ty`。

*值*类型的值`Ty`。

*顺序*A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

存储的值*Atom*交换前。

### <a name="remarks"></a>备注

`atomic_exchange_explicit`函数执行`read-modify-write`操作来交换中存储的值*Atom*与*值*，由指定的内存约束内*顺序*。

## <a name="atomic_fetch_add"></a>  atomic_fetch_add

将值添加到 `atomic` 对象中存储的现有值。

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向的指针`atomic`对象，它存储指向类型的指针`T`。

*值*类型的值`ptrdiff_t`。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的指针的值。

### <a name="remarks"></a>备注

`atomic_fetch_add`函数执行`read-modify-write`操作以原子方式将添加*值*中存储的值为*Atom*，并使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束。

当原子类型是`atomic_address`，*值*具有类型`ptrdiff_t`并且该操作将存储的指针视为`char *`。

另外还将为整型类型重载该操作：

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a>  atomic_fetch_add_explicit

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

*Atom*指向的指针`atomic`对象，它存储指向类型的指针`T`。

*值*类型的值`ptrdiff_t`。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的指针的值。

### <a name="remarks"></a>备注

`atomic_fetch_add_explicit`函数执行`read-modify-write`操作以原子方式将添加*值*中存储的值为*Atom*，在[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束由指定的`Order`。

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

## <a name="atomic_fetch_and"></a>  atomic_fetch_and

对某个值和存储在 `atomic` 对象中的一个现有值执行按位 `and`。

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向的指针`atomic`对象，它存储类型的值`T`。

*值*类型的值`T`。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

`atomic_fetch_and`函数执行`read-modify-write`操作的存储的值替换*Atom*的按位`and`的*值*中存储的当前值和*Atom*，并使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束。

## <a name="atomic_fetch_and_explicit"></a>  atomic_fetch_and_explicit

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

*Atom*指向的指针`atomic`对象，它存储类型的值`T`。

*值*类型的值`T`。

*顺序*A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

`atomic_fetch_and_explicit`函数执行`read-modify-write`操作的存储的值替换*Atom*的按位`and`的*值*中存储的当前值和*Atom*，由指定的内存约束内*顺序*。

## <a name="atomic_fetch_or"></a>  atomic_fetch_or

对某个值和存储在 `atomic` 对象中的一个现有值执行按位 `or`。

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向的指针`atomic`对象，它存储类型的值`T`。

*值*类型的值`T`。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

`atomic_fetch_or`函数执行`read-modify-write`操作的存储的值替换*Atom*的按位`or`的*值*中存储的当前值和*Atom*，并使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_fetch_or_explicit"></a>  atomic_fetch_or_explicit

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

*Atom*指向的指针`atomic`对象，它存储类型的值`T`。

*值*类型的值`T`。

*顺序*A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

`atomic_fetch_or_explicit`函数执行`read-modify-write`操作的存储的值替换*Atom*的按位`or`的*值*中存储的当前值和*Atom*，在[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束指定*顺序*。

## <a name="atomic_fetch_sub"></a>  atomic_fetch_sub

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

*Atom*指向的指针`atomic`对象，它存储指向类型的指针`T`。

*值*类型的值`ptrdiff_t`。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的指针的值。

### <a name="remarks"></a>备注

`atomic_fetch_sub`函数执行`read-modify-write`操作以原子方式减去*值*中存储的值从*Atom*，并使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束。

当原子类型是`atomic_address`，*值*具有类型`ptrdiff_t`并且该操作将存储的指针视为`char *`。

另外还将为整型类型重载该操作：

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a>  atomic_fetch_sub_explicit

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

*Atom*指向的指针`atomic`对象，它存储指向类型的指针`T`。

*值*类型的值`ptrdiff_t`。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的指针的值。

### <a name="remarks"></a>备注

`atomic_fetch_sub_explicit`函数执行`read-modify-write`操作以原子方式减去*值*中存储的值从*Atom*，在[memory_order](../standard-library/atomic-enums.md#memory_order_enum)通过指定约束`Order`。

当原子类型是`atomic_address`，*值*具有类型`ptrdiff_t`并且该操作将存储的指针视为`char *`。

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

## <a name="atomic_fetch_xor"></a>  atomic_fetch_xor

对某个值和存储在 `atomic` 对象中的一个现有值执行按位 `exclusive or`。

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向的指针`atomic`对象，它存储类型的值`T`。

*值*类型的值`T`。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

`atomic_fetch_xor`函数执行`read-modify-write`操作的存储的值替换*Atom*的按位`exclusive or`的*值*中存储的当前值和*Atom*，并使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_fetch_xor_explicit"></a>  atomic_fetch_xor_explicit

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

*Atom*指向的指针`atomic`对象，它存储类型的值`T`。

*值*类型的值`T`。

*顺序*A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

执行该操作之前的原子对象包含的值。

### <a name="remarks"></a>备注

`atomic_fetch_xor_explicit`函数执行`read-modify-write`操作的存储的值替换*Atom*的按位`exclusive or`的*值*中存储的当前值和*Atom*，在[memory_order](../standard-library/atomic-enums.md#memory_order_enum)由指定的约束*顺序*。

## <a name="atomic_flag_clear"></a>  atomic_flag_clear

集**bool**中的标志[atomic_flag](../standard-library/atomic-flag-structure.md)对象传递给**false**，在`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>参数

*标志*指向的`atomic_flag`对象。

## <a name="atomic_flag_clear_explicit"></a>  atomic_flag_clear_explicit

集**bool**中的标志[atomic_flag](../standard-library/atomic-flag-structure.md)对象传递给**false**，在指定[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束。

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*标志*指向的`atomic_flag`对象。

*顺序*A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_flag_test_and_set"></a>  atomic_flag_test_and_set

集**bool**中的标志[atomic_flag](../standard-library/atomic-flag-structure.md)对象传递给**true**的约束内`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>参数

*标志*指向的`atomic_flag`对象。

### <a name="return-value"></a>返回值

初始值*标志*。

## <a name="atomic_flag_test_and_set_explicit"></a>  atomic_flag_test_and_set_explicit

集**bool**中的标记[atomic_flag](../standard-library/atomic-flag-structure.md)对象传递给**true**，在指定[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束。

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*标志*指向的`atomic_flag`对象。

*顺序*A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

初始值*标志*。

## <a name="atomic_init"></a>  atomic_init

设置 `atomic` 对象中存储的值。

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向的指针`atomic`对象，它存储类型的值`Ty`。

*值*类型的值`Ty`。

### <a name="remarks"></a>备注

`atomic_init` 不是一个原子操作。 不是线程安全的。

## <a name="atomic_is_lock_free"></a>  atomic_is_lock_free

指定对 `atomic` 对象执行的原子操作是否为*无锁*。

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向的指针`atomic`对象，它存储类型的值`T`。

### <a name="return-value"></a>返回值

**true**如果对原子操作*Atom*无锁; 否则为**false**。

### <a name="remarks"></a>备注

如果对该类型执行的原子操作都没有使用锁，则原子类型为无锁。 如果此函数返回 true，则类型可以安全地在信号处理程序中使用。

## <a name="atomic_load"></a>  atomic_load

检索 `atomic` 对象中存储的值。

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向的指针`atomic`对象，其中包含类型的值`Ty`。

### <a name="return-value"></a>返回值

检索到的值存储在*Atom*。

### <a name="remarks"></a>备注

`atomic_load` 隐式使用 `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_load_explicit"></a>  atomic_load_explicit

检索 `atomic` 对象中存储的值（限于指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum)）。

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向的指针`atomic`对象，其中包含类型的值`Ty`。

*顺序*A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 不要使用 `memory_order_release` 或 `memory_order_acq_rel`。

### <a name="return-value"></a>返回值

检索到的值存储在*Atom*。

## <a name="atomic_signal_fence"></a>  atomic_signal_fence

充当调用线程中信号处理程序在同一线程中执行的其他 fence 之间的 *fence*（强制在加载/存储操作之间进行排序的内存同步基元）。

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*顺序*的内存排序约束确定 fence 类型。

### <a name="remarks"></a>备注

*顺序*参数确定 fence 类型。

|||
|-|-|
|`memory_order_relaxed`|fence 不起作用。|
|`memory_order_consume`|fence 为 acquire fence。|
|`memory_order_acquire`|fence 为 acquire fence。|
|`memory_order_release`|fence 为 release fence。|
|`memory_order_acq_rel`|fence 既是 acquire fence 也是 release fence。|
|`memory_order_seq_cst`|fence 既是 acquire fence 也是 release fence，并且在顺序上保持一致。|

## <a name="atomic_store"></a>  atomic_store

自动将值存储到原子对象中。

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>参数

*Atom*指向一个包含类型的值的原子对象的指针`Ty`。

*值*类型的值`Ty`。

### <a name="remarks"></a>备注

`atomic_store` 将存储*值*所指向的对象中*Atom*，在`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束。

## <a name="atomic_store_explicit"></a>  atomic_store_explicit

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

*Atom*指向的指针`atomic`对象，其中包含类型的值`Ty`。

*值*类型的值`Ty`。

*顺序*A [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 请勿使用 `memory_order_consume`、`memory_order_acquire` 或 `memory_order_acq_rel`。

### <a name="remarks"></a>备注

`atomic_store` 将存储*值*所指向的对象中*Atom*，在`memory_order`由指定*顺序*。

## <a name="atomic_thread_fence"></a>  atomic_thread_fence

充当 *fence* — 是强制在加载/存储操作之间进行排序的内存同步基元，没有关联的原子操作。

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>参数

*顺序*的内存排序约束确定 fence 类型。

### <a name="remarks"></a>备注

*顺序*参数确定 fence 类型。

|||
|-|-|
|`memory_order_relaxed`|fence 不起作用。|
|`memory_order_consume`|fence 为 acquire fence。|
|`memory_order_acquire`|fence 为 acquire fence。|
|`memory_order_release`|fence 为 release fence。|
|`memory_order_acq_rel`|fence 既是 acquire fence 也是 release fence。|
|`memory_order_seq_cst`|fence 既是 acquire fence 也是 release fence，并且在顺序上保持一致。|

## <a name="kill_dependency"></a>  kill_dependency

删除依赖关系。

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>参数

*Arg*类型的值`Ty`。

### <a name="return-value"></a>返回值

返回值是*Arg*。 评估*Arg*不会延续到函数调用的依赖项。 通过中断可能的依赖关系链，该函数可能允许编译器生成更高效的代码。

## <a name="see-also"></a>请参阅

[\<atomic>](../standard-library/atomic.md)<br/>
