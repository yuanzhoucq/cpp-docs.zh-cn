---
title: 编译器错误 C2070 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2070
dev_langs:
- C++
helpviewer_keywords:
- C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b23daf8a8c25e132aa0717715a742352537010c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044075"
---
# <a name="compiler-error-c2070"></a>编译器错误 C2070

type： 非法的 sizeof 操作数

[Sizeof](../../cpp/sizeof-operator.md)运算符要求表达式或类型名称。

下面的示例生成 C2070:

```
// C2070.cpp
void func() {}
int main() {
   int a;
   a = sizeof(func);   // C2070
}
```

可能的解决方法：

```
// C2070b.cpp
void func() {}
int main() {
   int a;
   a = sizeof(a);
}
```