---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: 1af084363fc0d6d1723a9af7b633779f92ed2b38
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450529"
---
# <a name="securescl"></a>_SECURE_SCL

被 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 所取代，此宏可定义是否已启用[经过检查的迭代器](../standard-library/checked-iterators.md)。 默认情况下，经过检查的迭代器在调试版本中处于启用状态，在零售版本中处于禁用状态。

> [!IMPORTANT]
> 不推荐使用 _SECURE_SCL 宏。 改为使用 _ITERATOR_DEBUG_LEVEL 控制检查的迭代器设置。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>备注

启用经过检查的迭代器时，使用不安全的迭代器会导致运行时错误并终止程序。 若要启用选中的迭代器, 请将 _ITERATOR_DEBUG_LEVEL 设置为1或2。 这等效于 _SECURE_SCL 设置1或 enabled:

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

若要禁用选中的迭代器, 请将 _ITERATOR_DEBUG_LEVEL 设置为0。 这等效于 _SECURE_SCL 设置0或 disabled:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

有关如何禁用经过检查的迭代器的警告信息，请参阅 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

## <a name="see-also"></a>请参阅

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[经过检查的迭代器](../standard-library/checked-iterators.md)\
[调试迭代器支持](../standard-library/debug-iterator-support.md)\
[：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)
