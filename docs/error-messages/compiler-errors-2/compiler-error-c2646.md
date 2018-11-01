---
title: 编译器错误 C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: c02d7216df42681ae2ec733ae932d22861c1f0ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571998"
---
# <a name="compiler-error-c2646"></a>编译器错误 C2646

全局或命名空间范围的匿名结构或联合必须声明为静态

匿名结构或联合具有全局或命名空间范围，但未被声明为 `static`。

下面的示例生成 C2646，并演示如何修复此错误：

```
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```