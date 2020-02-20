---
title: /Zc:rvalueCast（强制实施类型转换规则）
ms.date: 02/18/2020
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
ms.openlocfilehash: ac74192cad8a62e4c82b480038e727b114362cdd
ms.sourcegitcommit: b9aaaebe6e7dc5a18fe26f73cc7cf5fce09262c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504569"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast（强制实施类型转换规则）

指定 **`/Zc:rvalueCast`** 选项后，编译器会正确地将右值引用类型标识为强制转换操作的结果。 其行为符合 c + + 11 标准。 如果未指定该选项，则编译器行为与 Visual Studio 2012 中的行为相同。

## <a name="syntax"></a>语法

> **`/Zc:rvalueCast`**\
> **`/Zc:rvalueCast-`**

## <a name="remarks"></a>备注

如果指定了 **`/Zc:rvalueCast`** ，编译器将遵循 c + + 11 标准的第5.4 节，并仅处理导致非引用类型的强制转换表达式和导致对非函数类型的右值引用作为 rvalue 类型的强制转换表达式。 默认情况下，或者如果指定了 **`/Zc:rvalueCast-`** ，则编译器不符合要求，并将导致 rvalue 引用的所有强制转换表达式视为右。 为了符合和消除使用强制转换的错误，建议使用 **`/Zc:rvalueCast`** 。

默认情况下， **`/Zc:rvalueCast`** 为 off （ **`/Zc:rvalueCast-`** ）。 [/Permissive-](permissive-standards-conformance.md)编译器选项隐式设置此选项，但可以使用 **`/Zc:rvalueCast-`** 重写它。

如果将强制转换表达式作为参数传递给采用右值引用类型的函数，请使用 **`/Zc:rvalueCast`** 。 当编译器无法正确确定强制转换表达式的类型时，默认行为会导致编译器错误[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) 。 当未指定 **`/Zc:rvalueCast`** 时，此示例将在正确的代码中显示编译器错误：

```cpp
// Test of /Zc:rvalueCast
// compile by using:
// cl /c /Zc:rvalueCast- make_thing.cpp
// cl /c /Zc:rvalueCast make_thing.cpp

#include <utility>

template <typename T>
struct Thing {
   // Construct a Thing by using two rvalue reference parameters
   Thing(T&& t1, T&& t2)
      : thing1(t1), thing2(t2) {}

   T& thing1;
   T& thing2;
};

// Create a Thing, using move semantics if possible
template <typename T>
Thing<T> make_thing(T&& t1, T&& t2)
{
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));
}

struct Test1 {
   long a;
   long b;

   Thing<long> test() {
      // Use identity casts to create rvalues as arguments
      return make_thing(static_cast<long>(a), static_cast<long>(b));
   }
};
```

在适当情况下，默认编译器行为可能不会报告错误 C2102。 在此示例中，如果未指定 **`/Zc:rvalueCast`** ，则编译器不会报告错误转换所创建的右值的地址：

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" > **CC++ /**  > **语言**"属性页。

1. 将 "**强制类型转换规则**" 属性设置为 **`/Zc:rvalueCast`** 或 **`/Zc:rvalueCast-`** 。 选择 **"确定" 或 "** **应用**" 保存更改。

## <a name="see-also"></a>另请参阅

[/Zc（一致性）](zc-conformance.md)
