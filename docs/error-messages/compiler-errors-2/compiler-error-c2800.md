---
title: 编译器错误 C2800
ms.date: 11/04/2016
f1_keywords:
- C2800
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
ms.openlocfilehash: e893866a28c124e9e6cbc9663a488f89ac2d291b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408545"
---
# <a name="compiler-error-c2800"></a>编译器错误 C2800

不能重载 operator operator

不能重载以下运算符： 类成员访问 (`.`)，指向成员的指针 (`.*`)，作用域解析 (`::`)，条件表达式 (`? :`)，和`sizeof`。

下面的示例生成 C2800:

```
// C2800.cpp
// compile with: /c
class C {
   operator:: ();   // C2800
};
```