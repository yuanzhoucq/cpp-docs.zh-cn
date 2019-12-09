---
title: 编译器错误 C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 009a441ec610053176e79126d9f2663f29b26bc6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759043"
---
# <a name="compiler-error-c2299"></a>编译器错误 C2299

"function"：行为更改：显式专用化不能是复制构造函数或复制赋值运算符

此错误还可能是对 Visual Studio 2005 执行的编译器一致性工作的结果：以前版本的 Visual C++ Studio 允许复制构造函数或复制赋值运算符使用显式专用化。

若要解析 C2299，请不要使复制构造函数或赋值运算符成为模板函数，而是使用类类型的非模板函数。 通过显式指定模板参数来调用复制构造函数或赋值运算符的任何代码都需要删除模板参数。

下面的示例生成 C2299：

```cpp
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```
