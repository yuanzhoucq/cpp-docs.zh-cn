---
title: 编译器错误 C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 2c8164cad25d68ee61ff9fed7170482d5dfc9505
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474784"
---
# <a name="compiler-error-c2530"></a>编译器错误 C2530

identifier： 必须初始化引用

除非它已被声明，必须在声明它时，初始化引用：

- 使用关键字[extern](../../cpp/using-extern-to-specify-linkage.md)。

- 为类、 结构或联合的成员 （和构造函数中初始化）。

- 为函数声明或定义中的参数。

- 作为函数的返回类型。

下面的示例生成 C2530:

```
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```