---
title: 编译器错误 C2333
ms.date: 11/04/2016
f1_keywords:
- C2333
helpviewer_keywords:
- C2333
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
ms.openlocfilehash: cca7f0d3bd75cca8fdd621fb425dec42e6560f4e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747743"
---
# <a name="compiler-error-c2333"></a>编译器错误 C2333

"function"：函数声明中有错误;跳过函数体

对于在其类中定义的成员函数，出现其他错误后，将出现此错误。

下面的示例生成 C2333：

```cpp
// C2333.cpp
struct s1 {
   s1(s1) {}   // C2333
};
```
