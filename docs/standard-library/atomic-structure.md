---
title: atomic 结构
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 8701078f8a034d80dae41eee0d842fb15fd8d3a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203930"
---
# <a name="atomic-structure"></a>atomic 结构

描述一个对象，该对象对*Ty*类型的存储值执行原子操作。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>成员

|成员|描述|
|----------|-----------------|
|**构造函数**||
|[原子 (atomic)](#atomic)|构造一个原子对象。|
|**运算符**||
|[原子：： operator Ty](#op_ty)|读取并返回存储的值。 （[原子：： load](#load)）|
|[原子：： operator =](#op_eq)|使用指定值替换存储值。 （[原子：：存储](#store)）|
|[原子：： operator + +](#op_inc)|增加存储值。 仅由整型和指针专用化使用。|
|[原子：： operator + =](#op_add_eq)|将指定的值添加到存储值。 仅由整型和指针专用化使用。|
|[原子：： operator--](#op_dec)|减小存储值。 仅由整型和指针专用化使用。|
|[原子：： operator-=](#op_sub_eq)|从存储值减去指定的值。 仅由整型和指针专用化使用。|
|[原子：： operator&=](#op_and_eq)|对指定值和存储值执行按位 "与"。 仅由整型专用化使用。|
|[原子：： operator&#124;=](#op_or_eq)|对指定值和存储值执行按位 "或"。 仅由整型专用化使用。|
|[原子：： operator ^ =](#op_xor_eq)|对指定值和存储值执行按位 "异或" 运算。 仅由整型专用化使用。|
|**函数**||
|[compare_exchange_strong](#compare_exchange_strong)|对执行*atomic_compare_and_exchange*操作 **`this`** 并返回结果。|
|[compare_exchange_weak](#compare_exchange_weak)|对执行*weak_atomic_compare_and_exchange*操作 **`this`** 并返回结果。|
|[fetch_add](#fetch_add)|将指定的值添加到存储值。|
|[fetch_and](#fetch_and)|对指定值和存储值执行按位 "与"。|
|[fetch_or](#fetch_or)|对指定值和存储值执行按位 "或"。|
|[fetch_sub](#fetch_sub)|从存储值减去指定的值。|
|[fetch_xor](#fetch_xor)|对指定值和存储值执行按位 "异或" 运算。|
|[is_lock_free](#is_lock_free)|指定上的原子操作是否 **`this`** 为*无锁*。 如果对类型执行的原子操作都没有使用锁，则原子类型为*无锁*。|
|[加载](#load)|读取并返回存储的值。|
|[存储](#store)|使用指定值替换存储值。|

## <a name="remarks"></a>备注

类型*Ty*必须是*完全复制*。 也就是说，使用[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)复制其字节必须生成一个与原始对象相等的有效*Ty*对象。 [Compare_exchange_weak](#compare_exchange_weak)和[compare_exchange_strong](#compare_exchange_strong)成员函数使用[Memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)来确定两个*Ty*值是否相等。 这些函数不会使用*Ty*定义的 `operator==` 。 的成员函数 `atomic` ，用于 `memcpy` 复制*Ty*类型的值。

所有指针类型都存在部分专用化**原子 \<Ty \*> **性。 通过专用化可将偏移量添加到托管的指针值或者从其中减去该偏移量。 算术运算采用类型为的参数 `ptrdiff_t` ，并根据*Ty*的大小调整该参数，使其与普通地址算法保持一致。

除了之外，每个整数类型都存在专用化 **`bool`** 。 每个专用化为原子算术和逻辑运算提供了一组丰富的方法。

||||
|-|-|-|
|**原子 (atomic)\<char>**|**原子 (atomic)\<signed char>**|**原子 (atomic)\<unsigned char>**|
|**原子 (atomic)\<char16_t>**|**原子 (atomic)\<char32_t>**|**原子 (atomic)\<wchar_t>**|
|**原子 (atomic)\<short>**|**原子 (atomic)\<unsigned short>**|**原子 (atomic)\<int>**|
|**原子 (atomic)\<unsigned int>**|**原子 (atomic)\<long>**|**原子 (atomic)\<unsigned long>**|
|**原子 (atomic)\<long long>**|**原子 (atomic)\<unsigned long long>**|

整型专用化派生自相应的 `atomic_integral` 类型。 例如，**原子 \<unsigned int> **派生自 `atomic_uint` 。

## <a name="requirements"></a>要求

**标头：**\<atomic>

**命名空间:** std

## <a name="atomicatomic"></a><a name="atomic"></a>原子：：原子

构造一个原子对象。

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
初始化值。

### <a name="remarks"></a>备注

不能复制或移动原子对象。

作为原子的实例化的对象只能 \<*Ty*> 通过采用*Ty*类型的参数的构造函数进行初始化，而不能通过使用聚合初始化来进行初始化。 但 atomic_integral 对象只能使用聚合初始化来初始化。

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="atomicoperator-ty"></a><a name="op_ty"></a>原子：： operator *Ty*

指定给模板 "原子" 的类型的运算符 \<*Ty*> 。 检索** \* 此**中存储的值。

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>备注

此运算符应用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator"></a><a name="op_eq"></a>原子：： operator =

存储指定值。

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
一个*Ty*对象。

### <a name="return-value"></a>返回值

返回*值*。

## <a name="atomicoperator"></a><a name="op_inc"></a>原子：： operator + +

增加存储值。 仅由整型和指针专用化使用。

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>返回值

前两个运算符返回递增的值;最后两个运算符在增量之前返回值。 运算符使用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator"></a><a name="op_add_eq"></a>原子：： operator + =

将指定的值添加到存储值。 仅由整型和指针专用化使用。

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
整数或指针值。

### <a name="return-value"></a>返回值

包含加法结果的*Ty*对象。

### <a name="remarks"></a>备注

此运算符使用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator--"></a><a name="op_dec"></a>原子：： operator--

减小存储值。 仅由整型和指针专用化使用。

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>返回值

前两个运算符返回递减的值;最后两个运算符返回减量前的值。 运算符使用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator-"></a><a name="op_sub_eq"></a>原子：： operator-=

从存储值减去指定的值。 仅由整型和指针专用化使用。

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
整数或指针值。

### <a name="return-value"></a>返回值

一个包含减法结果的*Ty*对象。

### <a name="remarks"></a>备注

此运算符使用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator"></a><a name="op_and_eq"></a>原子：： operator&=

对指定值和** \* 此**的存储值执行按位 "与"。 仅由整型专用化使用。

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
*Ty*类型的值。

### <a name="return-value"></a>返回值

按位 "与" 的结果。

### <a name="remarks"></a>备注

此运算符执行读修改-写操作，将** \* 此**存储的值替换为*值*的按位 "与" 的值，并在 memory_order 的约束内替换** \* 此**中存储的当前值 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator124"></a><a name="op_or_eq"></a>原子：： operator&#124;=

对指定值和** \* 此**的存储值执行按位 "或"。 仅由整型专用化使用。

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
*Ty*类型的值。

### <a name="return-value"></a>返回值

按位 "或" 的结果。

### <a name="remarks"></a>备注

此运算符执行读修改-写操作，将** \* 此**存储的值替换为*值*的按位 "或"，并在 memory_order 约束的约束内存储在** \* 此**中的当前值 `memory_order_seq_cst` [memory_order](atomic-enums.md) 。

## <a name="atomicoperator"></a><a name="op_xor_eq"></a>原子：： operator ^ =

对指定的值和** \* 此**的存储值执行按位 "异或" 运算。 仅由整型专用化使用。

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
*Ty*类型的值。

### <a name="return-value"></a>返回值

按位 "异或" 的结果。

### <a name="remarks"></a>备注

此运算符执行读修改-写操作，将** \* 此**存储的值替换为按位 "异或"*值*以及在** \* 此**中存储的当前值（在 `memory_order_seq_cst` [memory_order](atomic-enums.md)约束的约束内）。

## <a name="atomiccompare_exchange_strong"></a><a name="compare_exchange_strong"></a>原子：： compare_exchange_strong

对** \* 此**执行原子比较和交换操作。

```cpp
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>参数

*.Exp*\
*Ty*类型的值。

*负值*\
*Ty*类型的值。

*Order1*\
第一个 `memory_order` 参数。

*Order2*\
第二个 `memory_order` 参数。

### <a name="return-value"></a>返回值

**`bool`** 指示值比较的结果的。

### <a name="remarks"></a>备注

此原子比较和交换操作将** \* 此**中存储的值与*Exp*进行比较。如果值相等，则操作将使用读修改写操作替换存储在** \* 此**中*的值*，并应用*Order1*指定的内存顺序约束。 如果值不相等，则操作将使用存储在** \* 此**中的值来替换*Exp* ，并应用*Order2*指定的内存顺序约束。

没有第二个重载的重载 `memory_order` 使用基于*Order1*值的隐式*Order2* 。 如果*Order1*为 `memory_order_acq_rel` ，则*Order2*为 `memory_order_acquire` 。 如果*Order1*为 `memory_order_release` ，则*Order2*为 `memory_order_relaxed` 。 在所有其他情况下， *Order2*等于*Order1*。

对于采用两个参数的重载 `memory_order` ， *Order2*的值不能为 `memory_order_release` 或 `memory_order_acq_rel` ，且不得大于*Order1*的值。

## <a name="atomiccompare_exchange_weak"></a><a name="compare_exchange_weak"></a>原子：： compare_exchange_weak

对** \* 此**执行弱原子比较和交换操作。

```cpp
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>参数

*.Exp*\
*Ty*类型的值。

*负值*\
*Ty*类型的值。

*Order1*\
第一个 `memory_order` 参数。

*Order2*\
第二个 `memory_order` 参数。

### <a name="return-value"></a>返回值

**`bool`** 指示值比较的结果的。

### <a name="remarks"></a>备注

此原子比较和交换操作将** \* 此**中存储的值与*Exp*进行比较。如果值相等，则操作将使用读修改写操作替换存储在** \* 此**中*的值*，并应用*Order1*指定的内存顺序约束。 如果值不相等，则操作将使用存储在** \* 此**中的值来替换*Exp* ，并应用*Order2*指定的内存顺序约束。

如果所比较的值相等，一个弱原子比较和交换操作将执行交换。 如果值不相等，则不保证操作执行交换。

没有第二个重载的重载 `memory_order` 使用基于*Order1*值的隐式*Order2* 。 如果*Order1*为 `memory_order_acq_rel` ，则*Order2*为 `memory_order_acquire` 。 如果*Order1*为 `memory_order_release` ，则*Order2*为 `memory_order_relaxed` 。 在所有其他情况下， *Order2*等于*Order1*。

对于采用两个参数的重载 `memory_order` ， *Order2*的值不能为 `memory_order_release` 或 `memory_order_acq_rel` ，且不得大于*Order1*的值。

## <a name="atomicexchange"></a><a name="exchange"></a>原子：： exchange

使用指定的值替换** \* 此**的存储值。

```cpp
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
*Ty*类型的值。

*为了*\
`memory_order`。

### <a name="return-value"></a>返回值

交换** \* 前的存储的值**。

### <a name="remarks"></a>备注

此操作在按*顺序*指定的内存约束内执行读修改-写操作，以使用*值*替换存储在** \* 此**中的值。

## <a name="atomicfetch_add"></a><a name="fetch_add"></a>原子：： fetch_add

提取存储在** \* 此**中的值，然后将指定的值添加到存储的值。

```cpp
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
*Ty*类型的值。

*为了*\
`memory_order`。

### <a name="return-value"></a>返回值

一个*Ty*对象，该对象包含在添加之前存储在** \* 此**中的值。

### <a name="remarks"></a>备注

`fetch_add`方法执行读修改-写操作，以原子方式向** \* 此**中存储的值添加*值*，并应用按*顺序*指定的内存约束。

## <a name="atomicfetch_and"></a><a name="fetch_and"></a>原子：： fetch_and

对值和存储在** \* 此**中的现有值执行按位 "与"。

```cpp
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
*Ty*类型的值。

*为了*\
`memory_order`。

### <a name="return-value"></a>返回值

一个*Ty*对象，它包含按位 "与" 的结果。

### <a name="remarks"></a>备注

`fetch_and`方法执行读修改-写操作，将** \* 此**存储的值替换为按*顺序*指定的内存约束中的按位 "与"*值*和当前** \* **值。

## <a name="atomicfetch_or"></a><a name="fetch_or"></a>原子：： fetch_or

对值和存储在** \* 此**中的现有值执行按位 "或"。

```cpp
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
*Ty*类型的值。

*为了*\
`memory_order`。

### <a name="return-value"></a>返回值

一个*Ty*对象，它包含按位 "或" 的结果。

### <a name="remarks"></a>备注

`fetch_or`方法执行读修改-写操作，将** \* 此**存储的值替换为按*顺序*指定的内存约束中的按位 "或"*值*和当前** \* **值。

## <a name="atomicfetch_sub"></a><a name="fetch_sub"></a>原子：： fetch_sub

从存储值减去指定的值。

```cpp
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
*Ty*类型的值。

*为了*\
`memory_order`。

### <a name="return-value"></a>返回值

一个包含减法结果的*Ty*对象。

### <a name="remarks"></a>备注

`fetch_sub`方法执行读修改-写操作，以原子** \* 方式在按***顺序*指定的内存约束内从存储的值中减去*值*。

## <a name="atomicfetch_xor"></a><a name="fetch_xor"></a>原子：： fetch_xor

对值和存储在** \* 此**中的现有值执行按位 "异或" 运算。

```cpp
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
*Ty*类型的值。

*为了*\
`memory_order`。

### <a name="return-value"></a>返回值

一个*Ty*对象，它包含按位 "异或" 的结果。

### <a name="remarks"></a>备注

`fetch_xor`方法执行读修改写操作，将** \* 此**存储的值替换为按位 "异或"*值*和存储在** \* 此**中的当前值，并应用按*顺序*指定的内存约束。

## <a name="atomicis_lock_free"></a><a name="is_lock_free"></a>原子：： is_lock_free

指定对** \* 此**的原子操作是否为无锁。

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>返回值

如果对** \* 此**的原子操作是无锁的，则为 true; 否则为 false。

### <a name="remarks"></a>备注

如果对类型执行的原子操作都没有使用锁，则原子类型为无锁。

## <a name="atomicload"></a><a name="load"></a>原子：： load

在指定的内存约束内检索** \* 此**中存储的值。

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>参数

*为了*\
`memory_order`。 *订单*不得为 `memory_order_release` 或 `memory_order_acq_rel` 。

### <a name="return-value"></a>返回值

** \* 此**中存储的检索值。

## <a name="atomicstore"></a><a name="store"></a>原子：：存储

存储指定值。

```cpp
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>参数

*负值*\
一个*Ty*对象。

*为了*\
一个 `memory_order` 约束。

### <a name="remarks"></a>备注

此成员函数以原子*Value*方式在按 **`*this`** *顺序*指定的内存约束中存储值。

## <a name="see-also"></a>另请参阅

[\<atomic>](../standard-library/atomic.md)\
[头文件引用](../standard-library/cpp-standard-library-header-files.md)
