---
title: 编译器错误 C2650
ms.date: 11/04/2016
f1_keywords:
- C2650
helpviewer_keywords:
- C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
ms.openlocfilehash: f71996c6d04d8be2101762fb0fb17634e6b25a1a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756131"
---
# <a name="compiler-error-c2650"></a>编译器错误 C2650

"operator"：不能是虚函数

`virtual`声明 `new` 或 `delete` 运算符。 这些运算符 `static` 成员函数中，不能 `virtual`。

## <a name="example"></a>示例

下面的示例生成 C2650：

```cpp
// C2650.cpp
// compile with: /c
class A {
   virtual void* operator new( unsigned int );   // C2650
   // try the following line instead
   // void* operator new( unsigned int );
};
```
