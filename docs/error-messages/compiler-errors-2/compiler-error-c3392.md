---
title: 编译器错误 C3392
ms.date: 11/04/2016
f1_keywords:
- C3392
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
ms.openlocfilehash: 34097de7d50e260ee82a8891cee988b1533debdd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556567"
---
# <a name="compiler-error-c3392"></a>编译器错误 C3392

“type_arg”: 对于泛型“generic_type”，泛型参数“param”的类型变量无效，它必须具有公共无参数构造函数

泛型类型实例化错误。 检查类型定义。 有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例使用 C# 创建一个组件，它包含具有 C + 中创建泛型类型时，不支持某些约束的泛型类型 + CLI。 有关详细信息，请参阅[类型参数的约束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```cs
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

可用 C3392.dll 组件时，下面的示例生成 C3392。

```cpp
// C3392_b.cpp
// Compile by using: cl /clr C3392_b.cpp
#using <C3392.dll>

ref class R { R(int) {} };
ref class N { N() {} };

value class V {};

ref class N2 { public: N2() {} };
ref class R2 { public: R2() {} };

int main () {
   GR<R^, V, N^>^ gr1;   // C3392
   GR<R^, V, N2^>^ gr1a; // OK

   GR<R^, N^, N^>^ gr3;  // C3392
   GR<R^, V, N2^>^ gr3a; // OK

   GR<R^, V, R^>^ gr4;   // C3392
   GR<R^, V, R2^>^ gr4a; // OK
}
```