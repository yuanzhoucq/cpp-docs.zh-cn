---
title: atomic 结构 | Microsoft 文档
ms.custom: ''
ms.date: 04/20/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- atomic/std::atomic
dev_langs:
- C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 298fe2751cf25355e2075a2870c34bf17cedc222
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="atomic-structure"></a>atomic 结构

描述执行对存储的值的类型执行原子操作的对象*Ty*。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>成员

|成员|描述|
|----------|-----------------|
|**构造函数**||
|[atomic](#atomic)|构造一个原子对象。|
|**运算符**||
|[atomic:: operator Ty](#op_ty)|读取并返回存储的值。 ([atomic::load](#load))|
|[atomic:: operator =](#op_eq)|使用指定值替换存储值。 ([atomic::store](#store))|
|[atomic:: operator + +](#op_inc)|增加存储值。 仅由整型和指针专用化使用。|
|[atomic:: operator + =](#op_add_eq)|将指定的值添加到存储值。 仅由整型和指针专用化使用。|
|[atomic:: operator-](#op_dec)|减小存储值。 仅由整型和指针专用化使用。|
|[atomic:: operator =](#op_sub_eq)|从存储值减去指定的值。 仅由整型和指针专用化使用。|
|[atomic:: operator & =](#op_and_eq)|执行按位在指定的值和存储的值上。 仅由整型专用化使用。|
|[atomic:: operator&#124;=](#op_or_eq)|执行按位或上指定的值和存储的值。 仅由整型专用化使用。|
|[atomic:: operator ^ =](#op_xor_eq)|执行按位异或上指定的值和存储的值。 仅由整型专用化使用。|
|**函数**||
|[compare_exchange_strong](#compare_exchange_strong)|执行*atomic_compare_and_exchange*操作**这**并返回结果。|
|[compare_exchange_weak](#compare_exchange_weak)|执行*weak_atomic_compare_and_exchange*操作**这**并返回结果。|
|[fetch_add](#fetch_add)|将指定的值添加到存储值。|
|[fetch_and](#fetch_and)|执行按位在指定的值和存储的值上。|
|[fetch_or](#fetch_or)|执行按位或上指定的值和存储的值。|
|[fetch_sub](#fetch_sub)|从存储值减去指定的值。|
|[fetch_xor](#fetch_xor)|执行按位异或上指定的值和存储的值。|
|[is_lock_free](#is_lock_free)|指定是否对执行原子操作**这**是*无锁定*。 如果对类型执行的原子操作都没有使用锁，则原子类型为*无锁*。|
|[负载](#load)|读取并返回存储的值。|
|[store](#store)|使用指定值替换存储值。|

## <a name="remarks"></a>备注

类型*Ty*必须*完全可复制*。 即，使用[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)要复制其字节必须生成一个有效*Ty*比较等于原始对象的对象。 [Compare_exchange_weak](#compare_exchange_weak)和[compare_exchange_strong](#compare_exchange_strong)成员函数使用[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)以确定是否两个*Ty*值相等。 这些函数将不会使用*Ty*-定义**运算符 = =**。 成员函数的**原子**使用**memcpy**复制类型的值*Ty*。

部分专用化，* * 原子\<Ty * > * *，存在的所有指针类型。 通过专用化可将偏移量添加到托管的指针值或者从其中减去该偏移量。 算术运算采用的类型自变量**ptrdiff_t**并调整该自变量的大小根据*Ty*与普通地址运算保持一致。

专用化存在除每个整数类型**bool**。 每个专用化为原子算术和逻辑运算提供了一组丰富的方法。

||||
|-|-|-|
|**原子\<char >**|**原子\<签名 char >**|**原子\<无符号 char >**|
|**原子\<char16_t >**|**原子\<char32_t >**|**原子\<wchar_t >**|
|**原子\<短 >**|**原子\<无符号短 >**|**原子\<int >**|
|**原子\<无符号的 int >**|**原子\<长 >**|**原子\<无符号长 >**|
|**原子\<长时间长 >**|**原子\<无符号长时间长 >**|

整型的专用化派生自对应**atomic_integral**类型。 例如，**原子\<无符号的 int >** 派生自**atomic_uint**。

## <a name="requirements"></a>要求

**标头：** \<原子 >

**命名空间：** std

## <a name="atomic"></a> atomic:: atomic

构造一个原子对象。

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>参数

*值*<br/>
初始化值。

### <a name="remarks"></a>备注

无法复制或移动原子对象。

是实例化的原子对象\<*Ty*> 可以仅由接受类型的自变量的构造函数初始化*Ty*和不能通过使用聚合初始化。 但是，可以初始化 atomic_integral 对象，只能通过使用聚合初始化。

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> atomic:: operator *Ty*

指定到模板，原子类型的运算符\<*Ty*>。 检索中存储的值**\*这**。

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>备注

此运算符可将应用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_eq"></a> atomic:: operator =

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

*值*<br/>
A *Ty*对象。

### <a name="return-value"></a>返回值

返回*值*。

## <a name="op_inc"></a> atomic:: operator + +

增加存储值。 仅由整型和指针专用化使用。

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>返回值

前两个运算符将返回递增的值;最后两个运算符将返回前递增的值。 操作员使用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_add_eq"></a> atomic:: operator + =

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

*值*<br/>
一个整数或指针的值。

### <a name="return-value"></a>返回值

A *Ty*对象，其中包含添加的结果。

### <a name="remarks"></a>备注

此运算符可使用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_dec"></a> atomic:: operator-

减小存储值。 仅由整型和指针专用化使用。

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>返回值

前两个运算符将返回递减的值;最后两个运算符将返回前递减的值。 操作员使用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_sub_eq"></a> atomic:: operator =

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

*值*<br/>
一个整数或指针的值。

### <a name="return-value"></a>返回值

A *Ty*对象，其中包含该减法运算的结果。

### <a name="remarks"></a>备注

此运算符可使用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_and_eq"></a> atomic:: operator & =

执行按位和上指定的值和存储的值为**\*这**。 仅由整型专用化使用。

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>参数

*值*<br/>
类型的值*Ty*。

### <a name="return-value"></a>返回值

按位的结果和。

### <a name="remarks"></a>备注

此运算符执行读取-修改-写入操作替换的存储的值**\*这**按位与的*值*和存储中的当前值 **\*这**的约束内**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_or_eq"></a> atomic:: operator&#124;=

执行按位或上指定的值和存储的值为**\*这**。 仅由整型专用化使用。

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>参数

*值*<br/>
类型的值*Ty*。

### <a name="return-value"></a>返回值

结果的按位或。

### <a name="remarks"></a>备注

此运算符执行读取-修改-写入操作替换的存储的值**\*这**与按位或的*值*和存储中的当前值 **\*这**的约束内**memory_order_seq_cst** [memory_order](atomic-enums.md)约束。

## <a name="op_xor_eq"></a> atomic:: operator ^ =

执行按位异或上指定的值和存储的值为**\*这**。 仅由整型专用化使用。

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>参数

*值*<br/>
类型的值*Ty*。

### <a name="return-value"></a>返回值

结果的按位异或。

### <a name="remarks"></a>备注

此运算符执行读取-修改-写入操作替换的存储的值**\*这**与按位异或*值*和存储中的当前值**\*这**的约束内**memory_order_seq_cst** [memory_order](atomic-enums.md)约束。

## <a name="compare_exchange_strong"></a> atomic:: compare_exchange_strong

在执行原子比较和交换操作**\*这**。

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

*Exp*<br/>
类型的值*Ty*。

*值*<br/>
类型的值*Ty*。

*顺序排列 1*<br/>
第一个 **memory_order** 参数。

*Order2*<br/>
第二个**memory_order**自变量。

### <a name="return-value"></a>返回值

A **bool**指示值比较的结果。

### <a name="remarks"></a>备注

此原子比较和交换操作中存储的值进行比较**\*这**与*Exp*。值是否相等，如果该操作将替换中存储的值**\*这**与*值*通过使用读取-修改-写入操作以及应用内存顺序约束指定的*顺序排列 1*。 值是否不相等，如果该操作将使用存储中的值**\*这**替换*Exp*并应用指定的内存顺序约束*Order2*.

不具有第二个重载**memory_order**使用隐式*Order2*基于的值*顺序排列 1*。 如果*顺序排列 1*是**memory_order_acq_rel**， *Order2*是**memory_order_acquire**。 如果*顺序排列 1*是**memory_order_release**， *Order2*是**memory_order_relaxed**。 在所有其他情况下， *Order2*等同于*顺序排列 1*。

对于采用两个重载**memory_order**参数、 的值*Order2*不得**memory_order_release**或**memory_order_acq_rel**，并且不得超过了的值更强*顺序排列 1*。

## <a name="compare_exchange_weak"></a> atomic:: compare_exchange_weak

对执行弱原子比较和交换操作**\*这**。

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

*Exp*<br/>
类型的值*Ty*。

*值*<br/>
类型的值*Ty*。

*顺序排列 1*<br/>
第一个 **memory_order** 参数。

*Order2*<br/>
第二个**memory_order**自变量。

### <a name="return-value"></a>返回值

A **bool**指示值比较的结果。

### <a name="remarks"></a>备注

此原子比较和交换操作中存储的值进行比较**\*这**与*Exp*。值是否相等，如果该操作将替换中存储的值**\*这**与*值*通过使用读取-修改-写入操作以及应用内存顺序约束指定的*顺序排列 1*。 值是否不相等，如果该操作将使用存储中的值**\*这**替换*Exp*并应用指定的内存顺序约束*Order2*.

为弱原子比较和交换操作执行交换，如果比较的值相等。 如果值是否不相等，则不保证操作若要执行的交换。

不具有第二个重载**memory_order**使用隐式*Order2*基于的值*顺序排列 1*。 如果*顺序排列 1*是**memory_order_acq_rel**， *Order2*是**memory_order_acquire**。 如果*顺序排列 1*是**memory_order_release**， *Order2*是**memory_order_relaxed**。 在所有其他情况下， *Order2*等同于*顺序排列 1*。

对于采用两个重载**memory_order**参数、 的值*Order2*不得**memory_order_release**或**memory_order_acq_rel**，并且不得超过了的值更强*顺序排列 1*。

## <a name="exchange"></a> atomic:: exchange

使用指定的值来替换存储的值为**\*这**。

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

*值*<br/>
类型的值*Ty*。

*顺序*<br/>
**memory_order**。

### <a name="return-value"></a>返回值

存储的值**\*这**交换前。

### <a name="remarks"></a>备注

此操作执行读取-修改-写入操作，以使用*值*替换存储在值**\*这**，由指定的内存约束内*顺序*。

## <a name="fetch_add"></a> atomic:: fetch_add

提取中存储的值**\*这**，然后将指定的值添加到存储的值。

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

*值*<br/>
类型的值*Ty*。

*顺序*<br/>
**memory_order**。

### <a name="return-value"></a>返回值

A *Ty*包含中存储的值的对象**\*这**之前添加。

### <a name="remarks"></a>备注

**Fetch_add**方法执行的读取-修改-写入操作以原子方式添加*值*中存储的值为**\*这**，并将应用内存通过指定的约束*顺序*。

## <a name="fetch_and"></a> atomic:: fetch_and

执行按位和上一个值和存储在现有值**\*这**。

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

*值*<br/>
类型的值*Ty*。

*顺序*<br/>
**memory_order**。

### <a name="return-value"></a>返回值

A *Ty*包含结果的按位的对象和。

### <a name="remarks"></a>备注

**Fetch_and**方法执行读取-修改-写入操作，以替换存储的值为**\*这**按位与的*值*和当前中存储值**\*这**，由指定的内存约束内*顺序*。

## <a name="fetch_or"></a> atomic:: fetch_or

执行按位或在某个值或现有值存储在**\*这**。

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

*值*<br/>
类型的值*Ty*。

*顺序*<br/>
**memory_order**。

### <a name="return-value"></a>返回值

A *Ty*对象，其中包含的结果的按位或。

### <a name="remarks"></a>备注

**Fetch_or**方法执行读取-修改-写入操作，以替换存储的值为**\*这**与按位或的*值*和当前值存储在**\*这**，由指定的内存约束内*顺序*。

## <a name="fetch_sub"></a> atomic:: fetch_sub

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

*值*<br/>
类型的值*Ty*。

*顺序*<br/>
**memory_order**。

### <a name="return-value"></a>返回值

A *Ty*对象，其中包含该减法运算的结果。

### <a name="remarks"></a>备注

**Fetch_sub**方法执行的读取-修改-写入操作以原子方式减去*值*中存储的值从**\*这**，内存中通过指定的约束*顺序*。

## <a name="fetch_xor"></a> atomic:: fetch_xor

执行按位异或在某个值或现有值存储在**\*这**。

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

*值*<br/>
类型的值*Ty*。

*顺序*<br/>
**memory_order**。

### <a name="return-value"></a>返回值

A *Ty*对象，其中包含的结果的按位异或。

### <a name="remarks"></a>备注

**Fetch_xor**方法执行读取-修改-写入操作，以替换存储的值为**\*这**与按位异或*值*和中存储的当前值**\*这**，并应用指定的内存约束*顺序*。

## <a name="is_lock_free"></a> atomic:: is_lock_free

指定是否对执行原子操作**\*这**是无锁定。

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>返回值

如果原子操作**\*这**是锁可用; 否则为 false。

### <a name="remarks"></a>备注

如果没有对该类型执行原子操作使用锁，原子类型是可用的锁。

## <a name="load"></a> atomic:: load

检索中存储的值**\*这**，指定的内存约束内。

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>参数

*顺序*<br/>
**memory_order**。 *顺序*不得**memory_order_release**或**memory_order_acq_rel**。

### <a name="return-value"></a>返回值

检索到的值存储在**\*这**。

## <a name="store"></a> atomic:: store

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

*值*<br/>
A *Ty*对象。

*顺序*<br/>
A **memory_order**约束。

### <a name="remarks"></a>备注

此成员函数以原子方式将存储*值*中`*this`，由指定的内存约束内*顺序*。

## <a name="see-also"></a>请参阅

[\<atomic>](../standard-library/atomic.md)<br/>
[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
