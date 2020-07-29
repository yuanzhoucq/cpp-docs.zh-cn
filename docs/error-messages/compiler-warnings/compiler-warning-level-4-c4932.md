---
title: 编译器警告（等级 4）C4932
ms.date: 11/04/2016
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: 992e047f31e4a30edd29ba6110bf119d2bc8928b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230592"
---
# <a name="compiler-warning-level-4-c4932"></a>编译器警告（等级 4）C4932

不区分 __identifier （标识符）和 \_ _identifier （标识符）

编译器无法区分 **_finally** and **`__finally`** 或 `__try` and **_try**作为参数传递给[__identifier](../../extensions/identifier-cpp-cli.md)。 不要尝试在同一程序中将它们同时用作标识符，因为这将导致 [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) 错误。

下面的示例生成 C4932：

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
