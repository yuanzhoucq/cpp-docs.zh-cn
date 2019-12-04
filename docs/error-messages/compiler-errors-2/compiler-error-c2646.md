---
title: 编译器错误 C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: a5c4dbc967c304fc6b13eb00e2c7093380ec8be9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758211"
---
# <a name="compiler-error-c2646"></a>编译器错误 C2646

全局或命名空间范围的匿名结构或联合必须声明为静态

匿名结构或联合具有全局或命名空间范围，但未被声明为 `static`。

下面的示例生成 C2646，并演示如何修复此错误：

```cpp
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```
