---
title: 编译器错误 C2258
ms.date: 11/04/2016
f1_keywords:
- C2258
helpviewer_keywords:
- C2258
ms.assetid: 105eaa87-befb-4ecb-9a3f-e09e14d2f5bf
ms.openlocfilehash: 916ccf444bf82c9d6c0c9ad290afb65353a4f5b2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758796"
---
# <a name="compiler-error-c2258"></a>编译器错误 C2258

非法的纯语法，必须为“= 0”

用不正确的语法声明一个纯虚函数。

下面的示例生成 C2258：

```cpp
// C2258.cpp
// compile with: /c
class A {
public:
   void virtual func1() = 1; // C2258
   void virtual func2() = 0;   // OK
};
```
