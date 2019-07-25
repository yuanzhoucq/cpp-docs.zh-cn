---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 58ebd91fb4fa32cf31d2c49429d0445b92fe0c82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449911"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

包括 C 标准库标头\<assert > 并将关联名称添加`std`到命名空间。 包括此标头可确保在`std`命名空间中声明使用 C 标准库标头中的外部链接声明的名称。

> [!NOTE]
> \<> 不定义`static_assert`宏。

## <a name="syntax"></a>语法

```cpp
#include <cassert>
```

## <a name="macros"></a>宏

```cpp
#define assert(E)
```

### <a name="remarks"></a>备注

`assert(E)`仅为常量, 如果定义了 NDEBUG, `assert`其中定义或重新定义了, 或*E*转换为 bool, 则计算结果为**true**。

## <a name="see-also"></a>请参阅

[assert 宏、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
