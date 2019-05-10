---
title: 编译器警告（等级 4）C4932
ms.date: 11/04/2016
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: cd37ee67545918991b286d16d0fe27b47414b3c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280256"
---
# <a name="compiler-warning-level-4-c4932"></a>编译器警告（等级 4）C4932

__identifier （identifier) 和\__identifier(identifier) 是无法区分

编译器无法区分作为参数传递到 **__identifier** 的 `__finally` _finally `__try` 与 **或** 与 [_try](../../extensions/identifier-cpp-cli.md)。 不要尝试在同一程序中将它们同时用作标识符，因为这将导致 [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) 错误。

下面的示例生成 C4932：

```
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```