---
title: 编译器错误 C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: cac397e4588c493fb8c47932feb97a5f12cf2583
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578212"
---
# <a name="compiler-error-c3391"></a>编译器错误 C3391

type_arg： 无效的类型参数的泛型参数 param 的泛型 generic_type 必须是不可以为 null 的值类型

泛型类型实例化错误。 检查类型定义。 有关详细信息，请参阅<xref:System.Nullable>并[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例使用 C# 创建一个组件，它包含具有 C + 中创建泛型类型时，不支持某些约束的泛型类型 + CLI。 有关详细信息，请参阅[类型参数的约束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```cs
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

可用 C3391.dll 组件时，下面的示例生成 C3391。

```cpp
// C3391_b.cpp
// Compile by using: cl /clr C3391_b.cpp
#using <C3391.dll>
using namespace System;
value class VClass {};

int main() {
   GR< Nullable<VClass> >^ a =
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK
}
```