---
title: 编译器错误 C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 481920fa2d8c32bc872e7b8805188cc674e6fe28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564809"
---
# <a name="compiler-error-c2482"></a>编译器错误 C2482

>'*标识符*: thread 数据管理/WinRT 代码中不允许的动态初始化

## <a name="remarks"></a>备注

在托管或 WinRT 代码，通过使用声明的变量[__declspec （thread)](../../cpp/thread.md)存储类修饰符属性或[thread_local](../../cpp/storage-classes-cpp.md#thread_local)不能用的表达式初始化存储类说明符这就需要在运行时的评估。 初始化所需的静态表达式`__declspec(thread)`或`thread_local`这些运行时环境中的数据。

## <a name="example"></a>示例

下面的示例生成 C2482 中托管 (**/clr**) 和 WinRT (**/ZW**) 代码：

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

若要解决此问题，请使用常量，初始化线程本地存储**constexpr**，或静态表达式。 单独执行任何特定于线程的初始化。