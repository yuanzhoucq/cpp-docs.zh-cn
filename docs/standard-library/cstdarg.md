---
title: '&lt;cstdarg&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdarg>
helpviewer_keywords:
- cstdarg header
ms.assetid: 639b4ef7-8408-4640-9343-41631f0ab663
ms.openlocfilehash: 0b45d5f591c5394ffa861e75169dce70f53b1baf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448031"
---
# <a name="ltcstdarggt"></a>&lt;cstdarg&gt;

包括 C 标准库标头\<stdarg.h > 并将关联名称添加`std`到命名空间。 包括此标头可确保在`std`命名空间中声明使用 C 标准库标头中的外部链接声明的名称。

## <a name="syntax"></a>语法

```cpp
#include <cstdarg>
```

## <a name="namespace-and-macros"></a>命名空间和宏

```cpp
namespace std {
    using va_list = see below;
}

#define va_arg(V, P)
#define va_copy(VDST, VSRC)
#define va_end(V)
#define va_start(V, P)
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
