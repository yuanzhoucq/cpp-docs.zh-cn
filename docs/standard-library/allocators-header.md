---
title: '&lt;allocators&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: f981b86ed8f5d3b240d9f02380a603eb4f2605bc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623582"
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;

定义多个模板，帮助为基于节点的容器分配和释放内存块。

## <a name="syntax"></a>语法

```cpp
#include <allocators>
```

> [!NOTE]
> \<allocators>从 Visual Studio 2019 版本16.3 开始已弃用。

## <a name="remarks"></a>备注

\<allocators>标头提供六个分配器模板，可用于为基于节点的容器选择内存管理策略。 对于使用这些模板，它还提供多种不同的同步筛选器，以将内存管理策略定制到各种不同的多线程方案（包括无）。 可以通过将内存管理策略与内存使用模式和同步要求相匹配来加速应用或降低其内存需求。

分配器模板使用重用的组件来实现，可以进行自定义或被替换，以提供额外的内存管理策略。

C + + 标准库（std：： list、std：： set、std：：多重集、std：： map 和 std：：多重映射）中基于节点的容器将其元素存储在单个节点中。 针对特定容器类型的所有节点都具有相同大小，因此无需内存管理器常规用途的灵活性。 因为已在编译时知道每个内存块的大小，所以内存管理器可以更简单、更快。

与非基于节点的容器一起使用时（例如 c + + 标准库容器 std：： vector std：:d eque 和 std：： basic_string），分配器模板将正常工作，但不可能为默认分配器提供任何性能改善。

分配器是一个类模板，用于描述一个对象，该对象用于管理指定类型的对象和对象数组的存储分配和释放。 分配器对象由 c + + 标准库中的多个容器类模板使用。

分配器是此类型的所有模板：

```cpp
template<class Type>
class allocator;
```

其中模板参数 `Type` 是由分配器实例所管理的类型。 C + + 标准库提供了在中定义的默认分配器类模板[分配](allocator-class.md)器 [\<memory>](memory.md) 。 \<allocators>标头提供以下分配器：

- [allocator_newdel](allocator-newdel-class.md)

- [allocator_unbounded](allocator-unbounded-class.md)

- [allocator_fixed_size](allocator-fixed-size-class.md)

- [allocator_variable_size](allocator-variable-size-class.md)

- [allocator_suballoc](allocator-suballoc-class.md)

- [allocator_chunklist](allocator-chunklist-class.md)

在创建容器时，将相应的分配器实例化用作第二个类型参数，如以下代码示例。

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0 使用 `allocator_chunklist` 和默认的同步筛选器来分配节点。

使用宏 [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) 来创建具有同步筛选器的分配器模板而非默认模板。

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1 使用 `allocator_chunklist` 和 [sync_per_thread](sync-per-thread-class.md) 同步筛选器来分配节点。

块分配器是一个缓存或筛选器。 缓存是一个类模板，它采用一个类型为 std：： size_t 的参数。 它定义分配和释放单个大小内存块的块分配器。 它必须使用运算符**new**获取内存，但不需要对每个块单独调用 operator **new** 。 例如，从较大块或缓存释放分配块进行子分配，以用于后续的重新分配。

如果编译器无法重新绑定在对模板进行实例化时使用的 std：： size_t 参数的值，则不一定是传递给缓存成员函数的参数 _Sz 分配和解除分配。

\<allocators>提供以下缓存模板：

- [cache_freelist](cache-freelist-class.md)

- [cache_suballoc](cache-suballoc-class.md)

- [cache_chunklist](cache-chunklist-class.md)

筛选器是一个块分配器，它使用另一个块分配器来实现其成员函数，后者作为模板自变量传递给它。 筛选器最常见的形式是同步筛选器，它采用同步策略来控制对其他块分配器实例的成员函数的访问。 \<allocators>提供以下同步筛选器：

- [sync_none](sync-none-class.md)

- [sync_per_container](sync-per-container-class.md)

- [sync_per_thread](sync-per-thread-class.md)

- [sync_shared](sync-shared-class.md)

\<allocators>还提供[rts_alloc](rts-alloc-class.md)的筛选器，该筛选器包含多个块分配器实例，并确定在运行时（而不是在编译时）用于分配或解除分配的实例。 它与不能编译重新绑定的编译器一起使用。

同步策略确定分配器实例如何处理来自多线程的同步分配和解除分配的请求。 最简单的策略是将所有请求直接传递到基础缓存对象，将同步管理留给用户。 较复杂的策略是使用互斥体对基础缓存对象的访问进行序列化。

如果编译器支持编译单线程和多线程应用程序，则单线程应用程序的默认同步筛选器为 `sync_none`，在所有其他情况下为 `sync_shared`。

缓存模板 `cache_freelist` 采用 max class 参数，该参数确定可用列表中要存储的最大元素数。

\<allocators>提供以下最大类：

- [max_none](max-none-class.md)

- [max_unbounded](max-unbounded-class.md)

- [max_fixed_size](max-fixed-size-class.md)

- [max_variable_size](max-variable-size-class.md)

### <a name="macros"></a>宏

|宏|描述|
|-|-|
|[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)|生成分配器类模板。|
|[CACHE_CHUNKLIST](allocators-functions.md#cache_chunklist)|生成 `stdext::allocators::cache_chunklist<sizeof(Type)>`。|
|[CACHE_FREELIST](allocators-functions.md#cache_freelist)|生成 `stdext::allocators::cache_freelist<sizeof(Type), max>`。|
|[CACHE_SUBALLOC](allocators-functions.md#cache_suballoc)|生成 `stdext::allocators::cache_suballoc<sizeof(Type)>`。|
|[SYNC_DEFAULT](allocators-functions.md#sync_default)|生成同步筛选器。|

### <a name="operators"></a>运算符

|运算符|说明|
|-|-|
|[operator！ = （ \<allocators> ）](allocators-operators.md#op_neq)|测试指定类的分配器对象之间是否不相等。|
|[operator = = （ \<allocators> ）](allocators-operators.md#op_eq_eq)|测试指定类的分配器对象之间是否相等。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[allocator_base](allocator-base-class.md)|定义基类和常用函数需要从同步筛选器创建一个用户定义的分配器。|
|[allocator_chunklist](allocator-chunklist-class.md)|描述一个对象，用于管理使用缓存类型为 [cache_chunklist](cache-chunklist-class.md) 的对象的存储分配和释放。|
|[allocator_fixed_size](allocator-fixed-size-class.md)|描述一个对象，用于管理由 [max_fixed_size](max-fixed-size-class.md) 所管理的长度的使用缓存类型 [cache_suballoc](cache-freelist-class.md) 的类型 `Type` 的对象的存储分配和释放。|
|[allocator_newdel](allocator-newdel-class.md)|实现一个分配器，该分配器使用**运算符 delete**来释放内存块，使用**new 运算符**分配内存块。|
|[allocator_suballoc](allocator-suballoc-class.md)|描述一个对象，用于管理使用类型 [cache_suballoc](cache-suballoc-class.md) 的缓存类型的类型 `Type` 的对象的存储分配和释放。|
|[allocator_unbounded](allocator-unbounded-class.md)|描述一个对象，用于管理使用缓存类型为 [cache_freelist](cache-freelist-class.md) 的对象类型 `Type` 的存储分配和释放，其长度由 [max_unbounded](max-unbounded-class.md) 管理。|
|[allocator_variable_size](allocator-variable-size-class.md)|描述一个对象，用于管理使用缓存类型为 [cache_freelist](cache-freelist-class.md) 的对象类型 `Type` 的存储分配和释放，其长度由 [max_variable_size](max-variable-size-class.md) 管理。|
|[cache_chunklist](cache-chunklist-class.md)|定义分配和释放单个大小内存块的块分配器。|
|[cache_freelist](cache-freelist-class.md)|定义分配和释放单个大小内存块的块分配器。|
|[cache_suballoc](cache-suballoc-class.md)|定义分配和释放单个大小内存块的块分配器。|
|[freelist](freelist-class.md)|管理内存块列表。|
|[max_fixed_size](max-fixed-size-class.md)|描述 max 类 对象，该对象将 [freelist](freelist-class.md) 对象的最大长度限制为固定的最大长度。|
|[max_none](max-none-class.md)|描述 max 类 对象，该对象将 [freelist](freelist-class.md) 对象的最大长度限制为零。|
|[max_unbounded](max-unbounded-class.md)|描述 max 类 对象，该对象不限制 [freelist](freelist-class.md) 对象的最大长度。|
|[max_variable_size](max-variable-size-class.md)|描述 max 类 对象，该对象将 [freelist](freelist-class.md) 对象限制为与已分配的内存块数大致成比例的最大长度。|
|[rts_alloc](rts-alloc-class.md)|Rts_alloc 类模板描述了一个[筛选器，该筛选器](allocators-header.md)保存缓存实例的数组，并确定在运行时（而不是在编译时）用于分配和解除分配的实例。|
|[sync_none](sync-none-class.md)|描述不提供同步的同步筛选器。|
|[sync_per_container](sync-per-container-class.md)|描述为每个筛选器对象提供单独的缓存对象的同步筛选。|
|[sync_per_thread](sync-per-thread-class.md)|描述为每个线程提供单独的缓存对象的同步筛选器。|
|[sync_shared](sync-shared-class.md)|介绍同步筛选器，它使用互斥体来控制对所有分配器共享的缓存对象的访问。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="see-also"></a>另请参阅

[头文件引用](cpp-standard-library-header-files.md)
