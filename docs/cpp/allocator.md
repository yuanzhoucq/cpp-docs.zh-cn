---
title: 分配器
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: f9c8de7c8686b89a2ab9570a2558e3f649e545b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155233"
---
# <a name="allocator"></a>分配器

**Microsoft 专用**

**分配器**声明说明符可以应用于自定义的内存分配函数，以便通过事件跟踪 Windows (ETW) 显示了分配。

## <a name="syntax"></a>语法

```
   __declspec(allocator) 
```

## <a name="remarks"></a>备注

Visual Studio 中的本机内存探查器工作原理是收集 ETW 事件数据在运行时分配。 CRT 和 Windows SDK 中的分配器在源级别上注释，因此可以捕获其分配数据。 如果你正在编写你自己的分配器，则返回一个指向新分配的堆内存的任何函数可以使用修饰`__declspec(allocator)`，如 mymalloc 示例所示：

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

有关详细信息，请参阅[测量在 Visual Studio 中的内存使用情况](/visualstudio/profiling/memory-usage)并[自定义本机 ETW 堆事件](/visualstudio/profiling/custom-native-etw-heap-events)。