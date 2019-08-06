---
title: '&lt;csetjmp&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csetjmp>
helpviewer_keywords:
- csetjmp header
ms.assetid: 8f21fddd-5e9b-4219-a848-581cdd3569d9
ms.openlocfilehash: 8f3a1a622776d5dd2ef3d22aaa3436933c5a7137
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452400"
---
# <a name="ltcsetjmpgt"></a>&lt;csetjmp&gt;

包含标准 C 库标头 \<setjmp.h> 并将关联名称添加到 `std` 命名空间。

## <a name="syntax"></a>语法

```cpp
#include <csetjmp>

using jmp_buf = see below;
```

## <a name="functions"></a>函数

```cpp
[[noreturn]] void longjmp(jmp_buf env, int val);
```

## <a name="macros"></a>宏

```cpp
#define setjmp(env)
```

## <a name="remarks"></a>备注

包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
