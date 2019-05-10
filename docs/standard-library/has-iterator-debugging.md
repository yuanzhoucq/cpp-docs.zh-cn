---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: 339c32f9b487db2e318f8763ac01a0d155fc1dc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159699"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

由 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代，该宏定义调试版本中是否启用了迭代器调试功能。 默认情况下，迭代器调试在调试版本中处于启用状态，在零售版本中处于禁用状态。 有关详细信息，请参阅[调试迭代器支持](../standard-library/debug-iterator-support.md)。

> [!IMPORTANT]
> 直接使用 _HAS_ITERATOR_DEBUGGING 宏已弃用。 请改用 _ITERATOR_DEBUG_LEVEL 来控制迭代器调试设置。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>备注

若要启用迭代器调试在调试版本中，设置为 2 _ITERATOR_DEBUG_LEVEL。 这相当于 _HAS_ITERATOR_DEBUGGING 设置为 1，或已启用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

_ITERATOR_DEBUG_LEVEL 不能设置为 2 （和 _HAS_ITERATOR_DEBUGGING 不能设置为 1） 在零售版本。

若要禁用调试迭代器在调试版本中的，设置为 0 或 1 _ITERATOR_DEBUG_LEVEL。 这相当于 _HAS_ITERATOR_DEBUGGING 设置为 0，或已禁用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>请参阅

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
