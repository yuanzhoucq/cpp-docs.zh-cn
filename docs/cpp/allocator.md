---
title: 分配器
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: a26cf4d2b79d64ddc9f0b60982d778e33d0f200a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216643"
---
# `allocator`

**Microsoft 专用**

**`allocator`** 声明说明符可应用于自定义内存分配函数，以使分配可通过 Windows 事件跟踪（ETW）来查看。

## <a name="syntax"></a>语法

> **`__declspec(allocator)`**

## <a name="remarks"></a>备注

Visual Studio 中的本机内存探查器的工作原理是在运行时收集发送的分配 ETW 事件数据。 CRT 和 Windows SDK 中的分配器在源级别上注释，因此可以捕获其分配数据。 如果你正在编写自己的分配器，则可使用修饰返回指向新分配的堆内存的指针的所有函数 `__declspec(allocator)` ，如以下如此 mymalloc 示例所示：

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

有关详细信息，请参阅[在 Visual Studio 中度量内存使用情况](/visualstudio/profiling/memory-usage)和[自定义本机 ETW 堆事件](/visualstudio/profiling/custom-native-etw-heap-events)。

**结束 Microsoft 专用**
