---
title: 编译器错误 C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 417763e8c26918d3cd83702b283244d1c13d9d1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735744"
---
# <a name="compiler-error-c2086"></a>编译器错误 C2086

"identifier"：重定义

多次定义该标识符，或后续声明与前一个声明不同。

C2086 也可以是对被引用C#程序集进行增量生成的结果。 重新生成C#程序集以解决此错误。

下面的示例生成 C2086：

```cpp
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```
