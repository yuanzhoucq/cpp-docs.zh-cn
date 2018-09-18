---
title: 编译器错误 C3225 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3225
dev_langs:
- C++
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8d8b1251b9c13a71faf771c85924a75681deab7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033246"
---
# <a name="compiler-error-c3225"></a>编译器错误 C3225

arg 的泛型类型参数不能是 type，它必须是值类型或句柄类型

泛型类型参数不是类型的正确。

有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

无法实例化具有本机类型的泛型类型。 下面的示例生成 C3225。

```
// C3225.cpp
// compile with: /clr
class A {};

ref class B {};

generic <class T>
ref class C {};

int main() {
   C<A>^ c = gcnew C<A>;   // C3225
   C<B^>^ c2 = gcnew C<B^>;   // OK
}
```

## <a name="example"></a>示例

下面的示例创建一个使用 C# 的组件。 请注意，该约束指定泛型类型仅使用值类型进行实例化。

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>示例

此示例使用 C#-编写的组件，并违反了约束只能为 MyList 的而不使用值类型实例化<xref:System.Nullable>。 下面的示例生成 C3225。

```
// C3225_c.cpp
// compile with: /clr
#using "C3225_b.dll"
ref class A {};
value class B {};
int main() {
   MyList<A> x;   // C3225
   MyList<B> y;   // OK
}
```