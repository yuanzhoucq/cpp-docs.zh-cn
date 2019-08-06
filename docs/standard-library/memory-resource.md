---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: d4b25c6ee575191f1e17b0202d33298e2e9e67f0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451906"
---
# <a name="ltmemoryresourcegt"></a>&lt;memory_resource&gt;

定义容器模板类 memory_resource 及其支持的模板。

## <a name="syntax"></a>语法

```cpp
#include <memory_resource>
```

## <a name="members"></a>成员

### <a name="operators"></a>运算符

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|测试位于运算符左侧的 memory_resource 对象是否不等于右侧的 memory_resource 对象。|
|[operator==](../standard-library/memory-resource-operators.md#op_eq_eq)|测试位于运算符左侧的 memory_resource 对象是否等于右侧的 memory_resource 对象。|

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

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
