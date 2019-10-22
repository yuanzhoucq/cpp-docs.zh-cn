---
title: allocator_traits 类
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator_traits
- memory/std::allocator_traits::propagate_on_container_move_assignment
- memory/std::allocator_traits::const_pointer
- memory/std::allocator_traits::propagate_on_container_swap
- memory/std::allocator_traits::propagate_on_container_copy_assignment
- memory/std::allocator_traits::difference_type
- memory/std::allocator_traits::allocator_type
- memory/std::allocator_traits::value_type
- memory/std::allocator_traits::pointer
- memory/std::allocator_traits::size_type
- memory/std::allocator_traits::const_void_pointer
- memory/std::allocator_traits::void_pointer
- memory/std::allocator_traits::allocate
- memory/std::allocator_traits::construct
- memory/std::allocator_traits::deallocate
- memory/std::allocator_traits::destroy
- memory/std::allocator_traits::max_size
- memory/std::allocator_traits::select_on_container_copy_construction
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
helpviewer_keywords:
- std::allocator_traits [C++]
- std::allocator_traits [C++], propagate_on_container_move_assignment
- std::allocator_traits [C++], const_pointer
- std::allocator_traits [C++], propagate_on_container_swap
- std::allocator_traits [C++], propagate_on_container_copy_assignment
- std::allocator_traits [C++], difference_type
- std::allocator_traits [C++], allocator_type
- std::allocator_traits [C++], value_type
- std::allocator_traits [C++], pointer
- std::allocator_traits [C++], size_type
- std::allocator_traits [C++], const_void_pointer
- std::allocator_traits [C++], void_pointer
- std::allocator_traits [C++], allocate
- std::allocator_traits [C++], construct
- std::allocator_traits [C++], deallocate
- std::allocator_traits [C++], destroy
- std::allocator_traits [C++], max_size
- std::allocator_traits [C++], select_on_container_copy_construction
ms.openlocfilehash: 470b3086b4bdfa776558122eda9e496fa6c4bcdc
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690066"
---
# <a name="allocator_traits-class"></a>allocator_traits 类

类模板描述补充*分配器类型*的对象。 分配器类型是描述分配器对象的任何类型，它用于管理已分配的存储。 具体而言，对于任何分配器类型 `Alloc`，可以使用 `allocator_traits<Alloc>` 来确定支持分配器的容器所需的所有信息。 有关详细信息，请参阅默认的 [allocator 类](../standard-library/allocator-class.md)。

## <a name="syntax"></a>语法

```cpp
template <class Alloc>
    class allocator_traits;
```

## <a name="members"></a>Members

### <a name="typedefs"></a>Typedef

|||
|-|-|
|`allocator_type`|该类型是模板参数 `Alloc`的同义词。|
|`const_pointer`|如果该类型的形式正确，则此类型为 `Alloc::const_pointer`，否则，此类型为 `pointer_traits<pointer>::rebind<const value_type>`。|
|`const_void_pointer`|如果该类型的形式正确，则此类型为 `Alloc::const_void_pointer`，否则，此类型为 `pointer_traits<pointer>::rebind<const void>`。|
|`difference_type`|如果该类型的形式正确，则此类型为 `Alloc::difference_type`，否则，此类型为 `pointer_traits<pointer>::difference_type`。|
|`pointer`|如果该类型的形式正确，则此类型为 `Alloc::pointer`，否则，此类型为 `value_type *`。|
|`propagate_on_container_copy_assignment`|如果该类型的形式正确，则此类型为 `Alloc::propagate_on_container_copy_assignment`，否则，此类型为 `false_type`。|
|`propagate_on_container_move_assignment`|如果该类型的形式正确，则此类型为 `Alloc::propagate_on_container_move_assignment`，否则，此类型为 `false_type`。 如果类型为 true，则支持分配器的容器将在移动赋值上复制其存储的分配器。|
|`propagate_on_container_swap`|如果该类型的形式正确，则此类型为 `Alloc::propagate_on_container_swap`，否则，此类型为 `false_type`。 如果类型为 true，则支持分配器的容器将在交换上交换其存储的分配器。|
|`size_type`|如果该类型的形式正确，则此类型为 `Alloc::size_type`，否则，此类型为 `make_unsigned<difference_type>::type`。|
|`value_type`|此类型是 `Alloc::value_type` 的同义词。|
|`void_pointer`|如果该类型的形式正确，则此类型为 `Alloc::void_pointer`，否则，此类型为 `pointer_traits<pointer>::rebind<void>`。|

### <a name="static-methods"></a>静态方法

以下静态方法调用给定分配器参数上的相应的方法。

|||
|-|-|
|[allocate](#allocate)|使用给定的分配器参数分配内存的静态方法。|
|[construct](#construct)|使用指定的分配器构造对象的静态方法。|
|[deallocate](#deallocate)|使用指定的分配器释放指定的对象数的静态方法。|
|[destroy](#destroy)|使用指定的分配器调用对象上的构造函数而不释放其内存的静态方法。|
|[max_size](#max_size)|可以分配使用指定的分配器确定对象的最大数目的静态方法。|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|在指定的分配器上调用 `select_on_container_copy_construction` 的静态方法。|

### <a name="allocate"></a>分配

使用给定的分配器参数分配内存的静态方法。

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

#### <a name="parameters"></a>参数

*al* \
分配器对象。

*计数*\
要分配的元素数量。

*提示*\
通过定位在请求之前分配的对象的地址，`const_pointer` 可能帮助分配器满足存储请求。 Null 指针将被视为无提示。

#### <a name="return-value"></a>返回值

每个方法均返回指向已分配对象的指针。

第一种静态方法返回 `al.allocate(count)`。

第二种方法返回 `al.allocate(count, hint)`（如果该表达式形式正确）；否则返回 `al.allocate(count)`。

### <a name="construct"></a>构造

使用指定的分配器构造对象的静态方法。

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

#### <a name="parameters"></a>参数

*al* \
分配器对象。

*ptr* \
指向要构造对象的位置的指针。

*args* \
传递给对象构造函数的参数列表。

#### <a name="remarks"></a>备注

如果该表达式形式正确，则静态成员函数调用 `al.construct(ptr, args...)`；否则计算 `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)` 的结果。

### <a name="deallocate"></a>写意

使用指定的分配器释放指定的对象数的静态方法。

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

#### <a name="parameters"></a>参数

*al* \
分配器对象。

*ptr* \
指向要释放对象的起始位置的指针。

*计数*\
要释放的对象数。

#### <a name="remarks"></a>备注

此方法调用 `al.deallocate(ptr, count)`。

此方法不会引发任何操作。

### <a name="destroy"></a>破坏

使用指定的分配器调用对象上的构造函数而不释放其内存的静态方法。

```cpp
template <class Uty>
    static void destroy(Alloc& al, Uty* ptr);
```

#### <a name="parameters"></a>参数

*al* \
分配器对象。

*ptr* \
指向对象位置的指针。

#### <a name="remarks"></a>备注

如果该表达式形式正确，则此方法调用 `al.destroy(ptr)`；否则计算 `ptr->~Uty()` 的结果。

### <a name="max_size"></a>max_size

可以分配使用指定的分配器确定对象的最大数目的静态方法。

```cpp
static size_type max_size(const Alloc& al);
```

#### <a name="parameters"></a>参数

*al* \
分配器对象。

#### <a name="remarks"></a>备注

如果该表达式形式正确，则此方法返回 `al.max_size()`；否则返回 `numeric_limits<size_type>::max()`。

### <a name="select_on_container_copy_construction"></a>select_on_container_copy_construction

在指定的分配器上调用 `select_on_container_copy_construction` 的静态方法。

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

#### <a name="parameters"></a>参数

*al* \
分配器对象。

#### <a name="return-value"></a>返回值

如果该类型格式正确，则此方法返回 `al.select_on_container_copy_construction()`;否则，它将返回*al*。

#### <a name="remarks"></a>备注

此方法用于在所关联的容器为构造副本时指定分配器。
