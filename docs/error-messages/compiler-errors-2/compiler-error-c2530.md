---
title: 编译器错误 C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 0816fcb4d9e2a3e6588dfcf937383fed7ab11395
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737122"
---
# <a name="compiler-error-c2530"></a>编译器错误 C2530

"identifier"：必须初始化引用

必须在声明引用后对其进行初始化（除非已声明）：

- 带有关键字[extern](../../cpp/using-extern-to-specify-linkage.md)。

- 作为类、结构或联合的成员（并在构造函数中初始化）。

- 作为函数声明或定义中的参数。

- 作为函数的返回类型。

下面的示例生成 C2530：

```cpp
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```
