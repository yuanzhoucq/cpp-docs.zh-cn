---
title: 编译器错误 C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: b37b28b4332b46aaaf803f58090a72c25e83f47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587754"
---
# <a name="compiler-error-c3181"></a>编译器错误 C3181

type： 运算符的操作数无效

无效的参数传递给[typeid](../../windows/typeid-cpp-component-extensions.md)运算符。 参数必须是托管的类型。

请注意，编译器使用的本机类型将映射到公共语言运行时中的类型的别名。

下面的示例生成 C3181:

```
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
