---
title: 编译器错误 C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: e4952f4702d871ecf1c818b1fc7394e54a1a295f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743882"
---
# <a name="compiler-error-c2464"></a>编译器错误 C2464

"identifier"：不能使用 "new" 分配引用

使用 `new` 运算符分配了引用标识符。 引用不是内存对象，因此 `new` 无法返回指向它们的指针。 使用标准变量声明语法来声明引用。

下面的示例生成 C2464：

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
