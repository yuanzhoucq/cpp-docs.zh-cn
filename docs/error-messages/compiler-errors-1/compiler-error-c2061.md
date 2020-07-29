---
title: 编译器错误 C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: 1e1b13960c84d4e03c6316c451c690f8b5a6236e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212860"
---
# <a name="compiler-error-c2061"></a>编译器错误 C2061

语法错误：标识符 "identifier"

编译器在不需要它的位置找到了标识符。 请确保在 `identifier` 使用之前声明。

初始值设定项可由括号括起来。 若要避免此问题，请将声明符括在括号中，或将其设为 **`typedef`** 。

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
