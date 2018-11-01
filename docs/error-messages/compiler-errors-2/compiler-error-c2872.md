---
title: 编译器错误 C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: 103998c7872b683c7405796ee28bd550246ae9bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566213"
---
# <a name="compiler-error-c2872"></a>编译器错误 C2872

'*符号*： 不明确的符号

编译器无法确定引用哪些符号。 具有指定名称的多个符号位于范围。 编译器找到的不明确的符号，请参阅以下的错误消息的文件位置和声明说明。 若要解决此问题，您可以完全限定的不明确的符号使用其命名空间，例如，`std::byte`或`::byte`。 此外可以使用[命名空间别名](../../cpp/namespaces-cpp.md#namespace_aliases)时消除歧义在源代码中的符号为包含的命名空间提供用于一个方便的短名称。

如果标头文件包含，则会发生 C2872 [using 指令](../../cpp/namespaces-cpp.md#using_directives)，并且后续的标头文件包括，其中包含在中指定的命名空间中也是一种`using`指令。 指定`using`指令仅后所有标头文件用指定`#include`。

C2872 可以导致在 Visual Studio 2013 之间的冲突`Windows::Foundation::Metadata::Platform`枚举类型，而 C + + /cli CX 定义`Platform`命名空间。 若要解决此问题，请执行以下步骤：

- 从项目文件中删除的"using 命名空间 Windows::Foundation::Metadata"子句。

- 指定包含此命名空间中任何类型的完全限定的名称。

## <a name="example"></a>示例

下面的示例生成 C2872，因为不明确的引用对一个名为变量`i`; 两个具有相同名称的变量都位于作用域：

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
