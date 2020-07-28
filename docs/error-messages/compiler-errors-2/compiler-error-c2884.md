---
title: 编译器错误 C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: d6014aa44dd1c2a5f1b0418a7171b239a754ec33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220192"
---
# <a name="compiler-error-c2884"></a>编译器错误 C2884

"name"：由 using 声明引入，与本地函数 "function" 冲突

尝试多次定义函数。 第一个定义是本地定义。 第二种情况是来自带有声明的命名空间 **`using`** 。

下面的示例生成 C2884：

```cpp
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```
