---
title: 编译器警告（等级 3）C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: 607122b5592c9db4fc2ad4cabf369b4605b2673b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228760"
---
# <a name="compiler-warning-level-3-c4645"></a>编译器警告（等级 3）C4645

用 __declspec(noreturn) 声明的函数有返回语句

在标记有[noreturn](../../cpp/noreturn.md)修饰符的函数中发现了[返回](../../cpp/return-statement-in-program-termination-cpp.md)语句 **`__declspec`** 。 **`return`** 语句已被忽略。

下面的示例生成 C4645：

```cpp
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```
