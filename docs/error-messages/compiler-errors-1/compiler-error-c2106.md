---
title: 编译器错误 C2106
ms.date: 11/04/2016
f1_keywords:
- C2106
helpviewer_keywords:
- C2106
ms.assetid: d5c91a2e-04e4-4770-8478-788b98c52a53
ms.openlocfilehash: baa0307dcf5d68a9ca26414b6f48e95289958a96
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752036"
---
# <a name="compiler-error-c2106"></a>编译器错误 C2106

"operator"：左操作数必须为左值

运算符的左操作数必须为左值。

下面的示例生成 C2106：

```cpp
// C2106.cpp
int main() {
   int a;
   1 = a;   // C2106
   a = 1;   // OK
}
```
