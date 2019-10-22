---
title: '&lt;memory&gt;'
ms.date: 08/04/2019
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: 4a6383ee94d021373b984122926a5bb73e18f953
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689364"
---
# <a name="ltmemorygt"></a>&lt;memory&gt;

定义一个类、运算符和一些模板来帮助分配和释放对象。

## <a name="requirements"></a>要求

**标头：** \<memory>

**命名空间:** std

## <a name="members"></a>Members

### <a name="functions"></a>函数

|||
|-|-|
|[addressof](../standard-library/memory-functions.md#addressof)|获取对象的实际地址。|
|[align](../standard-library/memory-functions.md#align)|根据所提供的对齐和起始地址，返回指向给定大小范围的指针。|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|创建一个 `shared_ptr`，指向使用指定分配器分配和构造的给定类型的对象。|
|[atomic_compare_exchange_strong](../standard-library/memory-functions.md#atomic_compare_exchange_strong)||
|[atomic_compare_exchange_weak](../standard-library/memory-functions.md#atomic_compare_exchange_weak)||
|[atomic_compare_exchange_strong_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_strong_explicit)||
|[atomic_compare_exchange_weak_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_weak_explicit)||
|[atomic_exchange](../standard-library/memory-functions.md#atomic_exchange)||
|[atomic_exchange_explicit](../standard-library/memory-functions.md#atomic_exchange_explicit)||
|[atomic_is_lock_free](../standard-library/memory-functions.md#atomic_is_lock_free)||
|[atomic_load](../standard-library/memory-functions.md#atomic_load)||
|[atomic_load_explicit](../standard-library/memory-functions.md#atomic_load_explicit)||
|[atomic_store](../standard-library/memory-functions.md#atomic_store)||
|[atomic_store_explicit](../standard-library/memory-functions.md#atomic_store_explicit)||
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|常量强制转换为 `shared_ptr`。|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|通知垃圾回收器：从指定地址开始且属于所指示块大小范围内的字符不包含可跟踪的指针。|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|通知垃圾回收器：所指示的地址属于分配的存储并可到达。|
|[default_delete](../standard-library/memory-functions.md#default_delete)|删除使用 `operator new` 分配的对象。 适合与 `unique_ptr` 一起使用。|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|速记 `destroy` 方法。|
|[destroy](../standard-library/memory-functions.md#destroy)|速记 `destroy` 方法。|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|速记 `destroy` 方法。|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|动态强制转换为 `shared_ptr`。|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|从 `shared_ptr` 获取删除器。|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|返回任意垃圾回收器所采用的指针安全类型。|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|为不超过指定元素数量的元素序列分配临时存储。|
|[make_shared](../standard-library/memory-functions.md#make_shared)|创建并返回一个 `shared_ptr`，指向使用默认分配器从零个或多个参数构造的分配对象。|
|[make_unique](../standard-library/memory-functions.md#make_unique)|创建并返回一个 [unique_ptr](../standard-library/unique-ptr-class.md)，指向从零个或多个自变量构建的分配对象。|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|一种对 `get_pointer_safety` 的所有可能返回值的枚举。|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|对使用 `get_temporary_buffer` 模板函数分配的临时内存执行解除分配。|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|静态强制转换为 `shared_ptr`。|
|[swap](../standard-library/memory-functions.md#swap)|交换两个 `shared_ptr` 或 `weak_ptr` 对象。|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|通知垃圾回收器：通过基地址指针和块大小而定义的内存块中的字符现在可包含可跟踪的指针。|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|通知 `garbage_collector`：指定的内存位置无法达到。|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|将来自指定输入范围的对象复制到未初始化的目标范围。|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|创建来自输入迭代器的指定数量的元素的副本。 副本放置在向前迭代器中。|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|速记 `uninitialized_default_construct` 方法。|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|速记 `uninitialized_construct` 方法。|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|将具有指定值的对象复制到未初始化的目标范围。|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|将具有指定值的对象复制到未初始化目标范围的指定数量的元素。|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|速记 `uninitialized_move` 方法。|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|速记 `uninitialized_move` 方法。|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|速记 `uninitialized_value_construct` 方法。|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|速记 `uninitialized_value_construct` 方法。|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>运算符

|||
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|测试指定类的分配器对象之间是否不相等。|
|[operator==](../standard-library/memory-operators.md#op_eq_eq)|测试指定类的分配器对象之间是否相等。|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|测试指定类的某一分配器对象是否大于或等于另一个分配器对象。|
|[operator<](../standard-library/memory-operators.md#op_lt)|测试指定类的某一对象是否小于另一个对象。|
|[operator\<=](../standard-library/memory-operators.md#op_gt_eq)|测试指定类的某一对象是否小于或等于另一个对象。|
|[operator>](../standard-library/memory-operators.md#op_gt)|测试指定类的某一对象是否大于另一个对象。|
|[operator<<](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` 插入器。|

### <a name="classes"></a>类

|||
|-|-|
|[allocator](../standard-library/allocator-class.md)|类模板描述了一个对象，该对象**管理类型为**的对象数组的存储分配和释放。|
|[allocator_traits](../standard-library/allocator-traits-class.md)|描述一个对象，用于确定支持分配器的容器所需要的全部信息。|
|[auto_ptr](../standard-library/auto-ptr-class.md)|类模板描述了一个对象，该对象存储一个**指向类型为**type <strong>\*</strong>的已分配对象的指针，该指针可确保当它的封闭 auto_ptr 被销毁时，它指向的对象将被删除。|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|报告不良的 weak_ptr 异常。|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|帮助生成一个 `shared_ptr`。|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|提供 `allocator_traits` 类型的对象所需的信息，以描述指针类型为 `Ptr` 的分配器。|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|一种所提供的适配器类，使算法能够将它们的结果存储到未初始化的内存中。|
|[shared_ptr](../standard-library/shared-ptr-class.md)|将引用计数智能指针回绕在动态分配的对象周围。|
|[unique_ptr](../standard-library/unique-ptr-class.md)|存储指向拥有的对象的指针。 指针不归任何其他 `unique_ptr` 所拥有。 当所有者被销毁后，`unique_ptr` 也会被销毁。|
|[weak_ptr](../standard-library/weak-ptr-class.md)|回绕弱链接指针。|

### <a name="structures"></a>结构

|||
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|hash|为 `unique_ptr` 和 `shared_ptr` 提供专用重载。|
|[owner_less](../standard-library/memory-functions.md#owner_less)|允许对共享指针和弱指针进行基于所有权的混合比较。|
|[uses_allocator](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>专用化

|||
|-|-|
|[allocator\<void>](../standard-library/allocator-void-class.md)|类模板分配器到类型**void**的专用化，仅定义在此专用化上下文中有意义的成员类型。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
