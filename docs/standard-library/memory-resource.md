---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: b5957412d2beff0dc709dc71a77834f13eeacb41
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269339"
---
# <a name="ltmemoryresourcegt"></a>&lt;memory_resource&gt;

定义容器模板类 memory_resource 和及其支持的模板。

## <a name="syntax"></a>语法

```cpp
#include <memory_resource>
```

## <a name="members"></a>成员

### <a name="operators"></a>运算符

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|测试运算符左侧的 memory_resource 对象是否不等于右侧的 memory_resource 对象。|
|[operator==](../standard-library/memory-resource-operators.md#op_eq_eq)|测试运算符左侧的 memory_resource 对象是否等于右侧的 memory_resource 对象。|

### <a name="specialized-template-functions"></a>专用化模板函数

|||
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>函数

|||
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>类和结构

|||
|-|-|
|[memory_resource 类](../standard-library/memory-resource-class.md)||
|[monotonic_buffer_resource 类](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options 结构](../standard-library/pool-options-structure.md)||
|[synchronized_pool_resource 类](../standard-library/synchronized-pool-resource-class.md)||
|[unsynchronized_pool_resource 类](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
