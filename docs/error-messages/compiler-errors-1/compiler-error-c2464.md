---
title: 编译器错误 C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: a00ac997f73175eeab08a0132128e48e8fc58feb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338891"
---
# <a name="compiler-error-c2464"></a>编译器错误 C2464

identifier： 不能使用 new 分配引用

引用标识符已分配与`new`运算符。 引用不是内存对象，因此`new`无法返回一个指针指向它们。 使用标准的变量声明语法声明的引用。

下面的示例生成 C2464:

```
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```