---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: b28f4554610d37b881494748f75499f46cd9e8d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230228"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

包括 C 标准库标头 \<assert.h> 并将关联名称添加到 `std` 命名空间。 包括此标头可确保在命名空间中声明使用 C 标准库标头中的外部链接声明的名称 `std` 。

> [!NOTE]
> \<assert.h>不定义 **`static_assert`** 宏。

## <a name="syntax"></a>语法

```cpp
#include <cassert>
```

## <a name="macros"></a>宏

```cpp
#define assert(E)
```

### <a name="remarks"></a>备注

`assert(E)`仅为常量，如果定义了 NDEBUG，定义 `assert` 了最后定义或重新定义的，或者*E*转换为 bool，则计算结果为 **`true`** 。

## <a name="see-also"></a>另请参阅

[assert 宏、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
