---
title: 编译器错误 C2389
ms.date: 11/04/2016
f1_keywords:
- C2389
helpviewer_keywords:
- C2389
ms.assetid: 6122dc81-4ee3-49a5-a67d-d867808c9bac
ms.openlocfilehash: 50fa514222b7f51ea28ffdb87bf09a870b80dff7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216240"
---
# <a name="compiler-error-c2389"></a>编译器错误 C2389

“operator”：非法的操作数“nullptr”

**`nullptr`** 不能为操作数。

以下示例生成 C2389：

```cpp
// C2389.cpp
// compile with: /clr
int main() {
   throw nullptr;   // C2389
}
```
