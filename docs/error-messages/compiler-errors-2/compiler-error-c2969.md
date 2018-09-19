---
title: 编译器错误 C2969 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2969
dev_langs:
- C++
helpviewer_keywords:
- C2969
ms.assetid: e4ea3d66-b937-4b2c-b42a-96e03fb11579
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 796660cbefab31a58a977930537897e6c537b834
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076926"
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