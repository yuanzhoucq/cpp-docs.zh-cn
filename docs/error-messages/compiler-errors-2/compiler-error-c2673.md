---
title: 编译器错误 C2673
ms.date: 11/04/2016
f1_keywords:
- C2673
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
ms.openlocfilehash: 1a27b41c11905a509889d46da655900b69070445
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216110"
---
# <a name="compiler-error-c2673"></a>编译器错误 C2673

"function"：全局函数没有 "this" 指针

全局函数尝试访问 **`this`** 。

下面的示例生成 C2673：

```cpp
// C2673.cpp
int main() {
   this = 0;   // C2673
}
```
