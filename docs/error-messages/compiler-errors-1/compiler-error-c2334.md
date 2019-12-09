---
title: 编译器错误 C2334
ms.date: 11/04/2016
f1_keywords:
- C2334
helpviewer_keywords:
- C2334
ms.assetid: 36142855-e00b-4bbf-80f5-a301edeff46e
ms.openlocfilehash: f8a096a89bdb076b857e5adc49ad8162551612f2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747691"
---
# <a name="compiler-error-c2334"></a>编译器错误 C2334

"：" 或 "{" 前面有意外的标记; 正在跳过明显的函数体

下面的示例生成 C2334。 此错误发生在错误 C2059 之后：

```cpp
// C2334.cpp
// compile with: /c
// C2059 expected
struct s1 {
   s1   {}   // C2334
   s1() {}   // OK
};
```
