---
title: 编译器错误 C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: a05c98564c4e45dc380690c1b8c9bace5fc14cf4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216149"
---
# <a name="compiler-error-c2646"></a>编译器错误 C2646

全局或命名空间范围的匿名结构或联合必须声明为静态

匿名结构或联合具有全局或命名空间范围，但未声明 **`static`** 。

下面的示例生成 C2646，并演示如何修复此错误：

```cpp
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```
