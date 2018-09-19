---
title: 编译器错误 C2061 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 896fdb21c57e0f558b87ec23e2be309cf49f8095
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057959"
---
# <a name="compiler-error-c2061"></a>编译器错误 C2061

语法错误： 标识符 identifier

编译器找到了不应在此标识符。 请确保`identifier`之前使用它被声明。

初始值设定项可能会用括号括起来。 若要避免此问题，将声明符括在括号中，或使它`typedef`。

当编译器检测到作为类模板参数; 表达式时，也可能导致此错误使用[typename](../../cpp/typename.md)以告知编译器它是一种类型。

下面的示例生成 C2061:

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

如果传递到实例名称，则会发生 C2061 [typeid](../../windows/typeid-cpp-component-extensions.md):

```
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