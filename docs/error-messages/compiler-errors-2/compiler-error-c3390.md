---
title: 编译器错误 C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: c624d3b0379d057b0ed566deffc2a0efcc324f88
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912863"
---
# <a name="compiler-error-c3390"></a>编译器错误 C3390

“type_arg”: 对于泛型“generic_type”，泛型参数“param”的类型实参无效，它必须是引用类型

泛型类型实例化错误。  检查类型定义。  有关详细信息，请参阅[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

第一个示例使用C#创建包含泛型类型的组件，该泛型类型具有在/clr 中C++创作泛型类型时不受支持的某些约束 有关详细信息，请参阅[类型参数的约束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

当 C3390 组件可用时，以下示例将生成 C3390。

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