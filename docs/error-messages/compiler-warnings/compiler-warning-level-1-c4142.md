---
title: 编译器警告（等级1） C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 97b13ad65335df435d071c106f577aefca7e072d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625011"
---
# <a name="compiler-warning-level-1-c4142"></a>编译器警告（等级1） C4142

类型的良性重定义

重定义类型的方式对生成的代码不起作用。

通过检查以下可能的原因进行修复：

- 派生类的成员函数与基类的相应成员函数具有不同的返回类型。

- 使用不同语法重新定义使用 `typedef` 命令定义的类型。

下面的示例生成 C4142：

```c
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```