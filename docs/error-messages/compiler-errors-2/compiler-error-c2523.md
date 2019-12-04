---
title: 编译器错误 C2523
ms.date: 11/04/2016
f1_keywords:
- C2523
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
ms.openlocfilehash: 56b0f88949d7a7fa5af945ab5d03ee9a480d6d3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746417"
---
# <a name="compiler-error-c2523"></a>编译器错误 C2523

"class：： ~ identifier"：析构函数/终结器标记不匹配

析构函数的名称必须是前面带有颚化符（`~`）的类名。 构造函数和析构函数是唯一与类同名的成员。

下面的示例生成 C2523：

```cpp
// C2523.cpp
// compile with: /c
class A {
   ~B();    // C2523
   ~A();   // OK
};
```
