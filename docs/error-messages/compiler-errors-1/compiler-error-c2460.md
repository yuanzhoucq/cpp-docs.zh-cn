---
title: 编译器错误 C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: a7d20a7658a75a492e19b9e81acaa3b6fce5cae7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743934"
---
# <a name="compiler-error-c2460"></a>编译器错误 C2460

"identifier1"：使用正在定义的 "identifier2"

类或结构（`identifier2`）声明为自身的成员（`identifier1`）。 不允许递归定义类和结构。

下面的示例生成 C2460：

```cpp
// C2460.cpp
class C {
   C aC;    // C2460
};
```

请改用类中的指针引用。

```cpp
// C2460.cpp
class C {
   C * aC;    // OK
};
```
