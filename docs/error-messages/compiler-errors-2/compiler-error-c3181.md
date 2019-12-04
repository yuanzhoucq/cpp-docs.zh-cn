---
title: 编译器错误 C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: e30ed7016ca3a4d4948a08c5c09268e52c9a407d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761668"
---
# <a name="compiler-error-c3181"></a>编译器错误 C3181

"type"：运算符的操作数无效

向[typeid](../../extensions/typeid-cpp-component-extensions.md)运算符传递了一个无效参数。 参数必须是托管类型。

请注意，编译器对映射到公共语言运行时中的类型的本机类型使用别名。

下面的示例生成 C3181：

```cpp
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
