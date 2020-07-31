---
title: 编译器错误 C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: f57b250f87bd7f2c5808b5a681ddfe49dfa5e876
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228890"
---
# <a name="compiler-error-c2872"></a>编译器错误 C2872

"*symbol*"：不明确的符号

编译器无法确定引用的符号。 范围内有多个具有指定名称的符号。 若要查看文件位置的错误消息和声明，请参阅编译器对于不明确符号的错误消息。 若要解决此问题，可以通过使用其命名空间（例如或）完全限定不明确的符号 `std::byte` `::byte` 。 你还可以使用[命名空间别名](../../cpp/namespaces-cpp.md#namespace_aliases)为包含的命名空间提供一个方便的短名称，以便在你的源代码中歧义符号时使用。

如果标头文件包括[using 指令](../../cpp/namespaces-cpp.md#using_directives)，则会发生 C2872，其中包含的某个类型也包含在指令中指定的命名空间中 **`using`** 。 **`using`** 仅在使用指定所有头文件后指定指令 `#include` 。

由于在 `Windows::Foundation::Metadata::Platform` 枚举类型和 c + +/CX-defined 命名空间之间发生冲突，因此 C2872 可能出现在 Visual Studio 2013 中 `Platform` 。 若要解决此问题，请执行以下步骤：

- 从项目文件中删除 "使用命名空间 Windows：： Foundation：： Metadata" 子句。

- 为此命名空间中包含的任何类型指定完全限定的名称。

## <a name="example"></a>示例

下面的示例生成 C2872，因为对名为的变量进行了不明确的引用 `i` ; 两个名称相同的变量位于范围内：

```cpp
// C2872.cpp
// compile with: cl /EHsc C2872.cpp
namespace A {
   int i;
}

using namespace A;
int i;
int main() {
   ::i++;   // ok, uses i from global namespace
   A::i++;   // ok, uses i from namespace A
   i++;   // C2872 ambiguous: ::i or A::i?
   // To fix this issue, use the fully qualified name
   // for the intended variable.
}
```
