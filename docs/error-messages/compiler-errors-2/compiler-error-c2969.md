---
title: 编译器错误 C2969
ms.date: 11/04/2016
f1_keywords:
- C2969
helpviewer_keywords:
- C2969
ms.assetid: e4ea3d66-b937-4b2c-b42a-96e03fb11579
ms.openlocfilehash: 1330babe92266a6bc410084b4a46ef75f83f0b7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455518"
---
# <a name="compiler-error-c2969"></a>编译器错误 C2969

语法错误: “symbol”: 成员函数定义应以“}”结尾

模板成员函数定义具有不匹配的右大括号。

以下示例生成 C2969：

```
// C2969.cpp
// compile with: /c
class A {
   int i;
public:
   A(int i) {}
};

A anA(1);

class B {
   A a;
   B() : a(anA);   // C2969
   // try the following line instead
   // B() : a(anA) {}
};
```