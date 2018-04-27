---
title: _HAS_ITERATOR_DEBUGGING | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
dev_langs:
- C++
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1e6cf83c0877c351a2bf247a557f3df53e9c1f22
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

由 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代，该宏定义调试版本中是否启用了迭代器调试功能。 默认情况下，迭代器调试在调试版本中处于启用状态，在零售版本中处于禁用状态。 有关详细信息，请参阅[调试迭代器支持](../standard-library/debug-iterator-support.md)。

> [!IMPORTANT]
> 已弃用直接使用宏 `_HAS_ITERATOR_DEBUGGING`。 请改用 `_ITERATOR_DEBUG_LEVEL` 来控制迭代器调试设置。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>备注

若要在调试版本中启用迭代器调试，请将 `_ITERATOR_DEBUG_LEVEL` 设置为 2。 这相当于 `_HAS_ITERATOR_DEBUGGING` 设置为 1 或已启用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

在零售版本中，`_ITERATOR_DEBUG_LEVEL` 无法设置为 2（且 `_HAS_ITERATOR_DEBUGGING` 无法设置为 1）。

若要在调试版本中禁用调试迭代器，请将 `_ITERATOR_DEBUG_LEVEL` 设置为 0 或 1。 这相当于 `_HAS_ITERATOR_DEBUGGING` 设置为 0 或已禁用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>请参阅

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[安全库：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
