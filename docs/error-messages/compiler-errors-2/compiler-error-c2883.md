---
title: 编译器错误 C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: 3f32307e519394433927d49aa92333fdff7b70f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587507"
---
# <a name="compiler-error-c2883"></a>编译器错误 C2883

name： 函数声明与 using 声明引入的 identifier 冲突

你试图超过一次定义的函数。 第一个定义了包含的命名空间从`using`声明。 第二种是本地的定义。

下面的示例生成 C2883:

```
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```