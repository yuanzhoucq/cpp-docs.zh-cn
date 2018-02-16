---
title: "编译器警告 （等级 1） C4319 |Microsoft 文档"
ms.custom: 
ms.date: 1/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4319
dev_langs:
- C++
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a492194003a639f684e84d125450067cd425276
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="compiler-warning-level-1-c4319"></a>编译器警告（等级 1）C4319

> ~： 零扩展*type1*到*type2*更大的

结果 **~**  （按位求补） 运算符是无符号，然后零扩展转换为更大的类型时。

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
