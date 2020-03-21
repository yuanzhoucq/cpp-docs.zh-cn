---
title: '&lt;csignal&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csignal>
helpviewer_keywords:
- csignal header
ms.assetid: d18bcf82-a89a-476c-a6bf-726af956f7c0
ms.openlocfilehash: fcad9c1b5ec20a7a10afc40884ece8ae8abec184
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076678"
---
# <a name="ltcsignalgt"></a>&lt;csignal&gt;

包括 C 标准库标头 \<的信号 .h > 并将关联名称添加到 `std` 命名空间。 包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。

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

## <a name="see-also"></a>另请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
