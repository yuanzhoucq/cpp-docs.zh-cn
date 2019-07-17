---
title: '&lt;climits&gt;'
ms.date: 11/04/2016
f1_keywords:
- <climits>
helpviewer_keywords:
- climits header
ms.assetid: 7ca8a539-aa45-4ac3-86e8-74513be3f07e
ms.openlocfilehash: 67cddab4f42d10c4d1c78762c32ed1e4fd1e6175
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244792"
---
# <a name="ltclimitsgt"></a>&lt;climits&gt;

包含 C 标准库标头\<limits.h >，并将添加到关联的名称`std`命名空间。 包括此标头中声明 C 标准库标头中使用外部链接声明的名称将确保`std`命名空间。

## <a name="syntax"></a>语法

```cpp
#include <climits>
```

## <a name="macros"></a>宏

```cpp
#define CHAR_BIT
#define SCHAR_MIN
#define SCHAR_MAX
#define UCHAR_MAX
#define CHAR_MIN
#define CHAR_MAX
#define MB_LEN_MAX
#define SHRT_MIN
#define SHRT_MAX
#define USHRT_MAX
#define INT_MIN
#define INT_MAX
#define UINT_MAX
#define LONG_MIN
#define LONG_MAX
#define ULONG_MAX
#define LLONG_MIN
#define LLONG_MAX
#define ULLONG_MAX
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
