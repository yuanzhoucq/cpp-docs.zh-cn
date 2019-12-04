---
title: 编译器错误 C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: dc64852523b6b56bc506260576e3c79164628340
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735926"
---
# <a name="compiler-error-c2061"></a>编译器错误 C2061

语法错误：标识符 "identifier"

编译器在不需要它的位置找到了标识符。 请确保在使用之前声明 `identifier`。

初始值设定项可由括号括起来。 若要避免此问题，请将声明符括在括号中，或使其成为 `typedef`。

当编译器将表达式检测为类模板参数时也可能导致此错误;使用[typename](../../cpp/typename.md)告诉编译器它是一个类型。

下面的示例生成 C2061：

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

如果将实例名称传递到[typeid](../../extensions/typeid-cpp-component-extensions.md)，则可能会发生 C2061：

```cpp
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```
