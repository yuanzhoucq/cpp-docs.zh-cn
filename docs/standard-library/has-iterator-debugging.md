---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: a1e3017ed7c6def18ce02d99dc8253b69c11ab58
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448837"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

由 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代，该宏定义调试版本中是否启用了迭代器调试功能。 默认情况下，迭代器调试在调试版本中处于启用状态，在零售版本中处于禁用状态。 有关详细信息，请参阅[调试迭代器支持](../standard-library/debug-iterator-support.md)。

> [!IMPORTANT]
> 不推荐使用 _HAS_ITERATOR_DEBUGGING 宏。 改为使用 _ITERATOR_DEBUG_LEVEL 控制迭代器调试设置。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>备注

若要在调试版本中启用迭代器调试, 请将 _ITERATOR_DEBUG_LEVEL 设置为2。 这等效于 _HAS_ITERATOR_DEBUGGING 设置1或 enabled:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

在零售版本中, 不能将 _ITERATOR_DEBUG_LEVEL 设置为 2 (并且 _HAS_ITERATOR_DEBUGGING 不能设置为 1)。

若要在调试版本中禁用调试迭代器, 请将 _ITERATOR_DEBUG_LEVEL 设置为0或1。 这等效于 _HAS_ITERATOR_DEBUGGING 设置0或 disabled:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>请参阅

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[调试迭代器支持](../standard-library/debug-iterator-support.md)\
[经过检查的迭代器](../standard-library/checked-iterators.md)\
[：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)
