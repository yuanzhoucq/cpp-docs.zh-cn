---
title: 编译器错误 C2548
ms.date: 11/04/2016
f1_keywords:
- C2548
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
ms.openlocfilehash: 2c680d86a0ea69d67f9e53a481f2f096f4cc7878
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659575"
---
# <a name="compiler-error-c2548"></a>编译器错误 C2548

class::member： 缺少参数参数的默认参数

默认参数列表缺少的参数。 如果提供的参数列表中的任意位置的默认参数，必须定义所有后续的参数的默认参数。

## <a name="example"></a>示例

下面的示例生成 C2548:

```
// C2548.cpp
// compile with: /c
void func( int = 1, int, int = 3);  // C2548

// OK
void func2( int, int, int = 3);
void func3( int, int = 2, int = 3);
```