---
title: 编译器警告（等级1） C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 69559348a27151a22b11cae8d821110d923cd803
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627329"
---
# <a name="compiler-warning-level-1-c4216"></a>编译器警告（等级1） C4216

使用了非标准扩展：长浮点

默认 Microsoft 扩展（/Ze）将**浮点长**视为**双精度**。 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）不会。 使用**double**维护兼容性。 下面的示例生成 C4216：

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```