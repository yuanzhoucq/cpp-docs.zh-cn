---
title: 编译器警告（等级 1）C4080
ms.date: 11/04/2016
f1_keywords:
- C4080
helpviewer_keywords:
- C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
ms.openlocfilehash: 5ecc50d4f967826cca691fae4f119c1dee2efef5
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626896"
---
# <a name="compiler-warning-level-1-c4080"></a>编译器警告（等级 1）C4080

应为段名标识符；找到“symbol”

[#pragma alloc_text](../../preprocessor/alloc-text.md) 中段的名称必须是字符串或标识符。 如果找不到有效标识符，则编译器会忽略杂注。

下面的示例生成 C4080：

```cpp
// C4080.cpp
// compile with: /W1
extern "C" void func(void);

#pragma alloc_text()   // C4080

// try this line to resolve the warning
// #pragma alloc_text("mysection", func)

int main() {
}

void func(void) {
}
```