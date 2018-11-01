---
title: 编译器错误 C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: e1146bf0ed2dd6d38a3c67cc6799c0e73f253323
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532608"
---
# <a name="compiler-error-c3390"></a>编译器错误 C3390

“type_arg”: 对于泛型“generic_type”，泛型参数“param”的类型实参无效，它必须是引用类型

泛型类型实例化错误。  检查类型定义。  有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

第一个示例使用 C# 创建一个组件，它包含具有 C + 中创建泛型类型时，不支持某些约束的泛型类型 + CLR。 有关详细信息，请参阅[类型参数的约束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```cs
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

可用 C3390.dll 组件时，下面的示例生成 C3390。

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK
}
```