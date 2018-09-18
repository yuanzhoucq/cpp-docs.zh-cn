---
title: 编译器错误 C2883 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2883
dev_langs:
- C++
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50cc5b2abb34fae21bea78aa146e74b9aa9491c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019258"
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