---
title: 编译器警告（等级 3）C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: d9aff4b554f4b162f87de9e1d373d59dea019637
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991745"
---
# <a name="compiler-warning-level-3-c4645"></a>编译器警告（等级 3）C4645

用 __declspec(noreturn) 声明的函数有返回语句

在用[noreturn](../../cpp/noreturn.md) `__declspec` 修饰符标记的函数中发现了[返回](../../cpp/return-statement-in-program-termination-cpp.md)语句。 忽略 `return` 语句。

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
