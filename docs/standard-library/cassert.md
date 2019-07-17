---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 14dda03e835ec411013b2d827bd1ccaa77f8982e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245021"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

包含标准 C 库标头\<assert.h >，并将添加到关联的名称`std`命名空间。 包括此标头中声明标准 C 库标头中使用外部链接声明的名称将确保`std`命名空间。

> [!NOTE]
> \<assert.h > 未定义`static_assert`宏。

## <a name="syntax"></a>语法

```cpp
#include <cassert>
```

## <a name="macros"></a>宏

```cpp
#define assert(E)
```

### <a name="remarks"></a>备注

`assert(E)` 只能为常量，如果定义了 NDEBUG 其中`assert`上一次定义或重新定义，或*E*转换为布尔值的计算结果为**true**。

## <a name="see-also"></a>请参阅

[assert 宏、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
