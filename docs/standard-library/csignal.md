---
title: '&lt;csignal&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csignal>
helpviewer_keywords:
- csignal header
ms.assetid: d18bcf82-a89a-476c-a6bf-726af956f7c0
ms.openlocfilehash: 2e82877a54c433b9db638b908be290535b1cc857
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452332"
---
# <a name="ltcsignalgt"></a>&lt;csignal&gt;

包括 C 标准库标头\<信号 .h > 并将关联名称添加`std`到命名空间。 包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。


## <a name="syntax"></a>语法

```cpp
#include <csignal>
```

## <a name="namespace-and-macros"></a>命名空间和宏

```cpp
namespace std {
    using sig_atomic_t = see below;

    extern using signal-handler = void(int);
}

#define SIG_DFL
#define SIG_ERR
#define SIG_IGN
#define SIGABRT
#define SIGFPE
#define SIGILL
#define SIGINT
#define SIGSEGV
#define SIGTERM
```

## <a name="functions"></a>函数

```cpp
signal-handler* signal(int sig, signal-handler* func);
int raise(int sig);
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
