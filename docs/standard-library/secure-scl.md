---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: dcfaee2906136dffbe79a49f089a079104112e78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559154"
---
# <a name="securescl"></a>_SECURE_SCL

被 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 所取代，此宏可定义是否已启用[经过检查的迭代器](../standard-library/checked-iterators.md)。 默认情况下，经过检查的迭代器在调试版本中处于启用状态，在零售版本中处于禁用状态。

> [!IMPORTANT]
> 直接使用 _SECURE_SCL 宏已弃用。 请改用 _ITERATOR_DEBUG_LEVEL 控制检查迭代器设置。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>备注

启用经过检查的迭代器时，使用不安全的迭代器会导致运行时错误并终止程序。 若要启用检查迭代器，设置为 1 或 2 _ITERATOR_DEBUG_LEVEL。 这相当于 _SECURE_SCL 设置为 1，或已启用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

若要禁用检查迭代器，设置为 0 _ITERATOR_DEBUG_LEVEL。 这相当于 _SECURE_SCL 设置为 0，或已禁用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

有关如何禁用经过检查的迭代器的警告信息，请参阅 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

## <a name="see-also"></a>请参阅

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[安全库：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
