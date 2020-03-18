---
title: '&lt;new&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425375"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedefs

## <a name="hardware_constructive_interference_size"></a>hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>备注

此数字是通过并发线程使用时态位置访问的两个对象所占用的最大连续内存大小。 它至少应为 `alignof(max_align_t)`。

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

## <a name="hardware_destructive_interference_size"></a>hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>备注

此数字是两个并发访问的对象之间的最小建议偏移量，以避免因实现引入的争用而导致的额外性能下降。 它至少应为 `alignof(max_align_t)`。

### <a name="example"></a>示例

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a>new_handler

该类型指向适合用作新处理程序的函数。

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>备注

此类型的处理程序函数由 new 或 `operator new[]`**运算符**在无法满足额外存储的请求时调用。

### <a name="example"></a>示例

有关将 [ 用作返回值的示例，请参阅 ](../standard-library/new-functions.md#set_new_handler)set_new_handler`new_handler`。
