---
title: 编译器错误 C2075
ms.date: 11/04/2016
f1_keywords:
- C2075
helpviewer_keywords:
- C2075
ms.assetid: 8b1865d2-540b-4117-b982-e7a58a0b6cf7
ms.openlocfilehash: d53ef6f34b061a04f2c136b4e349d4951529b94b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436304"
---
# <a name="compiler-error-c2075"></a>编译器错误 C2075

“identifier”：数组初始化需要大括号

指定的数组两边没有大括号。

以下示例生成 C2075：

```
// C2075.c
int main() {
   int i[] = 1, 2, 3 };   // C2075
}
```

可能的解决方法：

```
// C2075b.c
int main() {
   int j[] = { 1, 2, 3 };
}
```