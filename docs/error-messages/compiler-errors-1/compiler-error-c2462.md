---
title: 编译器错误 C2462 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2462
dev_langs:
- C++
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65df7f4fe7f3822f2723a1709751e3b9b0f23ade
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082842"
---
# <a name="compiler-error-c2462"></a>编译器错误 C2462

identifier： 无法在 new-expression 中定义类型

不能定义一种类型的操作数字段中`new`运算符。 将类型定义放在一个单独的语句。

下面的示例生成 C2462:

```
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```