---
title: 分配器
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: 39708e8cfff7f61c3a3f763f87e1a3da36f0d4b1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077260"
---
# <a name="allocator"></a>分配器

**Microsoft 专用**

**分配**器声明说明符可应用于自定义内存分配函数，以使分配可通过 Windows 事件跟踪（ETW）来查看。

## <a name="syntax"></a>语法

```
   __declspec(allocator)
```

## <a name="remarks"></a>备注

Visual Studio 中的本机内存探查器的工作原理是在运行时收集发送的分配 ETW 事件数据。 CRT 和 Windows SDK 中的分配器在源级别上注释，因此可以捕获其分配数据。 如果你正在编写自己的分配器，则返回指向新分配的堆内存的指针的任何函数都可以使用 `__declspec(allocator)`进行修饰，如如此 mymalloc 的此示例中所示：

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

有关详细信息，请参阅[在 Visual Studio 中度量内存使用情况](/visualstudio/profiling/memory-usage)和[自定义本机 ETW 堆事件](/visualstudio/profiling/custom-native-etw-heap-events)。

**结束 Microsoft 专用**
