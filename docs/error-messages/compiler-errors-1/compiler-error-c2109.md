---
title: 编译器错误 C2109
ms.date: 11/04/2016
f1_keywords:
- C2109
helpviewer_keywords:
- C2109
ms.assetid: 2d1ac79d-a985-4904-a38b-b270578d664d
ms.openlocfilehash: 109b4693a07374f05e8b51c73c15d04c6d9793cd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755728"
---
# <a name="compiler-error-c2109"></a>编译器错误 C2109

下标要求数组或指针类型

在不是数组的变量上使用了下标。

下面的示例生成 C2109：

```cpp
// C2109.cpp
int main() {
   int a, b[10] = {0};
   a[0] = 1;   // C2109
   b[0] = 1;   // OK
}
```
