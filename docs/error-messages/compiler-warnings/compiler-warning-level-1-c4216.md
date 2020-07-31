---
title: 编译器警告（等级 1）C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: b7fc44fd15f761c19ed28402a41b3bd3619b21a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223260"
---
# <a name="compiler-warning-level-1-c4216"></a>编译器警告（等级 1）C4216

使用了非标准扩展：长浮点

默认 Microsoft 扩展（/Ze）将**float long**视为 **`double`** 。 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）不会。 用于 **`double`** 维护兼容性。 下面的示例生成 C4216：

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```
