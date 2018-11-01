---
title: 编译器错误 C2673
ms.date: 11/04/2016
f1_keywords:
- C2673
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
ms.openlocfilehash: 8a544b6d96089195d7d28f9a62b091b4f1cfc537
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587637"
---
# <a name="compiler-error-c2673"></a>编译器错误 C2673

function： 全局函数没有 this 指针

全局函数尝试访问`this`。

下面的示例生成 C2673:

```
// C2673.cpp
int main() {
   this = 0;   // C2673
}
```