---
title: 编译器错误 C2800
ms.date: 11/04/2016
f1_keywords:
- C2800
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
ms.openlocfilehash: 8bab5cd015bd28228b9829cb59cb3b6fdf2f3717
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214602"
---
# <a name="compiler-error-c2800"></a>编译器错误 C2800

无法重载 "operator operator"

以下运算符无法重载：类成员访问（ `.` ）、指向成员的指针（ `.*` ）、作用域解析（）、 `::` 条件表达式（ `? :` ）和 **`sizeof`** 。

下面的示例生成 C2800：

```cpp
// C2800.cpp
// compile with: /c
class C {
   operator:: ();   // C2800
};
```
