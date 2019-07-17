---
title: '&lt;new&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245163"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedefs

## <a name="hardware_constructive_interference_size"></a> hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>备注

此数字是内存的建议的连续两个与时间局部性指由并发线程访问的对象占用大小的最大值。 它应至少为`alignof(max_align_t)`。

### <a name="example"></a>示例

```cpp
struct together { 
    atomic<int> dog;
    int puppy;
};

struct kennel {
    // Other data members...
    alignas(sizeof(together)) together pack;
    // Other data members...
};

static_assert(sizeof(together) <= hardware_constructive_interference_size);
```

## <a name="hardware_destructive_interference_size"></a> hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>备注

此数字是两个同时并发访问对象，以避免由于争用由实现引入的其他性能降低之间的最小建议偏移量。 它应至少为`alignof(max_align_t)`。

### <a name="example"></a>示例

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a> new_handler

该类型指向适合用作新处理程序的函数。

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>备注

这种类型的处理程序函数调用**运算符 new**或`operator new[]`时它们不能满足额外的存储的请求。

### <a name="example"></a>示例

有关将 `new_handler` 用作返回值的示例，请参阅 [set_new_handler](../standard-library/new-functions.md#set_new_handler)。
