---
title: 编译器错误 C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: b2d2766b11d15bdb666baa207591cc9ff279a280
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225470"
---
# <a name="compiler-error-c2464"></a>编译器错误 C2464

"identifier"：不能使用 "new" 分配引用

使用运算符分配了引用标识符 **`new`** 。 引用不是内存对象，因此 **`new`** 无法返回指向它们的指针。 使用标准变量声明语法来声明引用。

下面的示例生成 C2464：

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
