---
title: 编译器警告 （等级 1） C4142 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 011f71c1d57f03c2be9bac3df67cd0ed90aa8017
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117382"
---
# <a name="compiler-warning-level-1-c4142"></a>编译器警告 （等级 1） C4142

类型的良性重定义

一种类型是对生成的代码没有影响的方式重新定义。

通过检查以下可能的原因进行修复：

- 在派生类的成员函数具有不同的返回类型从相应的成员函数的类的基类。

- 使用定义的类型`typedef`命令已重新定义使用不同的语法。

下面的示例生成 C4142:

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```