---
title: 编译器警告 （等级 1） C4319 |Microsoft 文档
ms.custom: ''
ms.date: 1/18/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4319
dev_langs:
- C++
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1b5fe896ae7d8f43708b60ee4dda486ef08f428
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4319"></a>编译器警告（等级 1）C4319

> ~： 零扩展*type1*到*type2*更大的

结果**~** （按位求补） 运算符是无符号，然后零扩展转换为更大的类型时。

## <a name="example"></a>示例

在下面的示例中，`~(a - 1)`是计算结果为 32 位无符号 long 表达式并且然后通过零扩展转换为 64 位。 这会导致意外的运算结果。

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
